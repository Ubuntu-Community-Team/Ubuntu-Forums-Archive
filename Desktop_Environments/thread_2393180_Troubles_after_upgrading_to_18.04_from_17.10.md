---
title: "Troubles after upgrading to 18.04 from 17.10"
date: 2018-05-30
forum: Desktop Environments
---

### Post by doublec122 on 2018-05-30
Hi. So, technically I have two troubles, one that led to another. After I upgraded to 18.04, obviously I had to run into some form of issue. The issue is the black screen with the blinking cursor at the top left corner that after a while freezes. I tried to do the usual things, reinstalling Plasma (I have Kubuntu), restarting sddm and such. Nothing worked. Next, I tried to reinstall the nvidia drivers, since I was running out of options and I had some similar problem in the past and this worked then. First I purged nvidia, but then the tty froze and I had to restart. The second trouble comes in when I realise I don't see my wifi interface anymore and I my tethering doesn't work either, which is strange. What could be done?

---

### Post by Bashing-om on 2018-05-30
Hello doublec122; Welcome to the forum.

What results when booting with the "nomodeset"  boot parameter ?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2

EFI system ? Did you disable "secure boot" in bios ? as the nvidia driver is proprietary - 3rd party.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by doublec122 on 2018-05-30
> **Bashing-om said:**
> Hello doublec122; Welcome to the forum.

What results when booting with the "nomodeset"  boot parameter ?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2

EFI system ? Did you disable "secure boot" in bios ? as the nvidia driver is proprietary - 3rd party.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

Thank you for your answer, but, if it is possible, I'd like to get some help on my wifi interface problem first, since otherwise I can't access the internet at all (not even tethering works for me, it doesn't detect the interface). Moreover, if I solve this, I can finish reinstalling my nvidia drivers and if I still get a black screen, I'd recur to nomodeset. The worst part is that the wifi interface disappeared after I was forced to restart my laptop.

---

### Post by Bashing-om on 2018-05-30
doublec122; Yuk :(

I have no WIFI experience - all wired here . Others here will pick up my slack.

[INDENT]A know-it-all I am not
[/INDENT]

---

