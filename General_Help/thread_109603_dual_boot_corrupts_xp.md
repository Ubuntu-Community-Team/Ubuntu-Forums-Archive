---
title: "dual boot corrupts xp"
date: 2005-12-29
forum: General Help
---

### Post by fakie_flip on 2005-12-29
I have been trying to install Linux with XP on three computers that all had one harddrive. My computer has two harddrives. Therefore I did not have the same problem. About the first ten times I tried to install a dual boot on those three computers, I was using Ubuntu 5.10. Every time I would install XP and leave free space for Linux. XP would work fine after this except it needed sound drivers(Ubuntu had my sound drivers). Then I installed Ubuntu, and used when the partitioning tool came up, I used the option "use the largest amount of continuous free space". After that, Ubuntu worked fine, but when I tried to load Windows, this message came up in black and white:

Windows could not start because thed following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please reinstall a copy of the above file.

I want to make a full Linux system on these computers, but their owners are new to Linux and are not ready to have full Linux systems yet. I thought that this problem was a problem with the new Ubuntu 5.10 untill today when I tried to install Debian with the same method. Ubuntu uses the Debian installer, so I followed the same procedure and the same problem happened. The computer I've been working with the most has a 120 GB hdd with a nvidia vanta 6 video card, but I don't think the problem is the harddware because I have the same problem on each computer. Has this problem ever been reported before? What is causing it? What can be done to solve this problem?

---

### Post by harisund on 2005-12-29
Hmm.. I am not sure I completely understand what you are saying.. but from what I understand you want both Ubuntu and Windows XP all on a single hard disk. 

If you are starting fresh (meaning you don't have any data you want backed up) then go ahead with the Windows install and during the install create partitions and choose the partition to install Windows first, and then use the Ubuntu CD's manual partition option and install where you want. (Do not use the "use the largest amount of continuous free space" option_)

---

### Post by scunc_dvl on 2005-12-29
This may be simply because NTFS (the filesystem used by Windows) isn't well known nor easy to manipulate, and the partitioner made a mistake by chance.. though especially with a relatively large disk and a fresh XP install, I think this scenario is pretty unlikely.

When I made my dual boot, I defragmented XP thinking I wouldn't want to clobber any file fragments (or risk having the partitioner move them). I don't think anyone recommended this, and maybe it makes no difference, but my installation worked.

---

### Post by DevilsAdvocate on 2005-12-29
I've a dual-boot set up that I've installed and reinstalled multiple times (both XP and Ubuntu).  I suggest creating the 2 partitions you want before hand; i.e., an XP partition and a Linux partition...with a little free space at the end.  Then do the install.  I don't know if the "use free space" option works as I've always done it this way.

---

### Post by zoiks on 2005-12-29
This might be an error in the grub install.

Note that a Linux install of pretty much any sort isn't going to mess with the files in the WinXP partition.  The only thing that it will do to affect Windows is change the MBR (master boot record) of the first bootable hard drive.  The normal MBR that Windows installs just silently starts up the appropriate Windows files to load the WIndows OS.  (Incidentally the Windows installer will generally clobber any special bootloader you have like grub, that's why you have to install Windows first.)

When you install Linux with grub, grub will rewrite the MBR so that instead of just loading up the Windows stuff, it will give you a menu of options of OSs to start up.  If you choose WIndows, it's supposed to load up the proper Windows files and voila - Windows is running.

It's possible grub is pointing to the wrong directory and/or files.  Is your "<windows root>" location in an unusual place?  Perhaps, does it have spaces in the directory name?  Did you configure grub in a weird way perhaps?  (These are just wild guesses.)

---

### Post by towsonu2003 on 2005-12-29
I saw this a couple of times in the forums, try a search for hal.dll in the forums. 

These seem to be fine for the starters (read all before acting):

