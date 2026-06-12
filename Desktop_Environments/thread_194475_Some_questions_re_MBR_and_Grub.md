---
title: "Some questions re: MBR and Grub"
date: 2006-06-11
forum: Desktop Environments
---

### Post by rah on 2006-06-11
Hi everyone. I'm still kind of new at this, so please bear with me.

I have a few questions regarding the MBR and Grub.

On my AMD64, I have a few different distros right now, all variants of Ubuntu. I've got a a 64-bit Dapper, a 32-bit Breezy, and a 64-bit Xubuntu.

It seems that everytime I install a new distro to try it out, the MBR changes location. I say this because I have at the moment three different /boot/grub/menu.lst files -- one for each distro -- but the one that matches the boot menu that I see when powering up is the newest one (the menu.lst for Xubuntu).

[COLOR="Blue"]**Question 1a**: *Beyond what I just described, is there a way to determine where the MBR is located at any given time? Does its location have anything to do with /boot/grub/default?*[/COLOR]

[COLOR="Blue"]**Question 1b**: I*s it possible to move the MBR? I would like to have it back on the 64-bit Dapper partition, since that's my main system.*[/COLOR]

As for menu.lst, this seems to be something that is generated upon installation. However, if I add or remove a distro after installation -- on a different partition of course -- the original menu.lst doesn't reflect these changes.

[COLOR="Blue"]**Question 2**: *Is there a way I can update menu.lst whenever I want to reflect the current state of my HD as a whole? (Besides doing it manually -- I'd be afraid to mess it up!)*[/COLOR]

Thanks for reading.

---

### Post by sarhento_lobo on 2006-06-11
Hi rah, 

AFAIK the MBR should be in the disk you booted from, so the only way you can "move" your MBR is by changing the boot sequence (you're not technically moving it, just switching -- that is, if you have valid mbr's on your other boot disks).

From what I understand, you want your Dapper menu.lst to be the one used by grub when loading. I did something similar to this before back when I was myself testing several Ubuntu flavors (default and Kubuntu). What I did was to boot using a live cd, mount the partition of the installation I wanted to have in the grub menu, link the executables to /bin and /sbin (I think it was only these, there may be others), then did sudo grub-install. After rebooting the menus that appeared in grub were the ones I wanted.

You'll have to do a little bit of searching in these forums since I don't have the links of the threads that I used when I researched that one.

Cheers,
sarhento_lobo.

---

### Post by jimbob on 2006-06-11
Check out this article - it has helped me a lot.


[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB IDE 80 GB SATA
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mdurham on 2006-06-11
When Grub is installed on the MBR it is told where to find it's menu file "menu.lst".
This file is resposible for the menu that you see at boot time. So, Grub is always installed in the same place i.e. MBR, it's only the menu and it's location that changes. One way to fix the problem of ever changing menues is to get Grub into a state that you want and then copy the MBR to a floppy. After that whenever the MBR gets overwritten you can easily replace it with the saved MBR on the floppy. Of course the "menu.lst" must always be in the correct place for this particular Grub to work.
Maybe that helps? I'm not sure.

---

