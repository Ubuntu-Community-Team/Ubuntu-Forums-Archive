---
title: "Where's my phone?"
date: 2008-12-19
forum: General Help
---

### Post by astro4travel on 2008-12-19
I installed 'Bitpim"on the latest version of Ubuntu. I can't seem to get it to see my phone. I have a Sanyo Katana 11. It is supported by this software, but I can find it in that other operating system, but not Ubuntu. 
Help! Thanks for any help.

---

### Post by philetus on 2008-12-19
See if this helps

[http://www.bitpim.org/help/](http://www.bitpim.org/help/)

Linux USB Setup
USB drivers

Linux provides device drivers that can talk to the modem interface on phones. This driver is named acm and is usually autodetected and used.

Linux also provides device drivers for USB to serial converters. There is a builtin database of which vendor and product ids are applicable. Since there is a wide variety of converter chips, there is also a wide variety of drivers.
Direct USB access

BitPim can access USB devices directly. This is done using libusb which accesses the usb filesystem. You need to ensure the filesystem (usbdevfs) is mounted, usually below /proc/bus/usb.

By default Linux configures USB devices so that they are owned by root. You should be running BitPim as yourself, not root. Most recent Linux distributions use hotplug, and these instructions show you how to configure it.
 

   1.

      Edit /etc/hotplug/usb.usermap

      Add a line to the bottom.

      usbcell 0x0003 VID PID 0 0 0 0 0 0 0 0 0

      You need to replace VID and PID with the relevant vendor and product ids. The VID and PID can also be obtained from the Comm Port Settings dialog.

      Note For more recent versions of hotplug, it is considered better form to create the file /etc/hotplug/usb/usbcell.usermap.
   2.

      Create /etc/hotplug/usb/usbcell

      This script is executed whenever the device is inserted. Here is a simple example that makes the device be owned by root, group owned by cellusers and readable/writable by root and the members of cellusers.

      #!/bin/bash

      if [ "${ACTION}" = "add" ] && [ -f "${DEVICE}" ]
      then
              chown root "${DEVICE}"
              chgrp cellusers "${DEVICE}"
              chmod 660 "${DEVICE}"
      fi

      You can adjust that script as you see fit. Don't forget to make it executable. On many versions of Linux, there is a script named usbcam in the same directory that changes the device to be owned by the same person who is logged into the console. If you prefer that behavior, then copy usbcam to usbcell 

Direct USB access - udev

Recent Linux distributions (based on 2.6 kernel) may use "udev" instead of hotplug. With udev, the usb device ownership and permission can be set by a method that is similar in concept, but different in implementation. The following will work on Fedora Core 5. A similar procedure should work on other distributions that use udev.

   1.

      As done with the hotplug method above, create a cellusers group and put the users that will use BitPim in that group.
   2.

      Create /etc/udev/rules.d/60-cell.rules

      SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
      # LG Phone
      SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", GROUP="cellusers", MODE="0660"
      LABEL="cell_rules_end"

      1004 and 6000 should of course be replaced with the relevant VID and PID. (For the Sanyo SCP-3100 the VID/PID is 0474/071f).

      If you have a single user machine, you may find it easier to use a mode of 0666 and leave off the GROUP item. 

Auto Port and Phone Detection

BitPim can now auto-detect known USB devices (cell phones with USB cables) being connected to the computer (it is not aware if a device is disconnected from the computer). This feature is only available on systems runing udev version 095 or later (udevinfo -V) when BitPim is installed.

In order to take advantage of this feature, make sure that the followings are in place:

    * File /etc/udev/rules.d/60-bitpim.rules exists.
    * File /usr/bin/bpudev exists.
    * Group cellusers exists and you belong to that group. 

When a known device is connected, this feature sets the the device group to cellusers, permission to 0664, and initiates the BitPim phone detection process. The end result is that BitPim will be able to:

   1. Detect that a known device is connected,
   2. Set the appropriate group and permission for that device,
   3. Try to detect the phone model of that device.

---

### Post by astro4travel on 2008-12-21
Thanks for the reply. This seems a little advanced, however not totally above and beyond. First if you have the time, where do I find the Edit /etc/hotplug/usb.usermap? I did a ls -a and could not seem to locate this. Thanks for your time and patience. Michael

---

### Post by Coburn on 2011-08-23
This information is straight off the BitPim help page and it seems like it no longer applies.  My install of Ubuntu 11.04 does not have a module "acm" and it does not appear when I search for it in Synaptic.  Currently BitPim 1.0.7 is not detecting any comm/serial ports.

These are maintainer issues that the end-user should not be taxed with solving.

---

