---
title: "grub"
date: 2005-08-18
forum: Desktop Environments
---

### Post by clumsy1007 on 2005-08-18
Hi,

I've been running a dual boot with Ubuntu and Windows XP SP2 - it's been going fine for a few months now. But last night, while using Ubuntu, my CPU overheated and shut down. It does this on occasion, both in Windows and in Ubuntu, because I need a new fan :) and I just haven't replaced it yet, so i can only use my computer about30 minutes at a time. But this time, I went over the 30 minutes and the computer automatically shut down as it usually did, except this time, when I rebooted, Windows XP was no longer listed on the grub menu as it usually does - my only options were the Ubuntu set. Any idea on how to get my Windows option back?

Thanks!

---

### Post by alainhenry on 2005-08-18
As root, check your file /boot/grub/menu.lst, which contains the gub menu data.  

It should contain something like

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This is the windows part added by the installer.  the root (hd0,0) line could be different, depending on where windows is installed.  In this case it is hda1.  

If it does not contain it, you could try adding it (at the end)  and then rebooting.  

For more info on grub, try [http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

The same commands can be entered interactively from grub.  Type c when it shows the menu.  You might also have to setup grub again, see how to do that in the link

Alain

---

