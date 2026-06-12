---
title: "treat folder as a device?"
date: 2009-03-22
forum: General Help
---

### Post by TCSnyder on 2009-03-22
ok let me tell you my setup and what i am doing.

First i have Mandriva 2009 ( the free one installed ) but i know for a fact this works in ubuntu 8.10. i have found a program call "unetbootin" (just google it). it writes .iso images to usb drives

i wrote PuppyLinux to my jump drive, then made a new folder with

```
# mkdir /bootAlt/
``` 

then copied the contents of my usb to this folder. Then in grubs menu.lst I added this to the file

```
title Puppy Linux
kernel (hd0,0)/Bootalt/vmlinuz
initrd (hd0,0)/Bootalt/initrd.gz
```

and on restart I can boot into puppy linux without having a separate partition. 

the problem is i want to be able to do this without a usb port.
but it only can write to usb devices or the "/" directory

****WARNING*****
if you use this program do not write to the "/" directory
****WARNING*****

thanks for the help guys

---

### Post by KeyserSoze93 on 2009-03-23
I'm not sure if this will help but (from the mount manual):

```
Since Linux 2.4.0 it is possible to remount part of the file hierarchy somewhere else. The call is
              mount --bind olddir newdir
```

It depends how it knows if it is a usb device, but you could try something like:

mount --bind /SavedSettings /media/usb

---

