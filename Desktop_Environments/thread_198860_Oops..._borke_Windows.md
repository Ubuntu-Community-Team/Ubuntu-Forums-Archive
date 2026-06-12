---
title: "Oops... borke Windows"
date: 2006-06-17
forum: Desktop Environments
---

### Post by atomicbaum on 2006-06-17
Well, here's my problem:
     I was playing around with some tools that my sister's fiance gave me and I decided to re-size my ntfs partition so I could install a Linux to play around with (gentoo). So when I was installing gentoo, I accidentally wrote over windows (by the way, the gentoo install failed... ouch). 
    I will have to reinstall windows xp because my little brother isn't quite comfortable with Linux yet (but I'm teaching him). Now the problem is I have GRUB installed as my boot loader so I can boot into Ubuntu (my safe, solid Linux), windows 98, and windows xp. However, If I install windows XP, its boot-loader will take over GRUB and I wont be able to get into ubuntu. Is there any way I can install XP and get GRUB back up and running (without reinstalling ubuntu) and still detect windows 98 and xp (my current configuration)?

---

### Post by mlind on 2006-06-17
You can backup you grub using grub-floppy (dunno if it works with USB sticks too..),
or just have Ubuntu "alternate" install cd available. 

Alternate cd includes recovery mode, which can automatically mount your root (/)
partition and you just have to run 

```

grub-install /dev/**xxx**

```

where xxx is your harddisk where you want GRUB. 
This is usually /dev/hda, or /dev/sda for SATA disk.

If you have the luxury of two separate HDD's, just install grub on to
non-windows HDD and set it as first on boot order after you've installed windows.

I don't think you can prevent windows from wiping out MBR, it's evil.. :twisted:

---

### Post by fer5437 on 2006-06-17
See this thread [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) 

Hopefully it help.

---

### Post by RavenOfOdin on 2006-06-18
[QUOTE=atomicbaum]
So when I was installing gentoo, I accidentally wrote over windows 
[/quote]

That would sound less like an "oops" to me and more like "hell yes." :p

---

### Post by atomicbaum on 2006-06-19
I wish, well I got it up and running (with a whole day of updates and restarts). Thanks all.

---

