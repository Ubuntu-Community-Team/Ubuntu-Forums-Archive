---
title: "HP Officejet 7210 | Scanner not detected"
date: 2005-12-12
forum: Desktop Environments
---

### Post by linj on 2005-12-12
I'm unable to get my HP Officejet 7210 scanner function working. Printing works beautifully, thanks to KDE/CUPS integration, but scanning is difficult. I've gotten sane, quiteinsane, and kooka, but none of them see much. If it helps any, here's some dmesg after two power cycles: 

```
[4351406.026000] usb 1-2: new full speed USB device using ohci_hcd and address 12
[4351406.155000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 12 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4111
[4351406.159000] scsi9 : SCSI emulation for USB Mass Storage devices
[4351406.160000] usb-storage: device found at 12
[4351406.160000] usb-storage: waiting for device to settle before scanning
[4351411.167000]   Vendor: HP        Model: Officejet 7200 S  Rev: 1.00
[4351411.167000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4351411.207000] Attached scsi removable disk sdc at scsi9, channel 0, id 0, lun 0
[4351411.208000] usb-storage: device scan complete
[4351704.843000] usb 1-2: USB disconnect, address 12
[4351704.846000] drivers/usb/class/usblp.c: usblp0: removed
[4351733.270000] usb 1-2: new full speed USB device using ohci_hcd and address 13
[4351733.407000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 13 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4111
[4351733.413000] scsi10 : SCSI emulation for USB Mass Storage devices
[4351733.414000] usb-storage: device found at 13
[4351733.414000] usb-storage: waiting for device to settle before scanning
[4351738.420000]   Vendor: HP        Model: Officejet 7200 S  Rev: 1.00
[4351738.420000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4351738.454000] Attached scsi removable disk sde at scsi10, channel 0, id 0, lun 0
[4351738.455000] usb-storage: device scan complete


```

I know scanning works, since it works under Windows and used to work under Gentoo, with some random key pressing. But I'm really at a loss now at what to do.

Any help is much appreciated!

---

### Post by Zaventh on 2005-12-12
xsane?

---

### Post by linj on 2005-12-12
Done. 

```
no devices available
```

Same as quiteinsane, I believe. Kooka doesn't come with any error, and just sits there.

---

### Post by Zaventh on 2005-12-12
what does "scanimage -L" give?

---

