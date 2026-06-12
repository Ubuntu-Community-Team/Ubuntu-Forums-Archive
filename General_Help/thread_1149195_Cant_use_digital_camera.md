---
title: "Cant use digital camera"
date: 2009-05-05
forum: General Help
---

### Post by Hawk__0 on 2009-05-05
When I plug it in, there is no extra "sd" device in /dev (sda1, sda2, sdb1, etc).  But when I use lspci, I get:
```
Bus 001 Device 008: ID 04b0:016d Nikon Corp. 

```

That is my Nikon camera.  How can I mount this???

Ubuntu 8.04

---

### Post by mihai.ile on 2009-05-05
Try to see if there are several ways to connect to the pc from the cammera settings menu and try to change them. If no success then maybe your cammera don't connects as a usb drive and need to be loaded by some library.
If this is the issue, the easyest way to test is to install gThumb (it installs under applications->graphics) and from the application's menu File->Import or something like that and see if it detects your nikon.

---

### Post by Hawk__0 on 2009-05-05
I can't find any options to do that anywhere on my camera

edit:

I opened gthumb and went to import and saw:

```

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

```

People with this problem claim to have fixed it by modifying the /etc/udev/rules.d/45-libgphoto2.rules file, but I don't have this file!!!

EDIT:

Managed to get gthumb2 to load my images by installing (IIRC) libgthumb2-usb? libgthumb2-2-dev?

I cant remember if those are the exact package names, but they should be close.  Its a slow process loading them with gthumb2 but its better than nothing!

---

