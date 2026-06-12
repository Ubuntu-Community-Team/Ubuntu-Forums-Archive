---
title: "Getting rid of Grub"
date: 2006-05-15
forum: Desktop Environments
---

### Post by GuitarHero on 2006-05-15
I had ubuntu installed on an extra hard drive on my old computer, I built a computer today using the ubuntu hard drive to put my new windows installationn on it.  I tried booting up the old computer to get some files(i was stupid for not getting them before hand) and it shows and error when it gets to the grub part because linux is no longer there.  How do I get it to boot to windows and not use grub anymore?

---

### Post by aysiu on 2006-05-15
Follow [these instructions](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458).

---

### Post by GuitarHero on 2006-05-15
No thats not what I meant.  I already took the ubuntu hard drive out, put it in a new computer, and installed windows over it.  Now I need to get the old machine to boot off the windows hard drive that is still in there.

---

### Post by aysiu on 2006-05-15
How about [this](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx), then?

---

### Post by ori.livneh on 2006-05-15
you need to boot up the computer using a Windows boot diskette / cdrom that has **fdisk** (try [http://bootdisk.com/]("http://bootdisk.com/") if you don't have one). Once you get to the command prompt, you should type **fdisk /mbr**

Hope this helps.

---

### Post by GuitarHero on 2006-05-17
[QUOTE=ori.livneh]you need to boot up the computer using a Windows boot diskette / cdrom that has **fdisk** (try [http://bootdisk.com/]("http://bootdisk.com/") if you don't have one). Once you get to the command prompt, you should type **fdisk /mbr**

Hope this helps.[/QUOTE]
Would a regular XP disk work?  Is that what you are talking about?

---

