---
title: "Can't get my USB devices to work in vmware"
date: 2006-08-29
forum: Desktop Environments
---

### Post by saracen on 2006-08-29
I have Ubuntu as the Host OS and I installed a Windows XP guest.  Everything is working great except I can't get my USB devices to work - none of them.  I've enabled a USB controller for the virtual machine but when I boot the machine, none of my USB devices show up under VM -> Removable Devices -> USB Devices.  I have a webcam, an HP USB printer, and a blackberry.

The ONLY reason I need windows is to do blackberry development.  If I can get this working then I can finally say sayonara to the dual-boot.  If anyone can help out and get this working you'd really make my day :KS

---

### Post by diablo75 on 2007-11-08
open the following file: /etc/init.d/mountdevsubfs.sh by following command - gksudo gedit /etc/init.d/mountdevsubfs.sh

Find the following lines:
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb


Unmark them so that look like this:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb


Restart and your usb devices will be recognised

---

### Post by danwood76 on 2007-11-08
Here is a link to the issue on the vmware site:

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=30442796&stateId=0%200%2030444212](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=30442796&stateId=0%200%2030444212)

Their solution is slightly simpler and works perfectly.

regards,
Danny

---

