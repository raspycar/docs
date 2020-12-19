# The Raspycar projects docs

# Raspberry Pi OS setup

## Image download and install

- Download a Raspberry Pi OS image from https://www.raspberrypi.org/software/operating-systems/. `Lite` version is recommended as we won't need any window manager nor applications.
- Write the image on a SD card the way you prefer :)
- Mount the SD card on your computer

## SSH setup
- Go to the mounted `boot` SD card partition and create a `ssh` file: `touch /<path_to_mounted_boot/ssh`

## Wifi setup

- Create a `wpa_supplicant.conf` in the mounted `boot` folder and fill it with the following lines:

```
country=COUNTRY-CODE
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}
```

Obviously, you need to replace `NETWORK-NAME` and `NETWORK-PASSWORD` with your wifi network credentials. `COUNTRY-CODE` is your country code following [ISO-3166](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes) standard.

## Final steps

- Insert the SD card in your Raspberry Pi and power it up.
- Identify your Raspberry PI IP address on your router once is powered up.
- Connect via SSH to its IP address and start `raspi-config`, once there:
  - Change `pi` user password (recommended)
  - Under `Interfacing options`:
    - Enable `Camera`
    - Enable `SSH`
