# xps13-clover
Updated OS X Sierra Bootloader for Dell XPS 13

![Screenshot](/screenshots/screen1.png)

This repo contains everything you need for a working bootloader to boot OS X Sierra (tested with 10.12.1) on your XPS 13 9350 !

## Setting up the installer

First you need a working OS X machine with any OS X version (or a virtual machine). Download OS X Sierra in the App Store as well as Unibeast and Multibeast from https://www.tonymacx86.com/resources/categories/tonymacx86-downloads.3/

When download is finished install the OS X installer to a USB key by running Unibeast. Copy Multibeast app to the the root of your USB key.


### Updating CLOVER

You will need to mount the EFI partition of your usb key to modify bootloader.

To do so :
Find your usb key disk number with :
`diskutil list`

Mount partition with :

`mkdir /Volumes/EFI`

`mount -t msdos /dev/diskXs1 /Volumes/EFI` X being the disk number found before

Replace CLOVER (`/Volumes/EFI/EFI/CLOVER`) folder in the EFI partition of your key by the one in this repo.

## Booting the installer

To boot the installer we will need to configure the BIOS. Press F2 at boot and change these settings in the BIOS (make sure you use BIOS version 1.4.4, if not use windows to update it) 
:
- Disable Secure Boot
- Disable VT for Direct I/O
- Set SATA Operation to AHCI

Add UEFI option in the BIOS to boot from the key using UEFI.

## Installing 
Just follow the steps and enjoy !
Always remember to back up your important data !
Don't forget to run Multibeast at the end to install Clover to your startup disk, and copy the repo's CLOVER folder to your startup disk EFI partition.

## Getting drivers install
I would recommend using KextUtility to install drivers to your new system. You can do it using the command line, but let's jsut be lazy. You can find KextUtility here : http://cvad-mac.narod.ru/index/0-4
Use the soft to install driver in the `Kexts` folder :
- `ACPIBatteryManager.kext` : makes the battery part work (checking the percent capacity of the battery in the menu bar, ...)
- `VoodooPS2Controller.kext` : driver for the integrated keyboard and touchpad (no multi touch yet, but working on it ! )

## What does/does not work ?
### Working
- Battery Indicator
- Bluetooth (with new mini PCI card, I recommend DW1550, quite cheap on ebay)
- Display Brightness Slider
- Graphics (Intel HD540 Acceleration)
- Keyboard
- Sound (drivers not in repo yet !)
- NVMe SSD
- Power Management
- Touchpad (basic operations, no multitouch)
- USB-C Video Output (DisplayPort + HDMI)
- Webcam
- WiFi (with new mini PCI card, I recommend DW1550, quite cheap on ebay)
- Display Brightness Hotkeys

### Not Working
- SD Card Reader (not tested yet but should not work)

## Future improvement
In order to fix a few issues I need to patch DSDT, not done yet but should be ready soon !

## What are my specs ?
I am using my XPS 13 9350 with following specs :
- Intel® CoreTM i7-6560U @ 2.20 GHz
- 16Gb RAM
- 512 Gb NVMe SSD
- Intel Iris Graphics 540
- QHD+ screen with touch screen

But this bootloader should work with any XPS 13 9350 !






