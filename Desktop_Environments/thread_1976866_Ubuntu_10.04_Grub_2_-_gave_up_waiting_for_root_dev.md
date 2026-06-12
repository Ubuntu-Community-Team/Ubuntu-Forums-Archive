---
title: "Ubuntu 10.04 Grub 2 - gave up waiting for root device"
date: 2012-05-09
forum: Desktop Environments
---

### Post by nonshatter on 2012-05-09
Hi all,

I, like many others, have encountered the infamous 'Gave up waiting for root device' error while attempting to boot up. (I am using Ubuntu-desktop 10.04 LTS).

The full message is:

> Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay=
  - Check root=
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping to a shell!


Here's what I've tried:

[LIST=1]
[*]Booted into a Knoppix livecd, opened Gparted, checked the root partition is located at /dev/sdb1
[*]Editted /boot/grub/grub.lst and replaced the blkid/uuid with /dev/sdb1
[*]Rebooted - No effect
[*]Added the rootdelay=90 setting to the same line. No effect
[*]Entered the grub2 menu by holding shift key on boot. Entered the grub command line, set returns:
```
>grub set
?=0
color_highlight=
color_normal=
default=0
gfxmode=640x480
lang=en
locale_dir=(hd0,1)/boot/grub/locale
menu_color_highlight=black/light-gray
pager=
prefix=(hd0,1)/boot/grub
root=hd0,1

```
[*] Verified that the blkid of hd0,1 matches the blkid of /dev/sdb1
[*] Verified that ```
ls (hd0,1)/
``` returns the correct listing of the root file system I want to boot into
[*] /etc/fstab is referring to the root partition using the UUID/Blkid
[*] I have run the bash script suggested in this link: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) I can attach output of readme.txt once I get back into the LiveCD.
[/LIST]

I could really use some help with this!! Any info would be much appreciated. 

Thanks in advanced,
**ns**

---

### Post by oldfred on 2012-05-09
Have you tried commenting out the search line at the grub menu?

Not sure if your specific error, but there was something about the search line not having an = that it should have in some updates. And it set root is correct you do not need the search by UUID, that is backup where drive order may get changed and then you need the search by UUID.

---

