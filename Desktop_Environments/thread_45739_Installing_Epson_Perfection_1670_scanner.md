---
title: "Installing Epson Perfection 1670 scanner"
date: 2005-07-01
forum: Desktop Environments
---

### Post by jmarxer on 2005-07-01
Running xsane as root allows the choice of either the AverMedia card or the Epson scanner. Choosing the Epson scanner and clicking on Continue produces the following error:
	Failed to open device 'snapscan:libusb:003:006':
	Invalid argument.
in a separate dialog box, and the following on the terminal command line:
	jack@ubuntu:~$ sudo xsane
	[snapscan] Cannot open firmware file /path/to/your/firmware/file.bin.
	[snapscan] Edit the firmware file entry in snapscan.conf.

I've been been reading the Sane(NOT) and scanner HOWTOs and lots of other pages they make reference to, but what the hey! It just shouldn't be that hard to install and use an Epson scanner. My system is Hoary, AMD64 and the version of libusb I have installed is 0.1.8-17ubuntu2.

Any help would be much appreciated.

Following is some of what I've done so far:
**************************************************************************************
Scanning with GNU/Linux
July 1, 2005
Jack Marxer
This is the result of trying to list the sane devices available
$ scanimage -L
device `v4l:/dev/video0' is a Noname AVerMedia DVD EZMaker virtual device
device `snapscan:libusb:003:004' is a EPSON EPSON Scanner flatbed scanner

The green LED on the scanner blinks when either the power line or the USB cable (and the other is already connected) are plugged in, but after blinking a few times the light goes out. 

Running scanimage produces:
jack@ubuntu:~$ scanimage
scanimage: setting of option --br-x failed (Invalid argument)

Running xsane as root allows the choice of either the AverMedia card or the Epson scanner. Choosing the Epson scanner and clicking on Continue produces the following error:
	Failed to open device 'snapscan:libusb:003:006':
	Invalid argument.
in a separate dialog box, and the following on the terminal command line:
	jack@ubuntu:~$ sudo xsane
	[snapscan] Cannot open firmware file /path/to/your/firmware/file.bin.
	[snapscan] Edit the firmware file entry in snapscan.conf.

Running xsane as a normal user simply opens Xsane with the AverMedia for the input device.


This URL: [http://thegoldenear.org/toolbox/unices/scanning.html](http://thegoldenear.org/toolbox/unices/scanning.html)
is a document called Scanning and Scanner Serving for GNU/Linux and Windows, which explains how to setup a scanner for use in Debian GNU/Linux. It goes on to describe how to enable that scanner for remote use from workstations running Debian GNU/Linux, other unices or Microsoft Windows.

It says, “We need to identify the means being used to access your scanner and its location. You can use either of the following, whilst root”
jack@ubuntu:~$ sane-find-scanner -v
This is sane-find-scanner from sane-backends 1.0.15

searching for SCSI scanners:
checking /dev/scanner... failed to open (Invalid argument)
checking /dev/sg0... failed to open (Invalid argument)
	.
	.
	.
checking /dev/sgz... failed to open (Invalid argument)
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
checking /dev/usb/scanner0... failed to open (Invalid argument)
	.
	.
	.
checking /dev/usb/scanner15... failed to open (Invalid argument)
checking /dev/usbscanner... failed to open (Invalid argument)
checking /dev/usbscanner0... failed to open (Invalid argument)
	.
	.
	.
checking /dev/usbscanner15... failed to open (Invalid argument)
found USB scanner (vendor=0x04b8 [EPSON], product=0x011f [EPSON Scanner]) at lib usb:003:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
done
jack@ubuntu:~$ ~

OR

jack@ubuntu:~$ sudo scanimage -L
Password:
device `v4l:/dev/video0' is a Noname AVerMedia DVD EZMaker virtual device
device `snapscan:libusb:003:007' is a EPSON EPSON Scanner flatbed scanner
jack@ubuntu:~$

Then they say to Test the scanner this way:
jack@ubuntu:~$ scanimage -d snapscan:libusb:003:007 --format tiff > image.tif
[snapscan] Cannot open firmware file /path/to/your/firmware/file.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:003:007 failed: Invalid argument
jack@ubuntu:~$ sudo scanimage -d snapscan:libusb:003:007 --format tiff > image.tif
[snapscan] Cannot open firmware file /path/to/your/firmware/file.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:003:007 failed: Invalid argument
jack@ubuntu:~$

This URL is recommended for installing an Epson Perfection 1670:

[http://www.commercialventvac.com/~jeffs/epson1670andFedora.html](http://www.commercialventvac.com/~jeffs/epson1670andFedora.html)
**************************************************************************************

---

### Post by Franko30 on 2007-06-25
Hi,

it was no problem using this scanner in Dapper and Edgy, following this guide:

[http://ubuntuforums.org/showthread.php?t=26911](http://ubuntuforums.org/showthread.php?t=26911)

But unfortunately, there was a bug introduced in the Kernel used in Feisty, which makes using this scanner almost impossible, see:

[http://ubuntuforums.org/showthread.php?t=26911&page=3](http://ubuntuforums.org/showthread.php?t=26911&page=3)

Franko30

---

