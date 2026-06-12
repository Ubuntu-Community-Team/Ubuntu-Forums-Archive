---
title: "Fedora7 kernel panic"
date: 2007-06-06
forum: Fedora/RedHat and derivatives
---

### Post by kevinlyfellow on 2007-06-06
I decided to dual boot my machine and give fedora7 a shot on the hd.  I installed it but kept my grub that Ubuntu setup.  Trying to get fedora to work my grub entry reads
```

title           Fedora7
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.21-1.3194.fc7 ro single
initrd          /boot/initrd-2.6.21-1.3194.fc7.img

```

But when I boot with this, I get kernel panic.  Here is the error messages I recieve
```

Mounting root filesystem.
mount: could not find filesystem '/dev/root'
Setting up other filesystems.
Setting up new root fs
setuproot: moving /dev failed: No such file or directory
no fstab.sys, mounting internal defaults
setuproot: error mounting /proc: No such file or directory
setuproot: error mounting /sys: No such file or directory
Switching to new root and running init.
unmounting old /dev
unmounting old /proc
unmounting old /sys
switchroot: mount failed: No such file or directory
Booting has failed
Kernel panic -- not syncing: Attempted to kill init!

```

I found out that naming it
```
title     Fedora 7
``` would cause problems, but is there something else I've got wrong in my grub entry or is there a different issue?

---

### Post by kvonb on 2007-06-06
It's the Fedora mob's way of getting their daily fill of "I'm better than everyone else", all prospective new users are given a random problem so they have to go to the Fedora forum and ask for help.  Then they can all scream in harmony: "RTFM!!!" hahahah.

But seriously, if you can boot into Ubuntu, try running

```
sudo update-grub
```

That should rebuild the menu.lst with all the correct entries.

---

### Post by kevinlyfellow on 2007-06-06
Haha... I've been there before a while ago, I'd hope things changed!  I guess not...

So I updated grub and redhat wasn't found.  While "RingTFM" on grub-update it seems like it only scans /boot but I don't have a seperate boot partition.

My setup has two root partitions, one for Ubuntu and one for Fedora.  Then /home will be shared (with two different folders for the users) and of course the swap.

Looking at the error messages, is Fedora expecting that I have several different partitions setup for different folders?

---

### Post by kevinlyfellow on 2007-06-06
Fixed!!!

I needed to tell it what my root device was.  It thought that the root device was /dev/root.  In other words I needed the kernel parameter root=/dev/sda4

Thanks for your help kvonb

Edit:  BTW I love the new intel graphics driver

---

