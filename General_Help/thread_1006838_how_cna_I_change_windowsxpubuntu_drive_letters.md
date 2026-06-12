---
title: "how cna I change windowsxp/ubuntu drive letters?"
date: 2008-12-09
forum: General Help
---

### Post by JohnParker on 2008-12-09
After dual booting windows xp, the drive letter is set to J, this is very annoying and it wont allow some programs such as soldier front to install. The ubuntu partition is kind of " Blocking off"the letter C from being used. How can I change the drive letter in ubuntu?

---

### Post by oilchangeguy on 2008-12-09
> **JohnParker said:**
> After dual booting windows xp, the drive letter is set to J, this is very annoying and it wont allow some programs such as soldier front to install. The ubuntu partition is kind of " Blocking off"the letter C from being used. How can I change the drive letter in ubuntu?

you can't change the drive letter, where windows is installed, without doing a reinstall. how did you set up your dual boot? windows first, or ubuntu? windows first the drive letter would be c. ubuntu did not change the drive letter of windows, that's not possible.

---

### Post by LoneWolfJack on 2008-12-09
it IS possible to change drive letters (at least in win2k it was). it's somewhere in system->devices when you right click on the respective device.

other than that, you probably installed ubuntu first.., as windows doesn't really acknowledge the existence of any other OS, you should install it first and let ubuntu clean up its mess.

---

### Post by oilchangeguy on 2008-12-09
> **LoneWolfJack said:**
> it IS possible to change drive letters (at least in win2k it was). it's somewhere in system->devices when you right click on the respective device.

other than that, you probably installed ubuntu first.., as windows doesn't really acknowledge the existence of any other OS, you should install it first and let ubuntu clean up its mess.

not in xp, can't be done. and it's not windows not acknowledging another os, it's the other os's mbr gets overwritten. and how many posts are there where grub has not seen windows??????????? there's no way to know what the op has done. because even if you install windows after ubuntu, windows will still call it's partition c:

---

### Post by oilchangeguy on 2008-12-09
in some rare cases windows will during install give the hard drive another letter other than c. what the op can do is to open the computer and unplug everything but the hard drive and the cd drive. install windows, then plug everything back in.

---

### Post by Slim Odds on 2008-12-09
> **oilchangeguy said:**
> ....because even if you install windows after ubuntu, windows will still call it's partition c:

That's silly. A drive letter is an abstraction. It has nothing to do with which partition is used. Same with mount points in linux. You assign them. They are abstractions.

---

### Post by LoneWolfJack on 2008-12-09
not necessarily... in fact, it happened to me more than just a couple times that windows wouldn't call the first drive c (this was in my win98 days though).

can't be of much help to the op here short of recommending to remove all drives except one, clear all partitions from it and reinstall.

---

### Post by oilchangeguy on 2008-12-09
> **Slim Odds said:**
> That's silly. A drive letter is an abstraction. It has nothing to do with which partition is used. Same with mount points in linux. You assign them. They are abstractions.

you don't assign the drive letter to windows.

---

### Post by Slim Odds on 2008-12-09
> **oilchangeguy said:**
> you don't assign the drive letter to windows.

With the administration tools you can change any drive to any letter you want (as long as it not already in use). It's problematic to change the install drive letter after the install. But it's still just an abstraction.

I've changed the driver letter for many different drives for various reasons.

In general, if you're going to dual boot, it best to partition with a primary partition for windows first. Then, install windows first. That fact that windows wants to be the whole world is the main problem.

---

### Post by oilchangeguy on 2008-12-09
> **Slim Odds said:**
> With the administration tools you can change any drive to any letter you want (as long as it not already in use). It's problematic to change the install drive letter after the install. But it's still just an abstraction.

I've changed the driver letter for many different drives for various reasons.

In general, if you're going to dual boot, it best to partition with a primary partition for windows first. Then, install windows first. That fact that windows wants to be the whole world is the main problem.

from disk mgt you cannot change the drive letter of where windows is installed. you get an error message that says windows can not modify the system volume or boot volume.

---

### Post by timmahhny on 2009-01-11
Hey folks, Ubuntu does change the drive letters, and it just happened to me. I have a PC that **was running** Vista Home Premium, got stupid, installed Ubuntu, and now can't boot into either OS. Drive C, became drive D. Now am searching all around trying to undo this mess. 
 I had a bad gut feeling about installing Ubuntu, but did it anyway on this PC. I should have left it alone, but am not going to do a reinstall, because that would mean, I have to reinstall all the programs that I had, register them, and in a few cases, would have to call, tell them what happened, and get their permission to run a program, that I bought. 
 So, for those that do not think that installing Ubuntu will not change the drives, it will. It has done this to me before in the past when I was running XP pro. Then, I just made that machine fully Ubuntu, but can't do that on this PC. 
 I will work it out, there has got to be a way to do it. Swapping hard drives is not going to work, all ready tried that. I am now going to try something else, and will post it here when I am done. 
