---
title: "Mounting Windows Drive"
date: 2006-03-18
forum: Desktop Environments
---

### Post by soup440 on 2006-03-18
My windows partiton is, you guessed it, fucked up
big surprise...

Anyway, I want to pull off important documents onto an external hard drive that is compatible with linux and back up important files. 
I have been unsuccessful in mounting the windows drive in linux, can anyone help me with this. I saw how to do this in another thread a few months back, but this is urgent and I need this done ASAP.

Thanks!

---

### Post by Shapierian on 2006-03-18
use "mount -t _type_ _device_ _dir_"
type should be either vfat or ntfs
device will be is the format of /dev/hd{letter}{number} for an internal harddrive,
for usb mass stage it seems to be /dev/sd{letter}{number} this may require a little guess work on your part, /dev/sda1 is probably your best first guess.
dir is where you want to mount it, any empty directory should work

---

### Post by soup440 on 2006-03-18
I googled a bit and I got the information to mount the partition, which is hda2
I was able to mount it but the problem im getting is that it wont let me go into the windows disk saying that I dont have persmission to access the files.

---

### Post by aysiu on 2006-03-18
Which live CD are you using to mount it? Or are you using your Ubuntu partition to mount it?

If you have a live CD, Knoppix makes it super easy to mount Windows--it automatically shows up on the desktop, just click on it, and it automounts and opens.

If you're using Ubuntu, it's a bit more involved, but these links should help...

Abbreviated:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

Lengthy:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

