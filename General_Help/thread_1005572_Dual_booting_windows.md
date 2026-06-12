---
title: "Dual booting windows?"
date: 2008-12-08
forum: General Help
---

### Post by Saza on 2008-12-08
Is there anyway to dual boot windows along side Ubuntu?

Thanks,

Sam.

---

### Post by lovelyvik293 on 2008-12-08
Yes truck full of.Check it out:-
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Saza on 2008-12-08
I had a look, but im unsure about a few points:

```
# Backup the boot sector with eg. dd if=/dev/hda of=/mbr.bin bs=512 count=1 
# Mount your root partition in the livecd
# Restore the boot sector eg. dd if=/media/hda/mbr.bin of=/dev/hda bs=512 count=1 
```

How do I backup and restore the boot sector (dont really understand the eg.), and do I just select the partion when I'm asked by the livecd? :/

Thanks alot.

---

### Post by calvinps on 2008-12-08
I STRONGLY recommend installing it inside Windows - it does not require a partition, which will save destroying the hard disk.

Regards

---

### Post by lovelyvik293 on 2008-12-08
The backup things are for extra security you can leave them.
And for partition if you have two drives in one of which windows exist then you can install the ubuntu in this partition chose this partition at the installation time.

You can install the ubuntu inside XP with the help of wubi installer(wubi-installer.org)

This is the guide is you want to install the ubuntu without the wubi
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

---

### Post by icanfly0307 on 2008-12-08
What's the layout of your hard drive? Could you post the partitions and their sizes? Also, Wubi would wouldn't have the full functionality of Ubuntu and you might run into problems later. My recommendation? Free up space for a Ubuntu partition and install it onto there.

---

### Post by lovelyvik293 on 2008-12-08
Installation with windows with the wubi is the best choice.
Just download the wubi installer from the wubi site and it automaticaly download the Ubuntu iso image from the net.
Or if you have the ISO image with you then just put it along with wubi installer,so it can use this image.

---

### Post by icanfly0307 on 2008-12-08
Well, alright. Wubi is the best choice but only if you're a newbie and don't want to risk messing up your Windows partition. Just let us know which way you want to go (Ubuntu clean install or Wubi) and we'll help you out. :)

---

