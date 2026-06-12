---
title: "Grub.Is.Gone!"
date: 2009-01-11
forum: General Help
---

### Post by joey-elijah on 2009-01-11
Doh! Grubs gone.

I used to triple boot Ubuntu x64, Vista Ultimate x64 and Windows 7 x86. Now the x64 version of Windows 7 is out, i downloaded and installed...

My mistake.

I deleted vista (cos once despite having over 50GB free you can't 'shrink' a windows partitions without going through a whole bunch of hoops that take a looong time) so i  chopped up it's disk into smaller partitions and installed Windows 7 on one.

Nice.

Last time Grub linked to the Windows loader which listed both Vista Ultimate and Windows 7.

HOwever, now it's just gone. That's obviously because the bootloader grub was linking to for Windows is gone, too.

How do i fix it? I have a knoppix CD to hand, but i've messed my Grub list up far too many times in the past, so some help would be mucho appreciated! Thanks!

---

### Post by joey-elijah on 2009-01-11
Someone? I don't mean to bump, but i'd really like to be able use Ubuntu. As it is i can't boot into it and if i can't boot into what's the point in having it?!

---

### Post by damis648 on 2009-01-11
Thar ye go me hearty!
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by chex_m8 on 2009-01-11
i guess you can try reinstalling grub
sudo grub
grub> find /boot/grub/stage1    this will return something like (hd0,?) use this output
grub> root (hd0,?)
grub> setup (hd0)
grub> quit

---

### Post by joey-elijah on 2009-01-11
> **damis648 said:**
> Thar ye go me hearty!
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Ahh! many thanks! Shall give this a blast ASAP!

---

