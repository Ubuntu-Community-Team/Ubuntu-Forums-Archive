---
title: "Error 15: Menu.lst not found after illegal shutdown"
date: 2009-04-17
forum: General Help
---

### Post by jmg498 on 2009-04-17
Hello all,

I hope I am posting this in the right place (my installation was done using Wubi).

Yesterday my entire system froze under Ubuntu and I was forced to power down the computer.  When I went to reboot, grub came up with an Error 15: Menu.lst not found.

I searched the drive, and menu.lst was not in any of the folders Grub was looking in.  It was only in the /ubuntu/winboot folder.  I copied it over to where Grub was searching for it but that didn't work.

Is there any way to reinstall Grub or recreate the menu.lst file?  Any suggestions would be greatly appreciated.

Thanks!

---

### Post by jmg498 on 2009-04-17
I just realized that root.disk is nowhere on my drive anymore.  So I'm guessing I'll need to reinstall Wubi.  Actually, this time around I'll probably just install Ubuntu as an actual partition to avoid this problem in the future.

How exactly could a system lock-up followed by a power-down delete the root.disk and /disks folder?

Any info is appreciated.

---

### Post by meierfra. on 2009-04-17
Did you run "chkdsk" ?

> I just realized that root.disk is nowhere on my drive anymore.


Have a look at C:\found.0000

---

### Post by jmg498 on 2009-04-17
Yes.  I ran chkdsk /f and nothing changed.  There is no found.0000 file either.

---

### Post by meierfra. on 2009-04-17
> How exactly could a system lock-up followed by a power-down delete the root.disk and /disks folder?

root.disk is just a file on your windows partition. A hard power-down can damage the file system, and if chkdsk isn't able to recover the file, you are basically out of luck.  So with  a Wubi install, you need to avoid hard power-downs at all costs.

Do you have any valuable data on your Wubi partition, which isn't backed up? If yes you might try photorec to recover root.disk (but I don't really know whether photorec can handle this kind of file)


> Actually, this time around I'll probably just install Ubuntu as an actual partition to avoid this problem in the future.
Sound like I good idea.

---

### Post by jmg498 on 2009-04-17
> root.disk is just a file on your windows partition. A hard power-down can damage the file system, and if chkdsk isn't able to recover the file, you are basically out of luck. So with a Wubi install, you need to avoid hard power-downs at all costs.

Do you have any valuable data on your Wubi partition, which isn't backed up? If yes you might try photorec to recover root.disk (but I don't really know whether photorec can handle this kind of file)

Thanks.  I tried PhotoRec but no luck.  I just plan to install Ubuntu as a real partition to avoid this again.  Thanks for the info!

---

