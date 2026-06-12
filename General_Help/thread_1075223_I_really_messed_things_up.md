---
title: "I really messed things up"
date: 2009-02-20
forum: General Help
---

### Post by WYSIWYGeekgrl on 2009-02-20
I have several problems that I hope someone can graciously assist me with as I am new to Linux and have only been using it for about one month. 
I decided after having so much trouble with windows and having to replace a bad hard drive and reinstall everything (only to have it all undone by using software to scan the computer to assist on updating drivers)..to install Ubuntu (which I absolutely love!) 
I installed Intrepid along side windows xp because we could not do anything in windows, (after the driver update thing). Could not get on-line or even burn a cd to back things up. 
Within Ubuntu we were able to get the drivers that we needed for the computer and burn them to cd, and managed to get windows running once more. YAY!! 
I have however, made a huge mistake in the partitioning, that I didn't realize at the time. 
I have a 500 gig hd that was just installed and windows xp is only using 3 gigs of it.(NTFS)
Needless to say we keep getting errors about disk space and to un-install things because of it. 
I thought I would like to start over completely and gain the rest of the hardrive back..SoOoo..I thought that I would just pop in the recovery disk (Gateway 838gm) and redo everything over, thinking that..that would "fix" things back like new [-o<..That didn't work. [-X Now I don't have the option to boot into Ubuntu. 
I want to recover disk space, install my computer back to the original configuration and then install Ubuntu **properly** along-side windows. 
Believe me I wouldn't bother with windows but there are **some things** that I **have** to have. One being as trivial as it may sound, is my magicjack, as I don't have a home phone. 
I read something about using "gparted" is this something that I need to do? 
I have the live cd, but I am unsure of how to go about it and I am afraid of messing things up worse than they are. I hope someone can tell me what exactly I need to do so that I won't make the same mistakes twice.:oops:

---

### Post by northern lights on 2009-02-20
gParted is a common GNU/Linux GUI partitioning tool. It can handle resizing of ntfs partitions, which is what you'd want to do.

Boot your Ubuntu, run gParted, right-click the Windows partition's representation, and choose "Resize". Adjust its size to your liking and reuse the unallocated space (create new partition(s) and/or append some space to your existing ext3 partition(s)).

For clarification of your setup, can you post the output of```
sudo fdisk -l
```Thank you.

---

### Post by WYSIWYGeekgrl on 2009-02-20
Thank You for your reply :)
Here is the info you requested:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         393     3156741    7  HPFS/NTFS
/dev/sda2             394       60801   485227260    5  Extended
/dev/sda5             394        1656    10145016   83  Linux
/dev/sda6           60434       60801     2955928+  82  Linux swap / Solaris
/dev/sda7            1657       60065   469170261   83  Linux
/dev/sda8           60066       60433     2955928+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by L a r r y on 2009-02-20
I am relatively new to Ubuntu nyself, running currently Ubuntu 8.04.  I re-installed Ubuntu using the version 6.06 Dapper Drake  live cd, then upgraded it online to 8.04 because I could not get an 8.04 live cd to work.  I came to a prompt and no idea where to turn next on the Ubuntu 8.04 live cd.

I took a look at the GParted site with a Google search for gparted.  That program should let you resize your partitions and not lose your data.

I would allow about 40 gig for the file system and about 60 + gig for your home directory, because under Wine, you can install Windows software in Ubuntu.  I currently run EchoLink, an amateur radio program that lets me connect to distant radios around the world via the Internet; Cool Edit 96, an abandoned shareware, but still a great sound recorder and editor; Mailto Obfuscator, a Windows program that lets me encode email addresses in my Web pages.  There are some good counterparts in Linux for some of these, but the Windows programs just have a more familiar look and feel.

Some Windows programs don't work so well in Linux under Wine, but you never know until you try.  I have Winamp, which works well, but its library is a bit tricky and moving the program around on the screen can get real dicey.

Your Windows programs and their virtual Windows environment are all housed in your home directory -- this is why I suggest so much space for the home folder.

If you need to install gparted, you can do so within your Terminal: 

sudo apt-get install gparted

Typing gparted into my Terminal advised me that I do not have it installed, but gave me the directions I just passed along.

One place you can get help is in your Terminal.  Just type:

man commandname

where commandname is the name of a command that you want help with.  There is a lot of documentation available through the man system, but it is not a complete library.

Re-installing Windows does blow away the dual boot menu and that requires not a full reinstall of Ubuntu, but I can't recall what exactly I had to do..... perhaps nothing more than booting from a live cd and making repairs.

I hope this general discussion is of help.
--
Larry

Edit:  The question was answered and responded-to while I was writing!

---

### Post by geirha on 2009-02-20
Sounds like the recovery cd just overwrote the MBR with Windows' boot loader. This is the same thing that happens when you install windows after installing ubuntu, so the following should apply to your case too: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by WYSIWYGeekgrl on 2009-02-20
> **L a r r y said:**
> 
I took a look at the GParted site with a Google search for gparted.  That program should let you resize your partitions and not lose your data.

I too googled it, and hoping I do it right =)

> I would allow about 40 gig for the file system and about 60 + gig for your home directory, because under Wine, you can install Windows software in Ubuntu.  
Some Windows programs don't work so well in Linux under Wine, but you never know until you try.

I have had problems with *some* software using Wine, but I probably dont have it configured right. I wish magicjack was compatable.        

> I hope this general discussion is of help.
--
Larry

Thank You for Your response. All help is **greatly** appreciate!

---

### Post by WYSIWYGeekgrl on 2009-02-20
> **geirha said:**
> Sounds like the recovery cd just overwrote the MBR with Windows' boot loader. This is the same thing that happens when you install windows after installing ubuntu, so the following should apply to your case too: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thank You! Checking it out now! :)

---

### Post by WYSIWYGeekgrl on 2009-02-20
**Thanks to all of you that have been so very helpful with my problem!**
I will post the outcome later today when I get a chance to do some of the things suggested. I would try and do them now but it's almost 4 am here and I feel it would be best for me to try and get this resolved when I'm more awake, lol.

---

### Post by WYSIWYGeekgrl on 2009-02-21
Thanks to All who helped me out with this!:D
I'm **very** happy to report that everything is running smoothly thanks to your suggestion! 
You guys rock! *dances* \\:D/

---

