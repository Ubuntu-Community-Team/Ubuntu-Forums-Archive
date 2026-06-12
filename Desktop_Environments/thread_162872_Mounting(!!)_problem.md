---
title: "Mounting(!!) problem"
date: 2006-04-19
forum: Desktop Environments
---

### Post by tcarthy on 2006-04-19
I am new to ubuntu (and linux) but not computer illiterate. I am trying to dual boot with windows XP pro. I can install, boot & run ubuntu fine but as soon as I boot into windows, shutdown and boot into ubuntu again it fails! I get the message:

Mount: Mounting /dev/hdb1 on /root failed : Invalid argument

followed by other messages and then drop into a command line environment.

I have installed ubunto onto my primary slave drive.

Even when I boot from a floppy ubuntu fails in the same way.

Any suggestions??

---

### Post by enopepsoo on 2006-04-19
What boot manager are you using?

I heard there are problems with Windoze' boot manager.  If you are using it I would suggest grub.  The way to do that install in install the 'doze first and then install Ubuntu on the rest of the partition and let it put grub on there.

---

### Post by tcarthy on 2006-04-20
Thanks but I am using GRUB straight off the Ubuntu install disk.

---

### Post by Chris03 on 2006-04-20
This is my Grub entry with two partitions on one harddrive. In a terminal, type:

sudo gedit /boot/grub/menu.lst

Then, select everything and paste this:

default 1
timeout 3

title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader +1

title		Ubuntu Linux
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

This has worked here for a while now :)

---

### Post by slakas on 2006-04-20
well if just want to mount you can do:
moun -t <file system of windows ntfs or vfat> /dev/X /mount/point
where x your windows drive, for example /dev/hda2 or sth /mount/point is the place where you want to mount your windows partition

---

### Post by louis_nichols on 2006-04-21
[QUOTE=tcarthy]I am new to ubuntu (and linux) but not computer illiterate. I am trying to dual boot with windows XP pro. I can install, boot & run ubuntu fine but as soon as I boot into windows, shutdown and boot into ubuntu again it fails! I get the message:

Mount: Mounting /dev/hdb1 on /root failed : Invalid argument

followed by other messages and then drop into a command line environment.

I have installed ubunto onto my primary slave drive.

Even when I boot from a floppy ubuntu fails in the same way.

Any suggestions??[/QUOTE]

is the hdd which contains ubuntu partitioned? if it isn't, the mount device shoud just be /dev/hdb . and it should be mounted on "/" not "/root" which is just superuser's home folder.

---

