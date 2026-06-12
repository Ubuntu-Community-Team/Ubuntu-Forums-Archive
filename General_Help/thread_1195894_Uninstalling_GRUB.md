---
title: "Uninstalling GRUB"
date: 2009-06-24
forum: General Help
---

### Post by hersheynorris95 on 2009-06-24
I am a total newb to ubuntu, but I wanted to try it out, so I got the long term support version of ubuntu 8.04, and installed it to a second hard drive, with XP on my first.  After a few months, I decided that I didn't exactly need 500 gb for my linux installation.  So, i downloaded virtualbox to XP and installed ubuntu in a virtual machine.  Then, I reformatted my second hard drive, nuking my original linux install.  Ok fine, but I forgot that GRUB wouldn't have uninstalled, and sure enough, the next time I turned my machine on, it displayed Error 17 and would not boot to any OS.  So I reinstalled ubuntu on my second hard drive, hoping the bootloader would recognize it, but unfortunately, it doesn't.  It now shows Error 22, and won't boot to either XP or ubuntu, leaving my computer a $1000 paperweight.  Does anyone know how to uninstall GRUB *and *ubuntu, so I can have my computer back from the clutches of the GRUB errors?

Thanks!

---

### Post by marshall.robert on 2009-06-24
Insert and boot from you WinXP disc and get to the recovery console. When this is up simply type fixmbr which will remove grub and replace it with Windows' own boot loader. To remove Ubuntu simply format the hard drive/partition you installed it on to.

---

### Post by hersheynorris95 on 2009-06-24
> **marshall.robert said:**
> Insert and boot from you WinXP disc and get to the recovery console.  

Update: I ran the XP cd, but found that since I bought it OEM, it only let me install XP, rather than both install and/or repair XP.  I also ran Parted Magic, and found that linux didn't recognize the file needed to boot from the XP disk.  Now what?  I'm kinda stuck.

---

### Post by hibliss on 2009-06-24
If it is an OEM install, is there a recovery partition accessible from the biod post screen?

A lot of the time the recovery console is hidden there.

---

### Post by DGortze380 on 2009-06-24
super grub disc will also run fixmbr if I'm not mistaken.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by synapsys on 2009-06-24
There is no 'removing' grub or any boot loader for that matter. The only way to remove something on your mbr is to write over it with something else.

---

