---
title: "Mount USB Camera"
date: 2006-05-28
forum: Desktop Environments
---

### Post by utab on 2006-05-28
Dear all,

I want to monut a usb camera Canon Powershot A520. and I want to use my camera as a USB stick and camera for a trip. 

When pluged into usb slot, the camera icon appears on the desktop which I can not see from the console which I first tried. And how can I transfer a pdf document into the camera. I was using my camera for both purposes on XP.

I see usbfs on /proc/bus/usb type usbfs (rw) on the mount info, But I can not get into it from the console yet. I tried that graphically as well(to write sth) but still no use.

Any comments,

Regards

---

### Post by vidak on 2006-05-29
what about right-click on the icon&mount?
or eg
sudo mount /dev/sda1 /mnt/sda1 -o rw,sync
?
is the device present in /dev ? what does ls /dev/sd* say?

---

