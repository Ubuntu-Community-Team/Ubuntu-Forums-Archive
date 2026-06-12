---
title: "Can't mount a usb mp3 player!"
date: 2009-06-24
forum: General Help
---

### Post by Chops II on 2009-06-24
I know there is alot of stuff out there and on the forums about mounting usb drives and such, but i'm having trouble despite having fixed it previously.

I can mount and play with most usb devices fine.
One usb mp3 player however will only mount as root and with root read/write permissions only. Other users can only read.
Can't change ownership after mount because it is vfat (permission set on mount). However other vfat devices mounted in exactly the same way mount fine as the user.
I have nothing in fstab for any usb drives/devices. (which should be fine, ubuntu 9.04 can mount usb drives its never seen before without prior setting up right?)
I'm at a loss. Anyone make any suggestions?
Thanks!

---

### Post by geo909 on 2009-06-24
That's weird, usb sticks shouldn't have any problems..

Use ```
sudo fdisk -l
``` to see where is your disk in /dev/whatever..

Let's suppose that your usb stick is in /dev/sdb1

Make a directory in your media folder
```
sudo mkdir /media/myusb
```

Then something like
```
sudo mount -t vfat /dev/sdb1 /media/myusb
```

should work. If it doesn't, try
```
sudo mount -t vfat /dev/sdb1 /media/myusb -rw
```
but I am not sure if this has a point with disks formatted in FAT.

Anyway, try these, maybe they'll work..

---

### Post by Chops II on 2009-06-24
Thanks, i didn't realise you can add options to the end of that mount command. that at least opens up a whole bunch of things for me to try!

---

