---
title: "Major ubuntu SCREW UP !"
date: 2009-05-07
forum: General Help
---

### Post by HOLY COW on 2009-05-07
Hello and thanks for your time,

I have a old ***VAIO PCG-6HCP*** laptop with the following issues :

At first I had "***WIN XP***" on it >> Then i installed "***Ubuntu 9.04" via "WUBI***" >> It all worked flawlessly >> Then i ***transferred ubuntu*** (without editing the "menu.lst") via "***LVPM***" onto my second partition >> Reboot >> receive [COLOR="Red"]GRUB error 17[/COLOR] >> go back to "***WUBI installed UBUNTU***" >> then i [COLOR="Red"]delete[/COLOR] the "transferred UBUNTU" partition >> ***Unable to format it, i restart my system*** >>[COLOR="Red"] GET ERROR 17 once[/COLOR] >> then finally get [COLOR="Red"]ERROR 17 again[/COLOR].

Boot screen shows > GRUB loading stage1.5 > GRUB loading, please wait >> Error 17

[COLOR="Blue"]**Conclusion**[/COLOR] : **I CANNOT access my WIN XP or WUBI~UBUNTU installations.**
[B][I]
Here is my REAL issue/dilema [/I][/B]:
 
1.CD/DVD drive does NOT FUNCTION.
2.CANNOT BOOT from USB for some godforsaken reason (the option just does not exist in the BIOS).
3.I don't have the "money/time" to get a new cd/dvd-drive.Therefore i cannot make any use of a LIVE CD !

:KSAny suggestions ??? 
:KSAny possible solution that does not involve buying or repairing my cd/dvd drive ??

Thank you again and have a nice day.

PS : Sorry for the repulsive text formatting :D

---

### Post by maheshasolkar on 2009-05-07
> **HOLY COW said:**
> 1.CD/DVD drive does NOT FUNCTION.

That, right there, is a deal breaker as far as my expertise with computers goes! I'd love to hear what others have to say too.

I have a Sony VAIO laptop too. It's bios does not support booting from USB. But I thought it was because it is an old laptop.

< end of useless reply :) >

---

### Post by pastalavista on 2009-05-07
Only option I can think of is to borrow a CD drive from another laptop. If you can't do that or buy one, you're pretty much out of luck.

---

### Post by 123456789123456789123456 on 2009-05-07
it would seem that you messed up the partition table.

The computer does not know how to access the hard drive now.
You can fix it.
You need to be able to start the computer up with a cd drive.
You also need a boot cd that comes with a partition editor, that can write the tags to the xp directory, Bootable, and Primary.

Lets get the cd/dvd problem worked out first.
If you can open the laptop's case, do so, and confirm that the drive is plugged in.
if you are unable to do that, start the computer up, is the BIOS reconizing the the cd/dvd drive.
if so can you set the boot priority to boot from that drive first?
if not, access BIOS boot menu, usually F12 on most machines.  Choose the cd drive.
After you get the partitions set correctly, try booting from HDD(Hard Disk Drive), if it does not boot.  Either install on MBR, ntldr, or Reinstall Grub.

---

### Post by HOLY COW on 2009-05-07
> **maheshasolkar said:**
> That, right there, is a deal breaker as far as my expertise with computers goes! >

I was looking forward to a reply like that with terrific apprehension :( Though i still want to see what others have to say ???

---

### Post by HOLY COW on 2009-05-07
> **123456789123456789123456 said:**
> 

Lets get the cd/dvd problem worked out first.
If you can open the laptop's case, do so, and confirm that the drive is plugged in.
if you are unable to do that, start the computer up, is the BIOS reconizing the the cd/dvd drive.
if so can you set the boot priority to boot from that drive first?
if not, access BIOS boot menu, usually F12 on most machines.  Choose the cd drive.
After you get the partitions set correctly, try booting from HDD(Hard Disk Drive), if it does not boot.  Either install on MBR, ntldr, or Reinstall Grub.

Doing that as we speak. Will let you know asap if the DRIVE was properly plugged in or not !

Either way thanks a lot.

---

### Post by cmost on 2009-05-07
Please don't put so much **bold** and **CAPITALIZED** type in your posts.  It is not necessary in order to explain your problem and frankly, it's overly dramatic.  Calmly explain the issue and someone will assist you.  Thanks!  :-)

---

### Post by HOLY COW on 2009-05-07
> **cmost said:**
> Please don't put so much **bold** and **CAPITALIZED** type in your posts.  It is not necessary in order to explain your problem and frankly, it's overly dramatic.  Calmly explain the issue and someone will assist you.  Thanks!  :-)

Point duly noted and thank you for the reminder.

---

### Post by ghostborg on 2009-05-07
[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

Another thread has some ideas about Grub 17. 
Could be your bios and grub drive/partition assignments are not in agreement as that is what I think the above thread is eluding to.

---

### Post by kennyrogersjr on 2009-05-07
> **cmost said:**
> Please don't put so much **bold** and **CAPITALIZED** type in your posts.  It is not necessary in order to explain your problem and frankly, it's overly dramatic.  Calmly explain the issue and someone will assist you.  Thanks!  :-)

> **HOLY COW said:**
> PS : Sorry for the repulsive text formatting :)

Talk about beating it to death...was that really necessary? The person knew they did it, they apologized in advance. It actually helped me find the facts I needed to determine how to attack the problem. Get over it and go "help" someone else.

123456789123456798123456 - Great strategy. However, I'd check the BIOS first to see if it recognizes the drive. Then, if it doesn't recognize it, I'd open it up.

Good luck. Hopefully you can find another laptop cd/dvd drive so you don't lose your data. 

Ken

---

### Post by HOLY COW on 2009-05-07
> **123456789123456789123456 said:**
> it would seem that you messed up the partition table.

The computer does not know how to access the hard drive now.
You can fix it.
You need to be able to start the computer up with a cd drive.
You also need a boot cd that comes with a partition editor, that can write the tags to the xp directory, Bootable, and Primary.

Lets get the cd/dvd problem worked out first.
If you can open the laptop's case, do so, and confirm that the drive is plugged in.
if you are unable to do that, start the computer up, is the BIOS reconizing the the cd/dvd drive.
if so can you set the boot priority to boot from that drive first?
if not, access BIOS boot menu, usually F12 on most machines.  Choose the cd drive.
After you get the partitions set correctly, try booting from HDD(Hard Disk Drive), if it does not boot.  Either install on MBR, ntldr, or Reinstall Grub.

Alas ! i tried everything from above, even though the ***BIOS detects both the HDD and the Optical Drive*** i can't really do much.

Ultimately i think the ONLY SOLUTION to this problem at this point seems to be the one in which i *repair* or buy a *new* optical drive

Thank you again for your precious time.

PS : If by any means anyone out there has some other suggestion, please do let me know. Thank you all :)

---

