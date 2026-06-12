---
title: "Cant access hard drive anymore"
date: 2009-06-03
forum: General Help
---

### Post by ukulele_ninja on 2009-06-03
I have an external hard drive that I had hooked up to my media center box for a long time and recently I unplugged it and used it for something on my pc. Well when I plugged it back into the media box i cant mount it. I tried readding it to the fstab and everything but i absolutely cannot get back into this hdd and get my stuff of it. Is there an EASY way to access external hard drives that doesnt involve forty steps with the fstab?

---

### Post by nandemonai on 2009-06-03
What file system? 
Did you safely unmount? 
Does it show up when plugged in via:

```
lsusb
```

```
fdisk -l
```

---

### Post by eBoxNet on 2009-06-03
You can try this one :
Plugin your external disk on your windows media center machine and unplugit by using the safe hardware removal (right bottom screen)
then plugin your disk on your ubuntu machine.

---

### Post by ukulele_ninja on 2009-06-03
Its the XFS file system and no i dont think i unmounted safely, i just unplugged it. let me get the lsusb results. (Its firewire though)

---

### Post by ukulele_ninja on 2009-06-03
> **eBoxNet said:**
> You can try this one :
Plugin your external disk on your windows media center machine and unplugit by using the safe hardware removal (right bottom screen)
then plugin your disk on your ubuntu machine.

XFS wont show up on windows, also my linux box is my media center

---

### Post by ukulele_ninja on 2009-06-03
fdisk -1 does not seem to show it

---

### Post by nandemonai on 2009-06-03
> **ukulele_ninja said:**
> fdisk -1 does not seem to show it

Ah firewire so forget lsusb.

It's fdisk -l (lower case L, not 1) ;)

As a side note, NEVER just unplug a drive, unmount it first. Doing so can lead to corruption.

---

### Post by ukulele_ninja on 2009-06-03
> **nandemonai said:**
> Ah firewire so forget lsusb.

It's fdisk -l (lower case L, not 1) ;)

As a side note, NEVER just unplug a drive, unmount it first. Doing so can lead to corruption.

so ive probably corrupted it then? Anyways around this? fdisk -l doesnt do anything.

---

### Post by ukulele_ninja on 2009-06-03
Ooops! Goofy me wasnt using sudo first.

Yes the drive shows up in fdisk as sdc1. I deleted the fstab entry for it and it least it shows up under 'computer' now

---

### Post by nandemonai on 2009-06-03
> **ukulele_ninja said:**
> Ooops! Goofy me wasnt using sudo first.

Yes the drive shows up in fdisk as sdc1. I deleted the fstab entry for it and it least it shows up under 'computer' now

Glad you have it mounting.

An easier way to manage mounts than editing fstab directly is to use pysdm.

```
sudo apt-get install pysdm
```

```
sudo pysdm
```

---

### Post by ukulele_ninja on 2009-06-03
I will try that! Im trying restarting with the drive plugged in. I got the drive to mount to /ext/EXT_HD but it shows the path as being empty and only having 6.4 gigs free.

---

