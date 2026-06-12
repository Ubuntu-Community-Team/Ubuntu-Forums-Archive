---
title: "I just got ubuntu installed"
date: 2008-12-10
forum: General Help
---

### Post by rock7dmc on 2008-12-10
i used wubi to install it and i only told wubi to use 30 gigs of space. Now when i start my computer i get a choice between ubuntu and windows xp. I dont want my windows xp i just want ubuntu. I dont want any files that are on the windows xp partion either. is there a way for me to just delete everything in the windows xp partition? and when i do can i make it so my ubunti partition has access to all the space that the windows xp was using, so instead of 30 gigs all 250 gigabytes on my hardrive

Thanks everyone in advance

---

### Post by Dr Small on 2008-12-10
You didn't install Ubuntu from Wubi, as that installs Ubuntu inside of Windows and you wouldn't be prompted to choose which OS to boot by GRUB at boot.

---

### Post by sweetandy on 2008-12-10
Instead of using the Windows Ubuntu installer, try booting into the LiveCD and telling the partitioner to use the whole disk.

Hope it helps.

---

### Post by banana jama on 2008-12-10
download gparted and burn it to an iso image here is the address:
 [http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php") 
 once you burned an iso image of gparted turn off your computer and restart it with the cd loaded. gparted will start up and you will be able to delete your partion of xp and expand your partion of ubuntu if you so wish.

---

### Post by rock7dmc on 2008-12-10
Ok i used that program and it turns out that i only have 1 partition. I want to completly remove windows xp and everything i had installed while i had windows xp. Is it possible for me to do that without reinstall Ubuntu? I original tried installing ubuntu by burning its image to a disk but i got an error like "error 32, AX=4200" or something along those lines when i tried to reboot my computer with the cd in.

And if i only have 1 partition why does it say 
"please choose your operating system:
ubuntu
Windows XP"
when i restart my computer

---

### Post by 2handband on 2008-12-10
Your best bet is to just do a clean install. Since your present CD is giving you trouble go to the following URL:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

You can get either 8.04 or 8.10. I've tried both and have had better luck with 8.04. Download it to your Ubuntu partition (if it's giving you a choice then there are two partitions present) and immediately burn it to a fresh CD. 

Install from the CD. When you get to the disc partitioner select the "guided, use the whole disc" option.

Sit back, have a drink, and click when prompted. Good luck!

---

### Post by tarranacrobat on 2008-12-10
how do you start a new thread again?

---

### Post by rock7dmc on 2008-12-10
i fixed my problem i just installed from cd, thanks for the responsees

---

### Post by mali2297 on 2008-12-11
> **tarranacrobat said:**
> how do you start a new thread again?

[http://ubuntuforums.org/newthread.php?do=newthread&f=331](http://ubuntuforums.org/newthread.php?do=newthread&f=331)

---

