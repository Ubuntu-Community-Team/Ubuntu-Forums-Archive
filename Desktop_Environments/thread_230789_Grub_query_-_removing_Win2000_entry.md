---
title: "Grub query - removing Win2000 entry"
date: 2006-08-06
forum: Desktop Environments
---

### Post by ishimaru_kaito on 2006-08-06
I'm now reasonably dependent on Linux for all I do, but I have a small confidence problem in removing the Win2000 part of my setup. :( 

I have Win2000 on hd0,0 and Ubuntu (Dapper) on hd1,0 according to the menu.lst file, in my grub directory.  These are on separate hard drives.  Ubuntu is on the Master and Win2000 is on the Slave (IDE - old skool!).
If I were to reformat the Win2000 partition, or even to change it's use for trying other Linux OS'es, how would this affect grub?  Can I just reinstall something else and let grub sort it out?  Argh! :-k 

Any help here would be appreciated... :D

---

### Post by Tomosaur on 2006-08-06
You can remove the menu item from the menu.lst file and it will not show up on the grub screen. You can type 'update-grub' in a terminal and your available operating systems will be scanned and appended to to the menu.lst. You will probably have to run update-grub after removing/installing a new OS for it to update your menu and show/remove your new OS, unless you know exactly how to set up the menu.lst file yourself.

---

### Post by ishimaru_kaito on 2006-08-06
So it shouldn't matter that Grub may be installed on the Win2000 disk?  I seem to rememebr it installing to hd0,0 but if reinstall another OS and update Grub, that should change... :-?

---

### Post by Tomosaur on 2006-08-06
Unless you specifically installed WinGrub, grub will be installed on your linux install. It can't install itself to a windows partition. In actual fact it sits on your MBR, which windows overrwrites when it is installed (which is why you'll see so many 'I can't get to linux!' threads on here), but all of it's programs and data files such as menu.lst will live in /boot/grub of your linux install. Just be careful not to reinstall grub with a different distrobution. I don't know what the consequences of multiple Grub installs would be :/

---

### Post by ishimaru_kaito on 2006-08-06
Gotcha - install another flavour of *nix (I've been toying with Belenix for a while on a live disc, but don't install grub.  Then boot up Ubuntu, run a update-grub and it should see my new install?

Sorry for the newbie sounding stuff here, I just don't wanna break my system :o

---

