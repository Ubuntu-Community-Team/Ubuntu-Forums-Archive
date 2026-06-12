---
title: "Suddently, I can't boot Ubuntu"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Neo40 on 2006-02-19
Hi,

I was playing a game (Civ IV) then after a while my machine was not responding. I did a hardware reset and here I got after the Ubuntu splash screen:

Uncompressing linux...Ok, booting kernel.
Loading please wait...
mount: Mounting /dev/hda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesnt have /sbin/init

/bin/sh: can't access tty; job control turned off
#

What does it mean? Is my hdd dead?

Thanks

---

### Post by Robgould on 2006-02-19
Do you only have one hard drive?  Are you dual booting?  Can you still ge to windows if you are?   I don't think your hdd is dead, but need some more info.

---

### Post by Neo40 on 2006-02-19
Hi,

I dont dual booting but I have another hdd (I'm using it right now). Here is all the mesage if it can help:

Booting 'Ubuntu, kernel 2.6.12-10k7'
root (hd0,0)
Filesystem type is ext2fs, partion type 0x83
Kernel /boot/vmlinuxz-2.6.12-10-7k root =/dev/hda1 ro quiet splash
[Linux-bzImage, setup 0x1c00, size 0x1343bc]
initrd /boot/initrd.img-2.6.12-10-k7
[Linux-initrd @ 0x17a7d000, 0x562c77 bytes]
save default
boot
Uncompressing linux...Ok, booting kernel.
Loading please wait...
mount: Mounting /dev/hda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesnt have /sbin/init

/bin/sh: can't access tty; job control turned off
#


Also, I can't mount my hdd (Ubuntu) anymore when I boot with my another hdd:

[root@myhost eric]# mount /dev/hdb1 /mnt/hd
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Hope someone can help me...

---

### Post by kspringer on 2006-02-19
I don't believe it means your hdd is dead -- probably just inaccessible.  And, yeah, good luck with that...

The same thing happened to me today.  Running great and then, without warning, it failed to boot.  I have the same error messages you do.

I've been a "lurker" in these forums for months and months -- I don't have broadband and then I get my disks two weeks ago.  I do a full install.  Worked great.  (Had to take my machine to another town to get the updates! No broadband here...)

If you do a search in the forums, you'll find this isn't an isolated case.
Check [_here_]("http://ubuntuforums.org/showthread.php?t=132700&highlight=mount+failed") or [_here_]("http://ubuntuforums.org/showthread.php?t=125377&highlight=invalid+argument"), for example. That isn't all and I saw in one where there was a bugzilla/malone report on it.

Hey, maybe I'll do the "Recovery/root/fsck" thing...

Wish me luck.  Only other option is a total install (gotta get all those updates again! Man!)

ks

---

