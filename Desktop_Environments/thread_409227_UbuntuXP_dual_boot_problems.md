---
title: "Ubuntu/XP dual boot problems"
date: 2007-04-14
forum: Desktop Environments
---

### Post by Kamaria on 2007-04-14
Hi, I'm new to Ubuntu and I just installed it and everything on a separate partition. It's working fine, and I can access the data on my NTFS partition, however...

I can't boot into Windows XP itself.

I get the selection screen at startup (I assume that's GRUB) which allows me to choose from Ubuntu, Ubuntu in recovery mode, Windows XP, or my recovery partition (came with my PC).

Everything works fine EXCEPT for Windows XP. Selecting it gives me the 'Starting up....' screen with a blinking cursor and no disk activity. It simply hangs.

Any ideas on how to fix this problem?

---

### Post by izizzle on 2007-04-14
try reinstalling everything but install XP on the first partition (windows XP is too stupid to serch any other partition). Install ubuntu on the 2nd partition (GRUB IS smart enough to search the 2nd partition). tell me if this works!

- Imran

---

### Post by peacenik on 2007-04-14
I also just installed ubuntu (6.10, Edgy Eft) with a dual boot WinXP.
It works fine for me. (I just double checked!!). 
What I did was I was careful to leave the bootable flag on only for the WinXP partition. I seem to remember that Windows is more particular about that.
This might be what is causing the problem for you. You have to use the manual partition, because the automatic partition puts the bootable flag on the ubuntu root partition  by default.
I hope that this is what your problem is because then it's really easy to fix.
It just may be a particularity of my computer, though.

Please post what happens and how you solve the problem.

---

### Post by Kamaria on 2007-04-14
Here's an attachment of the partitions. I hope this helps you.
As you can see the NTFS partition is flagged as 'boot', so that doesn't seem to be the problem.

---

### Post by izizzle on 2007-04-14
try using the the technique that i described above.

install XP on the first partition flagged as "boot". then ubuntu on the other partition. tell me if if this works for you.

-Imran

---

### Post by Kamaria on 2007-04-14
Now when you say install XP, do you mean format and clean install? I obviously do wish to keep my data. :P

I actually might try using my XP recovery console and see if that helps, and then fish out my old hard drive and put Linux on there. (I should have done that in the first place, lol.)

---

### Post by izizzle on 2007-04-14
well i was thinking if you could backup your WIN XP partition and save it to a different harddrive or external harddrive or some type of dvd. Then format the WHOLE computer and install Xp first, then ubuntu and restore you backed up info from whereevere you choose to store it. Hope this helps

- Imran

---

### Post by izizzle on 2007-04-14
or you could use 2 seperate harddrives on your computer. 1 with XP and 1 with ubuntu :D

---

### Post by Topsiho on 2007-04-14
Hi,

I can see nothing wrong in your gparted screen, except for the nearly full partitions on your disc, and the rather small Linux partititons. Probably you need another disc and install Linux on that one :)

You might consider reinstalling Grub. How to do that I found  (and copied) from some other place on this forum, so you might search for this, if my copy is not really clear to you (between the double dashed lines):

===
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
Code:
**sudo grub**
This will get you a "grub>" prompt 
Code:
**find /boot/grub/stage1**
This will return a location.Use that location in the next line 
Code:
**root (hd?,?)**
Next enter the command to install grub to the mbr
Code:
**setup (hd0)**
Exit the grub shell
Code:
**quit**
===

Good luck,

Topsiho

---

