---
title: "VMware-server-1.0.5-80187.tar.gz no USB support"
date: 2008-05-12
forum: Desktop Environments
---

### Post by nu-kid on 2008-05-12
VMware-server-1.0.5-80187.tar.gz has no USB support. Everything else seems to work just fine. IS  there a way to make my usb stick work with this.?

---

### Post by chandra on 2008-05-12
IIRC, edit as sudo/kdesu the file /etc/init.d/mountdevsubfs.sh and uncomment these four lines so: 

#
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

Also append the line

usbfs /proc/bus/usb   usbfs   auto    0       0

to /etc/fstab

[Note that this is only a workaround. The preferred method is not to use /proc/bus/usb and should be used when supported by the VM software.]

After that, do

sudo /etc/init.d/mountdevsubfs.sh start

and

sudo mount -a

and restart VMware to see if the USB device is seen. Else, try after a reboot.

HTH.

---

