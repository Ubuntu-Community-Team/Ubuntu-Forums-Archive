---
title: "GRUB problem!"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Baphomet on 2006-06-18
Well i guess it's actually simple to fix this but i don't know how and am actually kind of afraid trying any other stuff.

So i had Windows XP + Ubuntu 5.10 installed with grub working like a charm. Since Ubuntu 6.06 was released i tried some stuff with 5.10 and managed to make it stop at booting (Some error about xserver). I didn't mind because i had decided to make a fresh install of ubuntu with new 6.06!

1. Booted with 6.06 CD.
2. Went to desktop and started the installer.
3. In the partitioning section, decided to go manual: deleted the two former partitions, and created two new ones (one ext3 and one swap).
4. Put the ext3 to / and the swap for swap.
5. Installed ok (just gave this error for not getting updates, but i figured it was some problem with the repositories and said ok).
6. Then i was expecting the grub installer to kick in, instead it just said to reboot and remove cd... as i did.
NOW:
The grub loader is there, with previous listing (the list that was when i had 5.10) but the time limit is diferent now and nothing happens for each of the items on the list. Just gives an disk error. This includes every instance of ubuntu and also Windows XP

SO:
I guess if i manage to edit the loader config and put all the correct stuff it will be OK, right? If yes, how do i do this? Where is the file, and how to do it correctly?

Thank for you patience with another newbie!

---

### Post by ozorba on 2006-06-18
Try this:

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub)

---

### Post by Baphomet on 2006-06-18
So tried the "reinstalling process" but again in the end it doesn't show any Grub stuff!

The second process is kind of cryptic to me. I don't know how to check wich drives are wich (e.g. hd(0,6)) and i don't know if GRUB is or not installed in the MBR or on the drive!

I need some serious newb help right?

---

### Post by Baphomet on 2006-06-18
Finally managed!

Well as i thoght it was just a matter of changing the drives in grub's menu list, hd(x,y). I figured that y were ok and the problem was fiding out what were the x for ubuntu and for my windows.

Thank you ozorba!
SO: Since the drive which i had both OSs on was the first (one BIOS) i tried hd(0,y) and there it was.

---

### Post by Baphomet on 2006-06-18
Well it seems it's not ok yet, because Windows still does not load.
Here's the windows entry in grub menu.lst
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

As i said before, it's on the same drive as ubuntu (hd(0,x) and it should be on partition 0. Meanwhile i think i tried all the combinations hd(0,1->3) since i have 3 NTFS partitions on that disk.

Any ideas? This is weird!

---

### Post by Baphomet on 2006-06-18
Well, managed again!
Didn't realise this:
> map (hd0) (hd2)
map (hd2) (hd0)

Which apparently changed alocations (?)... cut it off and it was ok again!

---