### Post by lucky2 on 2007-04-14
OK ive got you covered sweets, are you running a legitamate windows xp home or pro setup? (which one?) if you think you can access the windows xp recovery console (put the original cd in a boot time and follow the options till recovery console) then this should work. boot in to linux goto a teminal window and type "sudo dd if=/dev/hda3 of=/home/<ur user name>/boot.zzz bs=512 count=1" (dumps boot info to file boot.zzz in you're home dir). you say you can access you probably need to mount you're floppy drive? or usb card or what ever and copy the boot.zzz file to something that you can get to from within windows (you can write to an ntfs drive but its dodgy if i remember right) so when you have boot.zzz in you're hand, reboot from the windows xp cd, load up the recovery console, when it asks you to login (if you dont use the administrator account for every day use), login as administrator with no password, or one of youre own logins with youre password if tht does not work. Got prompt? type fixmbr, this will overwrite linux boot loader and stick the windows xp default one back in place, reboot and windows xp should load (you're milage may vary), K so now you should be back in windows xp load up notepad or whatever and open c:\boot.ini , underthe line

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect (or how ever it looks)
stick this line c:\boot.zzz="ubuntu or whatever"
now copy boot.zzz to youre c:\ drive reboot and shazam the magic is complete you should be able to load linux from the windows menu and windows from the linux menu, but the windows menu should come up first. Long winded yeas but im quite new to linux and im trying to cook tea!

thacked from these guides

[http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

---

### Post by Kamaria on 2007-04-14
> **lucky2 said:**
> OK ive got you covered sweets, are you running a legitamate windows xp home or pro setup? (which one?) if you think you can access the windows xp recovery console (put the original cd in a boot time and follow the options till recovery console) then this should work. boot in to linux goto a teminal window and type "sudo dd if=/dev/hda3 of=/home/<ur user name>/boot.zzz bs=512 count=1" (dumps boot info to file boot.zzz in you're home dir). you say you can access you probably need to mount you're floppy drive? or usb card or what ever and copy the boot.zzz file to something that you can get to from within windows (you can write to an ntfs drive but its dodgy if i remember right) so when you have boot.zzz in you're hand, reboot from the windows xp cd, load up the recovery console, when it asks you to login (if you dont use the administrator account for every day use), login as administrator with no password, or one of youre own logins with youre password if tht does not work. Got prompt? type fixmbr, this will overwrite linux boot loader and stick the windows xp default one back in place, reboot and windows xp should load (you're milage may vary), K so now you should be back in windows xp load up notepad or whatever and open c:\boot.ini , underthe line

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect (or how ever it looks)
stick this line c:\boot.zzz="ubuntu or whatever"
now copy boot.zzz to youre c:\ drive reboot and shazam the magic is complete you should be able to load linux from the windows menu and windows from the linux menu, but the windows menu should come up first. Long winded yeas but im quite new to linux and im trying to cook tea!

thacked from these guides

[http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

I'm running Windows XP Home, however it came pre-installed, and the recovery thing I'm talking about is on a seperate partition. I do have another disc downstairs and I assume I can do the same thing with it though. Let's see how this works.

---

### Post by Kamaria on 2007-04-14
Nope. My XP CD hung up on me all three times before it could even get to a menu. It seems I will have to use the recovery partition after all.

---

### Post by Kamaria on 2007-04-14
Reinstalling GRUB hasn't worked either, so I'm going back to my final option of the recovery thing. If that doesn't work......I'm going to have to find a way to back everything up and reformat.

---

### Post by Kamaria on 2007-04-15
I've exhausted almost all of my options. My Windows XP SP1 CD won't even load up to where I can access the recovery console (it freezes before I reach a menu) and the recovery PARTITION on my drive only screwed over the boot loader so I had to re-install GRUB again.

Is there any other way to boot into Windows and access the recovery console?

---

### Post by lucky2 on 2007-04-15
I dont know how the grub loading windows process works and cant test it myself (I use ntldr windows to manage dual boot) so the only thing I can suggest you have already tried, I just had a quick sniff around and found 'http://www.cgsecurity.org/wiki/TestDisk' which looks like an open source data recovery tool, it says it will run under Linux and recover NTFS boot records from the backup copy at the end of the partition, weather it will do both at the same time or not I dont know and to be honest I dont know how bushy you're windows installation is but if its trim then probably quicker just to re-install, cheers!

---

### Post by Kamaria on 2007-04-15
I think I completely screwed over my Windows install somehow. I used Super Grub Disk to put the Windows Bootloader back on, but start-up only showed a couple of Ys and a garbled character or two.

I'm going to try converting to FAT32 and move the boot flag to see if that does anything.

---

