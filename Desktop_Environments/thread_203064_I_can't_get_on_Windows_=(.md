---
title: "I can't get on Windows =("
date: 2006-06-24
forum: Desktop Environments
---

### Post by Thanatios on 2006-06-24
Hello everyone :) 

Lets start with telling what kind of stations I had before I installed Ubuntu:
C: (NTFS) D: (NTFS) G: (EXT3)

When I tried to install Ubuntu, it said that I needed an Linux Swap file. So I tried to create another station using the Ubuntu Live Install disk. So I created a Swap station, and moved fort to install Ubuntu. But I didnt get far, because I got an error saying that I dont have a Swap Station. So I got back to fix it. Out there I noticed that my extra Swap Station has the filesystem: Unknown. And same thing happened with my Windows station (C:).
So I found a way to still change the filesystem in the Swap station, at the Disks Manager. And so I installed Ubuntu (am on it right now, really sweet :D ).
But the filesystem for C: Coulnt be changed back to NTFS. Only VFAT. And that doesnt work for me when I try to restart.

So now my stations are:
C: (VFAT) (The bugged one)
D: (NTFS)
G: (EXT3)
H: (Linux Swap)

So my question is:
Is it possible to change the filesystem of my Local Station C: (The Windows Station) to NTFS again, using Terminal, DOS or just Ubuntu?

I would be really thankfull if someone could help.

---

### Post by bscbrit on 2006-06-24
Where did you create the swap space?  Did you have some free space (i.e. unallocated) space on the drive?  If not, I'm wondering if you have corrupted your C:\ drive by taking some of it for your swap partition.

---

### Post by Thanatios on 2006-06-24
Well, humn, I have installed Windows XP again (Took me 20 mins), on Station C. But now for some reason, I can't find my Station D. It just... Disapeared O.O Any idea why?

And also, how do I logon to Ubuntu now again? Or do I need to re-install it again? Because I dont get the book screen anymore.

Kind regards,
Thanatios

---

### Post by bscbrit on 2006-06-24
Unless you have a linux recovery disk, I think you will have to re-install but don't take my word for it!  Wait a short while and see if anyone comes up with a better solution.

The problem is caused by Windows.  Linux distributions (including Ubuntu, of course) are intelligent enough to recognise a Windows installation and thus create a dual-boot option.  Microsoft think it should be otherwise.  If you install Windows it will simply ignore your linux partitions and refuse to give you the dual-boot option.  If you know which partitions were used for '/', swap etc it is _possible_ to recreate the grub fairly easily, but I'm betting that you do not have that information written down anywhere.  Therefore a re-installation of Ubuntu might be your only way to get both working again.

---

### Post by ifokkema on 2006-06-24
[QUOTE=bscbrit]Unless you have a linux recovery disk, I think you will have to re-install but don't take my word for it!  Wait a short while and see if anyone comes up with a better solution.

The problem is caused by Windows.  Linux distributions (including Ubuntu, of course) are intelligent enough to recognise a Windows installation and thus create a dual-boot option.  Microsoft think it should be otherwise.  If you install Windows it will simply ignore your linux partitions and refuse to give you the dual-boot option.  If you know which partitions were used for '/', swap etc it is _possible_ to recreate the grub fairly easily, but I'm betting that you do not have that information written down anywhere.  Therefore a re-installation of Ubuntu might be your only way to get both working again.[/QUOTE]
Windows has overwritten the 'MBR', that is the part of your disk where a program is installed that actually boots stuff on your drive. Right now there's Microsoft crap there. You need to get Grub back. **You don't have to re-install Ubuntu, though :)**

Just check out this page:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Thanatios on 2006-06-24
Well, everything works fine now. Thanks guys!

Except for 1 thing. And thats my Local Station D:
For some reason I cant use it anymore at all. I kept data on it like games, documents and music and such. But now I cant access it anymore.
Can't use it with Linux, since it doesnt support NTFS
Can't use it with Windows, since it doesnt show up in my Computer O.O

Any suggestions? Thats like my last problem, making D show up in my computer again. :-?

---

### Post by ifokkema on 2006-06-24
[QUOTE=Thanatios]Well, everything works fine now. Thanks guys!

Except for 1 thing. And thats my Local Station D:
For some reason I cant use it anymore at all. I kept data on it like games, documents and music and such. But now I cant access it anymore.
Can't use it with Linux, since it doesnt support NTFS
Can't use it with Windows, since it doesnt show up in my Computer O.O

Any suggestions? Thats like my last problem, making D show up in my computer again. :-?[/QUOTE]
Well, this looks more Windows related :) LOL
I've had this once, too. Right click on "This computer", and click "Manage". There is some option for disks there. Something like "Disk manager". You can view your drives and all partitions. What does windows say about your partition? Can you right-click it and assign an drive letter?

---

### Post by Thund3rstruck on 2006-06-24
Actually you can modify your boot.ini file in windows to recognize your linux install and provide an option at boot. I've had to do this once... a long time ago. Search on google for boot.ini and linux

---

