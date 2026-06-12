---
title: "read ext 4 in xp?"
date: 2009-05-11
forum: General Help
---

### Post by mamamia88 on 2009-05-11
i sent my laptop back for repair and took the harrdrive out so they don't reinstall vista on my machine and i can't do anything about it.  now i have it in a usb enclosure and was wondering if there was a program that would let me read a ext 4 filesystem on xp?

---

### Post by LowSky on 2009-05-11
um I think thhe ext2/3 driver for XP will read ext4... it will just mount it as EXT3... i hope that makes sense

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mamamia88 on 2009-05-11
thanks man i'll give that a chance.  it's not going to try to format my windows to ext is it?

---

### Post by LookTJ on 2009-05-11
No, it will drive your ext filesystems, it will not format it. Just drive it :)

---

### Post by drawkcab on 2009-05-11
> **mamamia88 said:**
> thanks man i'll give that a chance.  it's not going to try to format my windows to ext is it?

No, it will just give you an option to mount your linux paritions.

If this works get back to us!

---

### Post by mamamia88 on 2009-05-11
man that didn't work it wanted me to format drive and i didn't want to do that

---

### Post by Muffinabus on 2009-05-11
> **mamamia88 said:**
> man that didn't work it wanted me to format drive and i didn't want to do that

I get the same thing, has been happening ever since I created a separate /home partition I believe.  Not sure if it's a problem with EXT4 or not.

---

### Post by ashmew2 on 2009-05-11
I have run into the same troubles with the Ext2IFS ,Everytime i tried to mount an ext2/ext3 drive , it told me i needed to format. I was so fed up with it , I looked around and found this great (open source) application : [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

It works like a charm on my Friend's Vista and XP as well :D

---

### Post by mamamia88 on 2009-05-11
> **ashmew2 said:**
> I have run into the same troubles with the Ext2IFS ,Everytime i tried to mount an ext2/ext3 drive , it told me i needed to format. I was so fed up with it , I looked around and found this great (open source) application : [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

It works like a charm on my Friend's Vista and XP as well :D

that wants to format the drive too

---

### Post by Skripka on 2009-05-11
> **LowSky said:**
> um I think thhe ext2/3 driver for XP will read ext4... it will just mount it as EXT3... i hope that makes sense

[http://www.fs-driver.org/](http://www.fs-driver.org/)

The Ext2/3 driver does not work here with Ext4.

---

### Post by mamamia88 on 2009-05-11
has anyone ran across a program made natively for ext 4 yet?

---

### Post by Eisenwinter on 2009-05-11
> **mamamia88 said:**
> has anyone ran across a program made natively for ext 4 yet?
I doubt there is one, as of yet.

Ext4 is a relatively young and untested filesystem, most Linux users still use Ext2 and Ext3.

---

### Post by LowSky on 2009-05-11
well ext4 is really new, it might take some time. I guess that is why it isn't the default format yet. infact the Arch Linux Wiki gives a good many reaosn not to use EXT4
[http://wiki.archlinux.org/index.php/Ext4#Creating_ext4_Partitions_From_Scratch](http://wiki.archlinux.org/index.php/Ext4#Creating_ext4_Partitions_From_Scratch)

---

### Post by ashmew2 on 2009-05-11
Ext3 is also not really "supported" if you understand. The drivers already mentioned were made more or less for Ext2...They dont offer journaling which you would get on a real Ubuntu install..There wont be any difference in speeds etc afaik..Just wait for a few months..It will be out sometime...And btw , Ext2FSD ran like the wind on my end :P

I guess Your partitions dont wanna be read under Windows :D

---

### Post by Skripka on 2009-05-11
> **LowSky said:**
> well ext4 is really new, it might take some time. I guess that is why it isn't the default format yet. infact the Arch Linux Wiki gives a good many reaosn not to use EXT4
[http://wiki.archlinux.org/index.php/Ext4#Creating_ext4_Partitions_From_Scratch](http://wiki.archlinux.org/index.php/Ext4#Creating_ext4_Partitions_From_Scratch)

_Actually the only real reason_ listed in that wiki NOT to use Ext4-is potential data corruption, due to apps not written with delayed allocation in mind--combine that with a hard reboot/shutdown, and you can get file corruption.  There's already a workaround to minimize this, and it is listed on that Wiki page.

All the Pros/Cons listed are simply why you might/might not not to try to adapt and Ext3 to an Ext4 etc etc.

---

### Post by bapoumba on 2009-05-11
Moved to General Help.

---

