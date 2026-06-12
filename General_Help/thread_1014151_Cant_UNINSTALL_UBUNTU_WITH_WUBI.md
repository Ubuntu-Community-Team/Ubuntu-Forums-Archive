---
title: "Cant UNINSTALL UBUNTU WITH WUBI"
date: 2008-12-17
forum: General Help
---

### Post by blandino123 on 2008-12-17
well i installed ubuntu with wubi.i booted into it and it was perfecT!!! i freaking loved it..i installed java flash player and everything i needed. then while watching some utube vids my pc crashed!!i was extremely scared.thne i booted into vista scared that my pc might get damaged.vista told me my pc was DAMAGED and i freaked out!!then my pc crashed AGAINNNNN.afterwards i turned it back on and vista told me to run a back up.i did and now im missing 30gb from my hard drive!!!(i used 30 gb option for ubuntu)
i couldnt find "wubi" on uninstall program files nither did i find "ubuntu" so i got soo scared.i still have the wubi folder in my hard drive and it has a file that uses 29gb and another that uses 900mb.im really scared to delete this folder because it might damage my pc.

also when i shut down and turn on i have the option to boot into ubuntu still.i havent tryed to enter but im scared to.now can anyone help me please?:confused::confused::confused::confused:

---

### Post by Jammanuser on 2008-12-17
> **blandino123 said:**
> well i installed ubuntu with wubi.i booted into it and it was perfecT!!! i freaking loved it..i installed java flash player and everything i needed. then while watching some utube vids my pc crashed!!i was extremely scared.thne i booted into vista scared that my pc might get damaged.vista told me my pc was DAMAGED and i freaked out!!then my pc crashed AGAINNNNN.afterwards i turned it back on and vista told me to run a back up.i did and now im missing 30gb from my hard drive!!!(i used 30 gb option for ubuntu)
i couldnt find "wubi" on uninstall program files nither did i find "ubuntu" so i got soo scared.i still have the wubi folder in my hard drive and it has a file that uses 29gb and another that uses 900mb.im really scared to delete this folder because it might damage my pc.

also when i shut down and turn on i have the option to boot into ubuntu still.i havent tryed to enter but im scared to.now can anyone help me please?:confused::confused::confused::confused:

First of all, i think that selecting 5GB for Wubi would have been better to start out with...then if u needed more space for Wubi, u could have always resized the root.disk with LVPM. Probably, if u had done that, instead of choosing 30 GBS, you would probably not be in this fix right now...

However, now that u r, and there's nothing that we can do about selecting the wrong size for Wubi...i would say go ahead and delete ur Wubi folder. Don't be afraid that it will mess up something...it wont. Delete it, and then check to see if u got ur 30 GBs back...and we can work from there! :lolflag:

Cheers! ):P

Jam Man

:guitar:

---

### Post by blandino123 on 2008-12-17
this folder?
c:ubuntu and c:ubuntu backup even if ubuntu back up is empty?

---

### Post by Jammanuser on 2008-12-17
> **blandino123 said:**
> this folder?
c:ubuntu and c:ubuntu backup even if ubuntu back up is empty?

Yeah...that's the one. Although you can keep "ubuntu backup" if u want...it wont make much of a difference either way.

Cheers! ):P

Jam Man

:guitar:

---

### Post by blandino123 on 2008-12-17
ok deleted =p gave me back my 30 gb and uhh what now?

---

### Post by Jammanuser on 2008-12-17
> **blandino123 said:**
> ok deleted =p gave me back my 30 gb and uhh what now?

Now check to make **sure** that the Ubuntu boot entry is gone from the Vista bootloader (assuming of course ur using Vista!:p)...and if it is, ur problem is completely solved, and everything's back to normal like it was before installing Wubi. But if it **isn't**, then u may need to use a program like [EasyBCD]("http://neosmart.net/dl.php?id=1") to delete the Ubuntu entry from ur Vista bootloader. :popcorn:

Cheers! ):P

Jam man

:guitar:

---

### Post by magmon on 2008-12-17
I would recommend a full install or partition install, more and more failed install reports have been coming in recently..

---

### Post by ago on 2008-12-19
Run chkdsk /r, then look for a hidden folder C:\found.000

---

### Post by tixetsal on 2009-02-12
Hey guys.  I had the exact same problem.  I had uninstalled/reinstalled ubuntu via wubi several times on Vista Ultimate x64, as I was "learning the ropes" (aka ruining my install trying to use hybrid SLI w/ubuntu).  Curse those nvidia drivers!!!  (Off topic - If anyone has figured out how to use hybrid SLI, pl let me know!)  Anyway, I was missing 90 GB of HD space.  I am a windows admin @ a major university in the SE, so I am no noob in Win, but I could not find the missing HD space ANYWHERE!  After struggling with the problem in my mind for 1/2 day, it finally hit me.  System Restore!  If you have already followed the instructions here (run uninstaller, manually deleted C:\ubuntu and all related backup dirs, run chkdsk /f /r) and you are still missing HD space.  TURN OFF SYSTEM RESTORE!  I got my 90 GB back, thank God.  I hope that this helps someone out there.  Good luck!

---

### Post by Darkmage09 on 2009-02-12
Turning your system restore only caused problems. For 1: If you have a huge problem and need to do a restore, but you turned off the restore option, their will be no "Shadow Copies" (Restore Files) to fix the problem.


Right click on the command prompt click on open as admin

Enter this command in the Command prompt:
"vssadmin resize shadowstorage /For=C: /On=C: /Maxsize=50MB" 

50MB can be anything from 50MB to 10GB (Possibly more) For me Vista only takes 1GB each time it makes a restore point.

You will then get back 15% of your HDD.

---

### Post by solwic on 2009-02-13
Actually if I recall correctly it's pretty easy to modify C:\boot.ini to remove the Linux line.  Would be the last line in the file, I think.

EDIT:  Don't hold me to that though.  It's been a long time since I used Wubi.  :P

---

