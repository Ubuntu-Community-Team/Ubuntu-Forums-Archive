---
title: "Stopping a USB Device Properly"
date: 2005-11-18
forum: Desktop Environments
---

### Post by jdgiotta on 2005-11-18
I'm using a Linksys USB WiFi adapter and when I want to disconnect the device I first close the network connection.

However, when I unplug the USB cable I experience random problems. Sometimes my mouse will stop working or the system will freeze.

Is there anything I can do to prevent system errors?

---

### Post by kosmic on 2005-11-18
Right click and Unmount

---

### Post by jdgiotta on 2005-11-18
The device doesn't show up as an icon like a USB drive does.

---

### Post by kosmic on 2005-11-18
ups sorry, hum im not in my linux box right now, but if you run in a console line the comand "Lsusb" you can see it detected and where it is mounted, so you jst need to umount it :) hope it helps

---

### Post by jdgiotta on 2005-11-18
All I get is:
```

Bus 001 Device 003: ID 1915:2233
Bus 001 Device 001: ID 0000:0000
```

I'm not sure how to tell it unmount something other then a drive.

---

### Post by professor_chaos on 2005-11-18
if you type "mount" in the command line, you should get a list of the currently mounted devices. Then "sudo umount /device"

---

### Post by jdgiotta on 2005-11-22
You see that's what poses a problem:
```

/dev/hda2 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

```
The last tmpfs on /dev is the only change in mounted devices when I plugin my Wifi adapter to the USB port.

How do I specify that device?

---