timmahhny

---

### Post by mdurham on 2009-01-11
> **timmahhny said:**
> Hey folks, Ubuntu does change the drive letters, and it just happened to me. I have a PC that **was running** Vista Home Premium, got stupid, installed Ubuntu, and now can't boot into either OS. Drive C, became drive D. Now am searching all around trying to undo this mess. timmahhny
timmahhny, how do you know that C became D if you can't boot?
Can you take a look with the live CD.

---

### Post by timmahhny on 2009-01-11
> **mdurham said:**
> timmahhny, how do you know that C became D if you can't boot?
Can you take a look with the live CD.

 I could see the drives when I used my Vista DVD when I attempted to fix the mbr. 
 Here is what I am running.
Xclio box
Asus M3N-HD/HDMI (MB)
AMD 8750 Tripple Core Phenom 2.4+ghz
Nvidia Geforce 8800 GT
Creative X-Fi Titanium Audio Card
4 gigs of DDR2 1066 RAM
1-750 Gig SATA HD
1-650 Gig SATA HD
1-250 Gig IDE HD
1-120 Gig IDE HD

 I have the 650 gig split into two partitions, one is the OS and the other is what I call work. 
 I installed Ubuntu on the 250 gig hard drive, using all 250 gigs.
 I think the original install was done with a bad burn, but I did a check on the CD and Ubuntu checker thing, said it was OK. I used gparted to remove Ubuntu partition, then tried reinstalling it. Afterwards, when I kept getting grub error 17, I downloaded another iso, burned it and tried it again. Same thing, could not boot. 
 I then downloaded the Vista Boot Fixer, and tried fixing the mbr the way it was posted on M.S website. that failed. **But, I found out that my OS was changed from "C" to "D" drive. **I tried swaping the drives, did not work. I tried removing all but the one drive, but of course that would not work, because that hard drive is partitioned into the "OS" and "Work", so it did not boot. 
 I then found a thread here and removed the grub loader, which set Vista back to original state, then removed Ubuntu partition, using the Ubuntu Live CD. 
Once that was done, I rebooted and everything is working like a charm. 
 I miss Ubuntu. I have Ubuntu installed on one laptop hard drive which I swap out when I want to use Ubuntu, but that gets tiresome and I am losing the small screws. Since I do not have my "backup" PC anymore running Ubuntu, I wanted to throw it on this PC, for when I want to use a real operating system. 
I will try it again, with the new disc, just not tonight. 
 I think the reason why the drives changed is because of Grub and where Grub was pointing too. 
 Timmahhny

---

### Post by Slim Odds on 2009-01-11
Ubuntu does **NOT** change Windows driver letters.

We are to the point where many people think that computers are magic. Just doing things at random.

A drive letter is an **abstraction.** Just as is a linux/unix mount point.

Windows assigns the driver letter to the partition.

Please be aware that Windows is **extremely unfriendly** about sharing the computer with ANY other OS.  Whereas Ubuntu is quite prepared to share.

The Windows install makes **no attempt** to consider that another OS might already be on the machine and might like to get booted once in a while.

Whereas Ubuntu normally sets up a dual boot by default is it finds another OS already on the machine.

To have the best chance for a successful dual boot with Windows and Ubuntu, I'd suggest the following:

[LIST=1]
[*]Make the Window partition the first one and a primary partition.
[*]Install Windows first.
[/LIST]
That should make it go smoothly.

---

### Post by Herman on 2009-01-12
:) I agree with Slim Odds, 
> Ubuntu does **NOT** change Windows driver letters.
We are to the point where many people think that computers are magic. Just doing things at random.
A drive letter is an **abstraction.** Just as is a linux/unix mount point.
Windows assigns the driver letter to the partition. That's what I think too.

By co-incidence, something similar to that just happened to me in a computer I'm upgrading for a friend of mine. She had Windows 2000 Professional, and wanted it copied to a larger hard disk.
I installed a larger hard disk in the machine and used a Ubuntu Live CD to copy the contents of the entire hard disk to the larger one with a 'dd' command. 
Then I and ran CHKDSK /R from Windows Recovery Console just to make sure all was okay, and rebooted.
After that I booted the Live CD again and resized the partitions with GParted Partition Editor, and ran CHKDSK /R from Windows Recovery Console again, and rebooted, and so far everything seemed okay.

Finally, I installed Ubuntu on the other hard disk, overwriting the old Windows installation, and installed GRUB to MBR in the first hard disk to dual boot with Windows, as one would normally do.
Ubuntu booted up okay and I installed updates and software.

