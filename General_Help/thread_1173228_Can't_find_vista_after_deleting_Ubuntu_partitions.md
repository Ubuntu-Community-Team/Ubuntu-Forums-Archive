---
title: "Can't find vista after deleting Ubuntu partitions"
date: 2009-05-29
forum: General Help
---

### Post by TheNeo on 2009-05-29
This is a serious issue for me. I deleted the partitions that held Ubuntu to make up some space for SLES 9.0 for school. Now when I rebooted (not thinking of course) grub errored out giving me 22. Figured it out that it was the Loader and then tried my Vista Recovery Disk. Found out that it wanted to reformat my entire hard drive so I ejected the disk at 0%. Next I tried to download the recovery torrent that helps rebuild the WinBootMng, but then it tells me no Windows on and fails to rebuild BootLoader. Next I try to manual recreate it from scratch failed there. Finally, I reinstall Ubuntu to see if I can find some type of software to recover the missing partition. Ubuntu says there is nothing there, but empty space!
```
colton@colton-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab5ce5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6761    54307701    7  HPFS/NTFS
/dev/sda2            6762       30401   189888300    5  Extended
/dev/sda5            6762       29437   182144938+  83  Linux
/dev/sda6           29438       30401     7743298+  82  Linux swap / Solaris
```
I have a 220 GB drive. I had about 120 Gig of files in NTFS school, family, just about everything I've been working on for the past year. I really really really need to get it back if anyone knows how to recover missing partition please help! Thanks in advance

---

### Post by fuzzyworbles on 2009-05-29
so when you mount /dev/sda1 it says that it's empty? if that's the case you're probably hosed. if i were you i'd just dig around the internet for live cd file recovery utilities and hope for the best. my money is that your windows "rescue" disk did a fast reformat, which completes in a snap, so maybe you weren't fast enough!

---

### Post by Sidewinder1 on 2009-05-29
I'm not trying to be a "smart-alec" but I've seen this type of question asked several times before on this board. Try a search for lost ntfs data, lost ntfs partition, etc....
I don't remember or I'd tell you. The good news is I've seen some recovery schemes that have been reported to have worked (read them on this forum).
HTH, Side

---

### Post by cariboo on 2009-05-29
Have a look [here]("http:///neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the version for your installation.

---

### Post by anarchyinc on 2009-05-29
You can fix this with a Linux recovery program in the form of a live cd. OpenSUSE and Debian comes with one last I checked. Not sure if ubuntu has one or not. Fix grub first, boot to windows when repaired. Or continue to reformat the old ubuntu partitions and reinstall ubuntu.

---

### Post by TheNeo on 2009-05-29
> **fuzzyworbles said:**
> so when you mount /dev/sda1 it says that it's empty? if that's the case you're probably hosed. if i were you i'd just dig around the internet for live cd file recovery utilities and hope for the best. my money is that your windows "rescue" disk did a fast reformat, which completes in a snap, so maybe you weren't fast enough!

Out of everyone here I have a feeling your right man. Last thing I'm gonna try is hook it up to another comp that contains XP and search from there.

---

### Post by TheNeo on 2009-05-29
> **Sidewinder1 said:**
> I'm not trying to be a "smart-alec" but I've seen this type of question asked several times before on this board. Try a search for lost ntfs data, lost ntfs partition, etc....
I don't remember or I'd tell you. The good news is I've seen some recovery schemes that have been reported to have worked (read them on this forum).
HTH, Side

Oh I know man I had a strong feeling I was going to get that reply. From what I've seen its in every post. Problem for me is I don't have a second to do **** seriously so I really appreciate everyone replying to the already dealt with situation.

---

### Post by TheNeo on 2009-05-29
> **cariboo907 said:**
> Have a look [here]("http:///neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the version for your installation.

This is what I did second and like I said to the guy above I believe that "Recovery" disc did a quick reformat or something because I can't find any files, the link you sent me has a repair option that states no windows on HD, and lastly to add to the heap of problems it gave me directions to create a WinBootMnger from scratch and the torrent either didn't have the file "bootsect.exe" or I'm missing something because after I tried that option I reboot and get this "no bootable device available.. insert disc or something something."  Another thing is I finally broke down and tried reinstalling Ubuntu to see if I could possibly find a fix from that angle and when the partition program came up it told me I had only 50ish Gig of NTFS and the rest was unallocated (170 gig where all my data was!!) so it seems I might be really screwed unless there is some kind of "free" advanced recovery tool. 
Once again appreciate everyone's response.

---

### Post by TheNeo on 2009-05-29
> **anarchyinc said:**
> You can fix this with a Linux recovery program in the form of a live cd. OpenSUSE and Debian comes with one last I checked. Not sure if ubuntu has one or not. Fix grub first, boot to windows when repaired. Or continue to reformat the old ubuntu partitions and reinstall ubuntu.

I've found something called, I know I'm a noob so you guys probably know this like 2nd nature, "rescue start end." Well that brought out the 50 gig NTFS partition but that doesn't have any content from past. It also has NTFS-config which did the same thing so still back at point "A". Thanks though.

---

### Post by TheNeo on 2009-06-06
For anyone interested I downloaded a torrent called GetDataBack which is a recovery software that brings up everything that has ever been on your harddrive. It takes about 12 hours to find all files for a 220 gig and then much longer to actually recover them. This was after I deleted all files, reformatted, and installed a different OS so it can be done. The only true way to delete files is by disk wiping and it needs to be done about six times to clear all data. What is needed is the torrent cables that are compatible to hook up your HD to another comp and I "believe" windows for that particular torrent.

---

