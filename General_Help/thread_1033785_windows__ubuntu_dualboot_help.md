---
title: "windows / ubuntu dualboot help"
date: 2009-01-07
forum: General Help
---

### Post by sPiN1 on 2009-01-07
I had ubuntu installed and I installed windows on my other partition for video games but now it took over my grub or something and I cna't choose to boot ubuntu or windows with grub, is there an easy way to fix this? I'm using windows xp currently.

---

### Post by gettinoriginal on 2009-01-07
Hopefully something in one of these will help: :P
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Zeroberry on 2009-01-07
Or [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sPiN1 on 2009-01-07
> **Zeroberry said:**
> Or [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I do this:
Type the following and press enter:

find /boot/grub/stage1
And get these 
grub> find /boot/grub/stage1
 (hd0,1)
 (hd0,2)

and when I do  this Install Grub:

grub> setup (hd0)

I get this

grub> setup (hd0)

Error 12: Invalid device requested


help?

---

### Post by sPiN1 on 2009-01-07
i would greatly appreciate if someone could help me get this to work

---

### Post by gettinoriginal on 2009-01-08
Sorry, no practical experience, never had a grub problem, but I found this:

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