Windows, however, had two problems. It booted okay the first time, but then it suddenly seemed to wake up to the fact that it was on a strange hard disk and I got 'found new hardware', and Windows wanted to install a driver for the new hard disk. Okay.
That's the point where I think the trouble started.
On reboot it wouldn't give me a login prompt. It had a program called pcAnywhere, which was interfering with that stage of the boot-up and I couldn't even get it to boot into safe mode. 
First I had to install a program called: chntpw in Ubunu in order to edit the Windows Registry and delete an entry for 'awgina', which is part of the pcAnywhere program, so it would revert it's normal 'msgina', and let me log in.
On reboot, I was able to login, but then it said it had no page file or the page file was too small, and rebooted.

And now I'm starting to get to the point. ... here's the link I found that helped me fix it, 
[System Has No Paging File]("http://www.computing.net/answers/windows-2000/system-has-no-paging-file/28269.html") - Computing.net, see post #3.
> This problem can occur if your Windows 2000 boot partition drive letter does not
match the drive letter assigned during the initial Windows 2000 Setup. 
Windows 2000 maintains a record of drive letters in a registry based database and
re-assigns drive letters based on Globally Unique Identifiers (GUID) recorded
for each volume. Should the volume GUID change or be duplicated (by hard drive
cloning software), the original drive letter may not be re-assigned to the boot
volumeNow, this GUID number is the same number that we see in fdisk's output of the MBR when we use the command 'sudo fdisk -lu'.
For example,
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
[COLOR=Blue]**Disk identifier: 0x49294929**[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41576219    20788078+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2        41576220    98092889    28258335   83  Linux
/dev/sda3       153276165   156296384     1510110    5  Extended
/dev/sda4        98092890   153276164    27591637+  83  Linux
/dev/sda5       153276228   156296384     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
[COLOR=Blue]**Disk identifier: 0x0000a95c**[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    22764104    11382021    7  HPFS/NTFS
/dev/sdb2        22764105   156296384    66766140    5  Extended
/dev/sdb5        22764168   150753959    63994896   83  Linux
/dev/sdb6       150754023   156296384     2771181   82  Linux swap / Solaris
```Neither GRUB nor Ubuntu touch the MBR's 'Disk signature', and neither does Microsoft's FIXMBR program. 
The preservation of the MBR's 'Disk Signature' is important to Windows Vista and later.

What happened to me was the opposite, I would have been better of changing the 'Disk Signature', so that Windows 9x will assign default drive letters and allow me to log in.

I tried to get my old [Windows 98 Floppy Disk]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method") to work so I could run fdisk/mbr, that will change the 'Disk Signature', which is the reason people with Vista aren't supposed to use fdisk/mbr. 
As my luck would have it though, this computer didn't seem to want to boot from the floppy for some reason.
Instead, I overcame the problem with a few more 'dd' commands.
First, I 'dd'ed the first 446 bytes of the first hard disk's MBR to a file.
Second, I 'dd'ed the first 446 bytes of the second hard disk's MBR to the first hard disk's MBR.
Third, I 'dd'ed the first MBR's 446 bytes of code from the file to the second hard disk's MBR.
Finally, I re-installed GRUB.

The result is a bootable and fully functioning Windows 2000 Professional.

So, the bottom line is, Windows changes it's own drive letters.
If it has been stimulated to do so by cloning the installation from some other hard disk, it could be the GUID number, (also called the 'Disk Signature', in the MBR that's causing the trouble, (or rather, the fact that Windows is programmed to base it's drive lettering at least partly on that).
Changing the MBR's 'Disk Signature' might solve the problem for other people's computers too, but think twice about that if you have Vista, because that will then make Vista unbootable.

Neither Ubuntu or GRUB write to the Windows partition or any other partition, at least not without being told to, and nor do they change the MBR's 'Disk Signature', or 'drive letter'.
Windows is the one that has a nasty habit of doing things by itself, without the knowledge or consent from the user.

Regards, Herman :)

---

### Post by iggy3 on 2010-11-02
Windows XP have some security issues you can use in your favor.

If you have acess to the partition Windows XP is installed (using an usb  live ubuntu, for example), you can backup your \windows\system32\sethc.exe (to  sethc.bkp, for example) and make a copy of cmd.exe renaming it as  sethc.exe

Then when you try to enter Windows XP and get stuck at the login page  you can press shift 5 times so Windows XP will open sethc.exe (wich in  fact is cmd.exe that you renamed) and you can open the disk management  by typing diskmgmt.msc

I believe that way you will be able to change your partition letter.

---

### Post by iggy3 on 2010-11-02
Actually I've tried that and it doesn't work, because that Windows tool doesn't allow you to change the letter of a system partition.

But with the command line I've been able to change the partition letter using a partition recover software.

But you need to run explorer.exe in the command line, then with explorer open you must run taskmgr.exe and kill the winlogon process. So after you recover the partition (and set it to the proper letter) using any partition recover software you can logon with your username and password once, and use the logon screen to turn off the computer.

Note: there is a limited time you can use the command line so use the partition recover software to scan only a few thousand sectors, just to find the actual partition of the disk wich is the one you're using.

---

