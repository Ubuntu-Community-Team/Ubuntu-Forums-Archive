---
title: "Uninstalling Ubuntu- GRUB issues and more.."
date: 2006-08-10
forum: Desktop Environments
---

### Post by CBTF on 2006-08-10
I decided to try ubuntu. While it was fun and smooth, ATI drivers made it a nightmare. 

I removed my linux partitions an allocated the space from them back into my XP partition.

I just solved an issue where I was recieving BOOT.INI errors at windows startup that were related to the GRUB loader.

Now my startup is still messed up. Windows wont play startup chimes, even on a fresh format. This is related to GRUB.Nitpicking I know but i shouldnt have to feel like stuff is broken b/c of ubuntu.

Does anyone have any suggestions?

---

### Post by computergroove on 2006-08-10
get the diagnostic utility for your hard drive and write zeros to it. Pretty much guarantees a clean hard drive includingthe removal of grub. Then reinstall XP.

---

### Post by BoneKracker on 2006-08-10
Just restore the full backup you made in Windows right before installing Ubuntu, right?

You don't need to zero-fill your drive.  Use the Windows recovery manager (part of the installer CD) and restore the Master Boot Record (MBR).

It's a command-line utility.  You might want to read about it a bit before trying it if you've never used it before.

---

### Post by computergroove on 2006-08-10
He already formated his drive and reinstalled XP and he is still having the same problem. Windows installs a new boot record during a formated fresh install and he still has grub floating around. It is unlikely that rebuilding the MBR again will remove Grub.

---

### Post by CBTF on 2006-08-10
> 
You don't need to zero-fill your drive. Use the Windows recovery manager (part of the installer CD) and restore the Master Boot Record (MBR).

I used an MBR fix- still having issues.


> get the diagnostic utility for your hard drive and write zeros to it. Pretty much guarantees a clean hard drive includingthe removal of grub. Then reinstall XP.

The problem here is that my windows xp is OEM and based on a recovery partition.

Any ideas? MBR did nothin, im confused.

EDIT: found this config text file in my C drive, anyone see anything wrong?
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


---

### Post by computergroove on 2006-08-10
OK no problem. I am not sure how versed you are with computers. 
Read this in its entirety before you begin. You might not be up to doing this. This isnt beginner stuff. Your recovery partition has a I386 folder - Burn it to a cd. 
Download and burn freedos [www.freedos.org](www.freedos.org) then either copy this file - [http://www.devedia.com/cgi-bin/ctdld.cgi?ftp://ftp.cyf-kr.edu.pl/pub/mirror/Microsoft/softlib/MSLFILES/PD0805.EXE](http://www.devedia.com/cgi-bin/ctdld.cgi?ftp://ftp.cyf-kr.edu.pl/pub/mirror/Microsoft/softlib/MSLFILES/PD0805.EXE)
to a floppy or burn it to a cd. (This file is a free version of smartdrv which will be important later). Get the hard drive utility we talked about before and write zeros to the drive. Next start the computer with cd rom drive support with the freedos cd.
At the command prompt type
1. fdisk and hit enter
2. agree to enable large disk support and hit enter
3. make a partition (option 1)
4. make a primary dos partition (option 1 again)
5. tellit yes to using the entire contents of the drive
6. When it is finished reboot the computer and start with cdrom drive support
7. at the prompt you need to format the drive. I am not sure the exact location of the command in freedos so you can try one of 2 things here:
a. type format c: <enter>
this will either start formating your drive or it will sat unknown command. If it says Unknown command      b. type dir format.com /s <enter>
you will get something like contents of d:\command\
format.com. 
d:\command is the location of format so we have to goto that directory to access and use the command for our purposes. 

type cd command (if thats the location of 
command.com) and hit enter.

Now retype format c: <enter> When it asks you if you are sure you want to format choose Y for yes. When it is done type c: <enter>

You should see c:\>


Put in either your floppy or your cd with the PD0805.EXE command on it. If its on cd
type d: <enter>
If its on floppy
type a: <enter>
Now type PD0805.exe <enter>
It will probably seem that nothing really happened but it did. 
Next type c: <enter>
type md i386 <enter>
type cd i386 <enter>
put your i386 cd into the drive and
type copy d:\i386 <enter>
This will copy all the windows xp installation files onto your hard drive. It will take a while.
When its done copying type winnt <enter>
You should come to a blue screen where it will ask you where the location of the i386 folder is. Just hit enter to continue. The computer will copy files for a bit and reboot. You should recognise this screen and be able to take it from here.   

By the way - Dell offers the Windows XP media with a new system for an extra $10. Do it next time if you dont want to go through this again.

---

