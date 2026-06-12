---
title: "Problems with mounting"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-05
(Previously posted at General Support by mistake, I don't think that's the correct place.)

I've just reinstalled Kubuntu from scratch (root and /home both completely new) and I'm pretty happy overall, but I have a couple of problems with mounting disks.

First, the floppy drive. When I insert a disk, right click the Floppy Drive icon and select 'Mount', it seems to mount but the icon doesn't change to indicate this. Then, when I attempt to access the disk, I get a message saying:

```
Could not mount device.

The reported error was:

mount: dev/fd1 already mounted or /media/floppy0 busy

mount: according to mtab, dev/fd1 is already mounted on /media/floppy0
```

Sure enough, if I make my way to /media/floppy0, I find the contents of the disk. But why can't I access it through the drive icon?

Attempting to access hdb1 causes more worry though. Attempting to either mount or access the drive produces the following message:

```
Could not mount device.

The reported error was:

mount: can't find dev/hdb1 in /etc/fstab or /etc/mtab
```

A lot of my data (in fact, all of it) is on that partition, so I'd rather it be mounted when I boot actually, because I plan to use it a lot for various things.

---

### Post by Jose Catre-Vandis on 2006-09-05
Not so sure about your floppy drive problem, but your 2nd hard drive is usually not picked up by Ubuntu (someone correct me if I am wrong, just relating personal experience from several multiple drive installations!), so you will need to manually edit your "fstab "

Create a new directory for the mount
```
sudo mkdir /mnt/HD2
```
or call it whatever you want
```
sudo nano /etc/fstab
```
or replace nano with editor of your choice

on a new line in the file type:
```
/dev/hdb1   /mnt/HD2  ext3  defaults  0  0
```
(assumes your 2nd drive is a linux drive, edit accordingly)
Save and exit editor, then:
```
sudo mount -a
```
if you (I!) got it right, your 2nd drive should now show up, sometimes though a reboot sorts things all out, if the mount -a command doesn't do it (don't know why)

---

### Post by Rhapsody on 2006-09-05
Thanks, that seemed to do it. Now I can really get cracking with this system.

---

