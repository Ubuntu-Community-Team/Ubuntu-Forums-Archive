---
title: "external drive spookiness"
date: 2009-05-14
forum: General Help
---

### Post by ranko on 2009-05-14
hi everybody,

in ubuntu 8.10, this worked fine, i did a clean install of 9.04, and now this is happening:

i have an external hard drive plugged into a usb port constantly. when ubuntu boots, it won't automount the partitions on the drive like it did before. not only that, but it doesn't even recognize that an external drive is plugged in at all. gparted for example only sees /dev/sda (the internal drive that boots ubuntu), it doesn't see /dev/sdb (the external drive). fdisk as well.

BUT

doing any of the following makes ubuntu see the drive and mount the partitions on it:

a) when i unplug the external drive from the usb port and plug it in again, ubuntu sees the drive and mounts both partitions on it (/dev/sdb1 and /dev/sdb2). gparted and fdisk both see the drive (/dev/sdb).

b) when i plug in a usb key into another usb port, without touching the external drive, i get the same effect as a)! ubuntu suddenly recognizes the usb key as well as my external drive, which has been plugged in the whole time!

any explanation of this spooky behavior would be appreciated.

thnx,
ranko

---

### Post by ranko on 2009-05-14
so, to recap, i need to plug *anything* into *any* usb port for ubuntu to suddenly wake up and realize that i have stuff plugged into other usb ports as well.

it's like it needs this "new usb device connected" event to enable usb device detection at all. any device that was already connected at boot time will not be visible until i connect something new into the computer. that's when ubuntu will suddenly detect all devices plugged into usb ports on my computer.

any help is appreciated!

bump

---

### Post by unutbu on 2009-05-14
If you boot up the machine, open a terminal, and type
```

sudo /etc/init.d/hal restart
```
is the external USB drive recognized?

If it works, we can set it up so this command is issued at boot so you don't have to do anything extra.

---

### Post by ranko on 2009-05-14
this doesn't help, unfortunately.

---

### Post by unutbu on 2009-05-14
How about 
```

sudo /etc/init.d/udev restart
```?

---

### Post by ranko on 2009-05-14
this doesn't help either.

any more contenders? step right up! :-)

---

### Post by Locutus_of_Borg on 2009-05-14
use /etc/fstab to assign mount points

---

### Post by bacardiandwatermelon on 2009-05-14
sudo gedit /etc/fstab

Is the external drive listed there? Ive always had issues with external devices in fstab. Try commenting it out with #. Saving and restarting.

---

### Post by ranko on 2009-05-14
the partitions on the external drive are not in /etc/fstab.

---

### Post by Locutus_of_Borg on 2009-05-14
> **ranko said:**
> the partitions on the external drive are not in /etc/fstab.
then put them in there to have them mount automatically

hal automounting is based events triggered by removing/inserting usb devices

or you could write a script to mount them if you dont want to use fstab

---

### Post by ranko on 2009-05-14
it doesn't work if i put the partitions in /etc/fstab because there is no device mapped to /dev/sdb on my machine as far as ubuntu is concerned. this means that attempting to mount /dev/sdb1 for example just gives me an error. the /dev/sdb device is detected (along with the partitions on it) only after i plug something into a usb port.

also, to quote the ubuntu wiki "Removable devices such as flash drives *can* be added to fstab, but are typically mounted by gnome-volume-manager <snip>...", emphasis theirs.

again, this used to work in ubuntu 8.10. i would boot my system up and the partitions on my external drive would be mounted. maybe something has changed in gnome-volume-manager since then...

---

### Post by ranko on 2009-05-15
(bump)

---

### Post by unutbu on 2009-05-15
I would be surprised if this works, but it is easy to try, so perhaps it is worth a shot:

Jaunty might be polling for USB devices earlier than previous versions of Ubuntu, and the USB drive is not in a ready state to be polled at boot time. Perhaps if we delay Jaunty a bit, the USB drive will have time to become ready. 

So, the idea is: boot the machine and get to the GRUB menu. Press 'e' to edit the boot line. Use the arrow keys to select the "kernel" line. Go to the end of the line and add 
```

rootdelay=120

```
Press return. Press 'b' to proceed with the boot.
If it works, you can experiment with reducing the number 120.

---

### Post by ranko on 2009-05-15
this didn't work either. this is one stubborn problem :-/.

i appreciate all of your replies!
any other ideas?

---

### Post by Noah_Kapiolani on 2009-05-15
Same problem

---

### Post by ranko on 2009-05-18
(bump)

---

### Post by unutbu on 2009-05-18
ranko, open a terminal and type
```

dmesg | bzip2 > dmesg.bz2
```
and post dmesg.bz2 as an attachment. Maybe there will be a clue for us (i.e. an error message) in there.

---

### Post by ranko on 2009-05-18
sending output from dmesg in attachment.

---

### Post by unutbu on 2009-05-18
Could you unplug-and-plug the USB drive to make it visible to the system, and then run-and-post dmesg again?

---

### Post by ranko on 2009-05-19
sending new dmesg output, after unplugging my usb key and plugging it in again, which makes ubuntu recognize my usb key as well as both partitions on my external drive.

---

### Post by unutbu on 2009-05-20
I suspect you have found a bug in Ubuntu.
To get this addressed by developers, I'd first read this
[http://mdzlog.wordpress.com/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/](http://mdzlog.wordpress.com/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/) and
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
and then file a bug report. I'm not very knowledgable about how this process works, so if you run into any questions, I would recommend asking at #ubuntu-bugs at irc.ubuntu.com.

---

