# rpi_elecfreaks_22_tft_dt_overlay
Device Tree Overlay for using an Elecfreaks 2.2" SPI TFT with a Raspberry Pi

## Wiring
| Raspberry Pi Pin | LCD Pin   |
| ---------------- | --------- |
| GPIO9 (MISO)     | SDO(MISO) |	
| GPIO18           | LED       |
| GPIO11 (CLK)     | SCK       |
| GPIO10 (MOSI)    | SDI(MOSI) |
| GPIO24           | D/C       |
| GPIO23           | RESET     |
| GPIO8 (CE0)      | CS        |
| GND              | GND       |
| 5V 	           | VCC       |

## Compiling the Device Tree Blob

## Using the Device Tree Overlay

Copy `elecfreaks_22_tft.dtb` to `/boot/overlays` on your Raspberry Pi and add to `/boot/config.txt`:
```
dtoverlay=elecfreaks_22_tft
```

## Switching console to the display
Edit `/boot/cmdline.txt` and append
```
fbcon=map:10
```
to the existing Kernel Commandline

## Improve display performance
Boot your Raspberry Pi and install notro's fbtft kernel (https://github.com/notro/fbtft) with improved SPI performance:
```
sudo REPO_URI=https://github.com/notro/rpi-firmware rpi-update
```
Reboot afterwards for a much snappier display update.
