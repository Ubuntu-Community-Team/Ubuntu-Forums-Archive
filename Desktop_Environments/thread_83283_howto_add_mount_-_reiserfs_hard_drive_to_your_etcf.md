---
title: "howto add mount - reiserfs hard drive to your /etc/fstab file?"
date: 2005-10-28
forum: Desktop Environments
---

### Post by kazuya on 2005-10-28
how do you add mount a reiserfs hard drive to your /etc/fstab? I have enabled the partitions, but how do I permanently ensure that they get mounted upon bootup?

Also my bootup time is very slow since adding xfce, and kde to ubuntu breezy. I have a 2200 XP AMD athlon, 512MB RAM machine. the boot time is like 5 minutes now.

I know somethings are bad on my update and installs?

The culprit or issue probably lies in the fact that I boot currently from a 7.5GB hard drive. I have 250, 200, and 160 GB hard drives, but they are just data storage drives.

I plan on converting one over to Ubuntu and thus begins my OS of choice.

I have been a mepis user for about 8 months now, and Xandros for 3 months. Debian based  desktop OSes are awesome. Breezy is a huge step up from what I expected, and the forum is awesome.


PS: in my /etc/fstab file,

is it /mnt/hda2  reiserfs rw /media/hda2 noauto?

modifying the fstab file makes it mount automatically right?

---

### Post by Appolusionist on 2005-10-28
[quote=kazuya]
PS: in my /etc/fstab file,
 
is it /mnt/hda2 reiserfs rw /media/hda2 noauto?
 
modifying the fstab file makes it mount automatically right?[/quote]
 
If you want it to load automatically... I suggest using this line instead...
 
/dev/hda2 /media/hda2 reiserfs defaults 0 1

---

### Post by kazuya on 2005-10-28
thanks chief.

---

