---
title: "some questions"
date: 2005-04-15
forum: Desktop Environments
---

### Post by toto23 on 2005-04-15
I am a new linux user.I used Kubuntu 5.04 live cd and i got some errors.

1)when i tried to access harddisk i got this error
"could not mount divece. The reported error was mount: can't find 
dev/hda5 in /etc/fstab or /etc/mtab"

2)for soundcart it gave this error
"error was initializing the sound drive. device/dev/dsp cannot be opened(no such file or directory).the sound server will continiu using null output device."

3)also i could't  configure network in Kubuntu.

Can you help me to fix this problems?

---

### Post by accuser on 2005-04-15
> 1)when i tried to access harddisk i got this error
"could not mount divece. The reported error was mount: can't find 
dev/hda5 in /etc/fstab or /etc/mtab"
You need to specify a mount point - a place where the root folder of the hard disk partition will be found. If you don't mount will look in the files /etc/fstab and /etc/mtab to find out where the default or exisitng mount point is. In a terminal (or Konsole), type:
```
$ sudo mount /dev/hda5 /mnt
```
For more options, look at the online manual for mount:
```
$ man mount
```

---