### Post by metoo on 2005-12-12
Is the device already supported by the hpoj driver? Check [www.linuxprinting.org](www.linuxprinting.org) . hpoj is on sourceforge as well, if I remember correctly.
If it is supported by hpoj, is it in the version which ships with ubuntu (could be a bit older, haven't enabled the driver here - synpatic?).
When installing a HP OJ 4215 on another machine, kooka worked imidiately. So it could be, that your machine is too new for the standard ubuntu driver (guessing)??

---

### Post by linj on 2005-12-12
```
jeff@ubuntu:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x03f0, product=0x4111) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
jeff@ubuntu:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

Well, that's troubling... Yes, the device is supported by hpoj driver, since that's what I used to use on Gentoo. I'm not sure how to get to hpoj, though, since I've been using the KDE/CUPs interface all along. Just apt-get it?

I apt-getted hpoj, but I can't set it up. Here's some of it:
```
jeff@ubuntu:~$ sudo /etc/init.d/hpoj setup

Stopping the HP OfficeJet Linux driver.

----------------------------------------------------------------------

This program manages devices controlled by the HP OfficeJet Linux
driver (hpoj).  It attempts to probe your computer for local parallel-
and USB-connected devices, and allows you to specify network addresses
for remote JetDirect-connected devices.

If you experience any difficulties in detecting your device(s), then
refer to the hpoj documentation for troubleshooting information.

----------------------------------------------------------------------

Currently defined device names ([*]=default):
    (none)

----------------------------------------------------------------------

Probe for parallel-connected devices ([y]/n)?

Successfully loaded kernel module "lp" for the device probe.

Warning: Probing incorrect I/O port addresses could result in system
instability and/or data loss!  Consult your hardware documentation, BIOS
setup and/or kernel messages to verify correct base addresses in the
following prompts.   Also, take care not to probe parallel ports that
have non-printer devices (such as disk or tape drives) connected.

No parallel ports were auto-detected.

Press <Enter> alone to continue, or if you would like to probe an
undetected parallel port, then enter its hexadecimal base address
(such as "378", "278", or "3BC") here --->

----------------------------------------------------------------------

Probe for USB-connected devices ([y]/n)?

*** Warning: Your system appears to be running in SMP (multi-processor)
*** mode.  The kernel USB printer-class driver appears to be loaded
*** as a module and/or enabled to be auto-loaded.  Use of the kernel USB
*** printer-class driver instead of libusb on SMP systems may result in
*** system instability or crashes with some kernel versions.

*** Would you like the kernel USB printer-class driver to be
*** disabled and unloaded now for the USB probe ([y]/n)?

Successfully updated /etc/modules.conf to disable kernel module "usblp".

Successfully updated /etc/hotplug/blacklist to disable kernel module "usblp".

Successfully unloaded kernel module "usblp".

Probing "%002%001"...
    No device found.

Probing "%001%003"...
    No device found.

Probing "%001%002"...
    No device found.

Probing "%001%001"...
    No device found.

----------------------------------------------------------------------

Press <Enter> alone to continue, or if you would like to add a
JetDirect-connected device, then enter its dotted-decimal
IP address or hostname here --->

----------------------------------------------------------------------

Done updating device configuration files stored under /etc/ptal.
If you make manual changes to those files, then be sure to run
"/etc/init.d/hpoj start" so they will take effect.

----------------------------------------------------------------------

Starting the HP OfficeJet Linux driver.
    No hpoj devices have been configured.
    As root, run "/etc/init.d/hpoj setup".

jeff@ubuntu:~$ sudo /etc/init.d/hpoj setup

Stopping the HP OfficeJet Linux driver.

----------------------------------------------------------------------

This program manages devices controlled by the HP OfficeJet Linux
driver (hpoj).  It attempts to probe your computer for local parallel-
and USB-connected devices, and allows you to specify network addresses
for remote JetDirect-connected devices.

If you experience any difficulties in detecting your device(s), then
refer to the hpoj documentation for troubleshooting information.

----------------------------------------------------------------------

Currently defined device names ([*]=default):
    (none)

----------------------------------------------------------------------

Probe for parallel-connected devices ([y]/n)?  n

----------------------------------------------------------------------

Probe for USB-connected devices ([y]/n)?  y

*** Warning: Your system appears to be running in SMP (multi-processor)
*** mode.  The kernel USB printer-class driver appears to be loaded
*** as a module and/or enabled to be auto-loaded.  Use of the kernel USB
*** printer-class driver instead of libusb on SMP systems may result in
*** system instability or crashes with some kernel versions.

*** Would you like the kernel USB printer-class driver to be
*** disabled and unloaded now for the USB probe ([y]/n)?  n

Probing "/dev/usb/lp0"...
    *** Found "Officejet 7200 series" but failed to communicate with it!
    *** Elapsed time for this attempt was 0 second(s).
    *** Check syslog file for ptal-mlcd error messages.
    *** See hpoj documentation for troubleshooting information.

Probing "%002%001"...
    No device found.

Probing "%001%003"...
    No device found.

Probing "%001%002"...
    No device found.

Probing "%001%001"...
    No device found.

----------------------------------------------------------------------

Press <Enter> alone to continue, or if you would like to add a
JetDirect-connected device, then enter its dotted-decimal
IP address or hostname here --->

----------------------------------------------------------------------

Done updating device configuration files stored under /etc/ptal.
If you make manual changes to those files, then be sure to run
"/etc/init.d/hpoj start" so they will take effect.

----------------------------------------------------------------------

Starting the HP OfficeJet Linux driver.
    No hpoj devices have been configured.
    As root, run "/etc/init.d/hpoj setup".

```

---

### Post by Haegin on 2005-12-13
try "sudo scanimage -L" if it picks it up then it may be a permissions problem...

---

### Post by linj on 2005-12-13
Same message. But, if I do sane-find-scanner with sudo, I can get: 
```
jeff@ubuntu:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x03f0 [HP], product=0x4111 [Officejet 7200 series]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
jeff@ubuntu:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

It at least gives me a name, now...

---

