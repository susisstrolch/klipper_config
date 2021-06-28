# klipper_config
Klipper configuration files (Vertex Delta K8800, FLSUN QQ-S Pro) 

### FLSUN QQ-S Pro - printer-1
- TMC2209 StepSticks, UART mode, wires connected to wifi expansion socket
YouTube - MakerbaseTeam [https://www.youtube.com/watch?v=7ShcFKXrVHo&t=29s&ab_channel=MakerbaseTeam](https://www.youtube.com/watch?v=7ShcFKXrVHo&t=29s&ab_channel=MakerbaseTeam) 
Foxies-CSTL FLSUN_QQS-PRO Marlin Firmwares [https://github.com/Foxies-CSTL/Marlin_2.0.x/tree/FLSUN_QQS-PRO-MULTI/Marlin/Firmwares#31-TMC-with-UART-mode](https://github.com/Foxies-CSTL/Marlin_2.0.x/tree/FLSUN_QQS-PRO-MULTI/Marlin/Firmwares#31-TMC-with-UART-mode) 
- BMC extruder, mounted to the side of the printer.
- alternative Sherpa extruder
- Capricorn bowden
- Triangelab Dragon HF V2
- WIP
	- 10mm vertical rods
	- Haydn Huntley MagBalls (308mm)
	- Spring belt tensioning

### Velleman Vertex Delta K8800 - printer-2
- Heated bed
	- 220mm, 120W
	- borosilicat, pertinax
- BMC extruder
- Capricorn bowden
- Triangelab Dragon HF V2
- Haydn Huntley MagBalls (288mm)
- Spring belt tensioning

# menuconfig template files for Klipper boards
>cp menuconfig.<xxx> ~/klipper/.config
>make clean
>sudo systemctrl stop klipper*.service

Flash according to board specific info

>sudo systemcvtrl start klipper*.service

### menuconfig.BP
	- BluePill
	- HID-Bootloader
	- 2k Bootloader size
	- serial: /dev/serial/by-id/usb-Klipper_stm32f103xe_55FF6B064883524833322187-if00
	Flashing:
	  make flash FLASH_DEVICE=/dev/ttyACM0

	
### menuconfig.Vertex
	- Vertex Delta K8800
	- RAMPS 1.3 compatible
	- serial: /dev/serial/by-id/usb-1a86_USB2.0-Serial-if00-port0
	Flashing:
	  make flash FLASH_DEVICE=/dev/serial/by-id/usb-1a86_USB2.0-Serial-if00-port0

	
### menuconfig.QQSP
	- FLSUN QQ-S Pro
	- MKS Robin Mini compatible(??)
	- serial: /dev/serial/by-id/usb-1a86_USB-Serial-if00-port0
	Flashing:
	  make
	  update_mks_robin.py out/klipper.bin robin_mini.bin
	  - copy the robin_mini.bin file to the printer's SD card
	  - insert SD card into printer
	  - remove USB cable, toggle power switch, attach USB cable
