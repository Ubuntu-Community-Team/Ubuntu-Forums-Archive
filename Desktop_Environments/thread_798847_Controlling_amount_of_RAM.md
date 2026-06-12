---
title: "Controlling amount of RAM"
date: 2008-05-18
forum: Desktop Environments
---

### Post by Carlos Fonseca on 2008-05-18
I am wondering if there is a way to limit the amount of ram accessed by the Ubuntu system. I know the "/burnmemory" key in windows. There is something similar in Linux?
Thanks!

---

### Post by sdennie on 2008-05-18
I'm not sure why this would be useful but, you should be able to do it by adding "mem=" when booting.  For example, when you boot and grub comes up, hitting e on the kernel you plan to boot then moving down one line and hitting e again then typing "mem=512M", hitting enter and then b should boot the system with 512M of RAM.  I haven't tried this but I believe it will work.

---

### Post by Carlos Fonseca on 2008-05-18
Hi vor!
I am testing this because my system (865pe chipset) didn't like 4GB of ram too much. Every time I use 4 sticks of 1GB, Ubuntu (or any other distro) runs very slowly. Using the key you explained made the system runs without a glitch. :)
This is a very awkward solution but worked very well in my dual boot setup, WinXP and Ubuntu. (windows recognizes 3.6GB and have no problem.)
Thank you very much!

---

### Post by sdennie on 2008-05-18
I see.  You can make that change permanent by editing /boot/grub/menu.lst and adding the mem= command you used to the end of the parts labeled "defoptions=" and "altoptions=" and then running

```

sudo update-grub

```

---

### Post by Methanoid on 2009-05-13
I'm in a similar position. This ISNT Ubuntu giving me the grief but a Linux kernel called AMithlon that isn't happy with 1Gb+.

Some people find mem=512M works for them (is it case sensitive in any way) but it doesnt for me if I have 2x1Gb memory. If I remove one DIMM it boots and the mem=512M works. 

Is there any OTHER way to limit memory use in Linux? I know, its not Ubuntu but this place is the  best for any Linux support, not just Ubuntu.

Its been suggested that MLOCK can use up some memory before the kernel loads but I have to confess it confuses me. 

I just want to be able to multi boot my system with XP (happy with 2gb), Ubuntu (happy with 2gb) and Amithlon (have to remove a dimm to get it to work) AND to have 2gb installed!

Help me Obi-Wan, you're my only hope!!! :popcorn:

---

