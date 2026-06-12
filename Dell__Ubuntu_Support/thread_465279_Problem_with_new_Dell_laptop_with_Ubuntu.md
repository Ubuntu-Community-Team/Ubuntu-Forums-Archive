---
title: "Problem with new Dell laptop with Ubuntu"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by JohnnyC44 on 2007-06-05
So I received my Dell E1505N, fired it up, installed the updates -- and when it rebooted I received the" Error 17: Cannot mount selected partition" message.  I searched this forum and discovered that it's looking for the boot in partition 0 when Dell has stuck it in partition 2.

I need someone -- please -- to explain to me in Readers Digest language how to change this.  I am a real newbie here.  New in the sense that I don't know squat about Linux -- yet.  Thanks in advance!

---

### Post by dstew on 2007-06-05
Do you have a Live CD that you can boot?

---

### Post by tgalati4 on 2007-06-05
In grub:

> root (hd0,2)
"I found a Linux Partition"
> kernel /boot/vmlinuz-(tab key) root=/dev/mapper/Ubuntu-root ro  Complete the sentence with your full kernel (perhap vmlinuz-2.6.15-28-386
>initrd /boot/initrd-(tab key)  Complete the sentence with your full initrd (perhaps initrd.img-2.6.15-28-386)
>boot

Cross your fingers.

Once you are in Ubuntu, open a terminal (Apps-->Access-->terminal)

sudo nano /boot/grub/menu.lst (or grub.conf depending on what it's called)

Use the arrow keys to move to the section that says root (hd0,0) and change it to (hd0,2)

Control-O (return), Control-X (to exit)

Now grub should be changed in future boots.

That wasn't too bad.

Reader's Digest:

Grub is the Grand Unified Boot Loader.  It's neat, but you have to know how it works.  It lets you choose what operating system you want to boot into.  You can have 7 to choose from.  (But you can change it to add more.)

root (hd0,0)  means look for a boot partition with meaningful stuff on disk #0 (the first disk found) and partition #0 (the first partition of that disk).
kernel /boot/vmlinux-2.6---  This is the the mini kernel that will boot, detect your hardware and load the entire operating system.  It will change whenever you upgrade the kernel.  Normally updates will take care of updating grub, but not always.  root=/dev/mapper/Ubuntu-root ro means look for the Ubuntu root directory in a device called /dev/mapper/Ubuntu-root.  ro means mount this file system as read-only initially.

initrd /boot/initrd-2.6----  This is the "initial ramdisk"--the bootstrap program that gets loaded that will then load the kernel.  Again, it is specific to the latest version of Ubuntu that you have updated.  It's version should match the kernel that you are booting.

boot (what we are trying to accomplish).

It's new, but not hard.

---

### Post by JohnnyC44 on 2007-06-05
Thanks, folks!  I'm back up and running.  So Linux is a lot like DOS.  I've got a Linux primer coming from Amazon, so I should have some legs under me fairly soon.  I appreciate the quick response from the community.  I hope to be able to give back here as I become more experienced.  Thanks again!  John

---

### Post by phr0ze on 2007-06-05
> **JohnnyC44 said:**
>  So Linux is a lot like DOS.  

LOL

---

### Post by bapoumba on 2007-06-06
Thread moved to "Ubuntu Dell Support".

---