[http://ubuntuforums.org/showthread.php?t=106666&highlight=hal.dll](http://ubuntuforums.org/showthread.php?t=106666&highlight=hal.dll)

[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

[http://www.ubuntuforums.org/showthread.php?t=78509&highlight=missing+hal.dll](http://www.ubuntuforums.org/showthread.php?t=78509&highlight=missing+hal.dll)

[http://www.ubuntuforums.org/showthread.php?t=73254&highlight=missing+hal.dll](http://www.ubuntuforums.org/showthread.php?t=73254&highlight=missing+hal.dll)

good luck.

Oh, and a note: if you decide to reinstall everything, 
1. use a live cd (ubuntu or a small thing like R.I.P.) to partition hard disk
2. install windows first
3. install ubuntu second using expert partitioning w/ the partitions you created...

---

### Post by Danielle on 2005-12-29
hi, you **might** be able to fix it with the windows cd.

 again, you might be able to fix it with a live ntfs cd like ubcd4win by editting the boot.ini in system32. if windows gets confused about the partitons and gets it wrong you will receive that error message. editting boot.ini will fix it **if** when you have alook at the ini file the partition infomation is incorrect.

---

### Post by fakie_flip on 2005-12-29
I don't know if this is weird or normal, but Windows works. The person's computer I am working on a ntfs partition 40 gb for music and backup files. Its drive letter is C: instead of the partition with windows installed being C: The partition with Window's installed is D: and the boot.ini is on the C: Freespace for Linux is on the harddrive. After reading what people said in this thread, I was going to try qtparted on Knoppix to set up the partitions for Ubuntu. I am going to read and try to figure out what the partitions should be with 256mb of ram. I was confused because before I switched to Ubuntu, Linux needed three partitions to work right. With Ubuntu, there were only two partitions for it. I wondered if grub tried to boot the wrong ntfs partition. That probably does not happen because I had the same thing happen on other computers without a third ntfs partition. boot.ini looks like this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

I don't know if the guided partitioning tool on Ubuntu was causing the problem because it shows what it does to the partitioning table before it writes out all the changes, and it is the same changes I would have made if I were doing the partitioning manually. The extra partition I was talking about contains all of the backup files, and it is still there each time i reinstall windows. The person says it would take a long time to put all of the music(30gb) back on there. I will try qtparted. Thanks for the suggestions.

---

### Post by fakie_flip on 2005-12-29
What is the best and correct way to set up the partitions? Remember I have left at least 30gb free for Linux and Windows is already reinstalled.

---

### Post by Bachstelze on 2005-12-29
I would recommend manually partitioning the hard drive when installing Ubuntu instead of letting the installer doing it. Automatic partitioning is really unpredictable.

---

### Post by towsonu2003 on 2005-12-30
[QUOTE=fakie_flip]What is the best and correct way to set up the partitions? Remember I have left at least 30gb free for Linux and Windows is already reinstalled.[/QUOTE]
I would go with:
5GB -> /
RAM x2 -> swap (if you have 216MB RAM, then 512MB swap)
rest ->/home

---

### Post by popeyeray on 2006-01-01
I found the following link that fixed problem in 5 minutes. I used **[COLOR="Red"]Method 2[/COLOR]**
[http://support.microsoft.com/?kbid=314477]("http://support.microsoft.com/?kbid=314477")

Method 2
Use the Bootcfg utility in the Recovery Console to correct the Boot.ini file:
1.	Use the Windows XP CD-ROM to start your computer.
2.	When you receive the message to press R to repair Windows by using the Recovery Console, press the R key.
3.	Select the Windows installation that you want, and then type the administrator password when prompted.
4.	Type bootcfg /rebuild, and then press ENTER.
5.	When the Windows installation is located, the following instructions are displayed:
Add installation to boot list? (Yes/No/All)
[Type Y in response to this message.]

Enter Load Identifier:
[This is the name of the operating system. Type Windows XP Professional or Windows XP Home Edition.]

Enter OS Load options:
[Leave this field blank, and then press ENTER].
After you perform the preceding steps, restart the computer, and then select the first item on the boot menu. This should allow Windows XP to start normally.

After Windows XP has successfully loaded, the Boot.ini can be modified to remove the incorrect entry.

I always install the recovery console after SVPK 1, you won't be able to with SVPK 2. The recovery console can save your bacon if Windows is not booting all the way.:mad:  Go here for recovery console _**[COLOR="Red"]installation[/COLOR]**_ instructions:
[http://support.microsoft.com/default.aspx?scid=kb;en-us;307654]("http://support.microsoft.com/default.aspx?scid=kb;en-us;307654")

---

### Post by SiliconJon on 2006-01-06
I had a similar problem this evening.  After my first install of first XP then Ubuntu, my XP installation went amok claiming the loss of a file (of which I did not take note of its name).  After trying again with a few irrelavent differences, I realized what I had done and corrected it on the third installation.

The first two times the root linux ext3 partition was assigned as the boot partition, the first time using the automated partitioning option, and the second time patitioning manually but making no difference as I followed the automated method's lead.  Windows did not like this, and finally cooperated when I left my NTFS/XP Pro partition as the boot partition on the third attempt.

Sure would have been easier and faster to fix that manually!

---

