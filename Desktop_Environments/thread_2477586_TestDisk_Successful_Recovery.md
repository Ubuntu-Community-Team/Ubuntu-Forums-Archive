---
title: "TestDisk Successful Recovery"
date: 2022-07-31
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-07-31
Testdisk is a great recovery tool.

I am a fairly experienced Linux user, my system was multi boot.  Previously I had a choice to boot 20:04 LTS, an older 18:04, Linux MX and Windows 10.  

Now recently I wanted to try Google Chrome Flex for PC.  Installation bit confusing, intent was to install onto a USB stick but somehow it went to reformat my main internal drive, realising my mistake I aborted installation immediately but damage done, new partition table had been created.

Annoying  rather than disastrous.

Removed the 1TB disk so that I could experiment at my leisure. 

Used Testdisk, deep search took about 3 to 4 hours on my laptop.  Search options not very intuitive  and I inadvertently  escaped a few times ending up back at command prompt and needing to start the deep 4 hour search again.

Eventually got the hang, result showed many possible recovery areas, methodically checked them in order and one resulted in the complete file system of my 20:04 LTS install.

Copied some folders from my home directory to an attached HD and now, with a fresh new 22:04 installation I am probably in a better position than before.

Despite my experience with Ubuntu and computers in general I did not have an up to date back up so lesson learnt.

Testdisk is an amazing program, cross platform (didn't bother with windows recovery) and it is free.

Geoff Lane

---

### Post by sudodus on 2022-07-31
Thanks for sharing your experience. I think you will be able to help other users here to use TestDisk :-)

---

### Post by ActionParsnip on 2022-07-31
Could have used your backups instead. Far quicker and more likely to recover the data

---

### Post by Geoff_Lane on 2022-08-03
> **ActionParsnip said:**
> Could have used your backups instead. Far quicker and more likely to recover the data

Not sure what backup you are referring to but in my penultimate sentence I did mention I did not have an up to date backup.

Geoff

---

### Post by ActionParsnip on 2022-08-03
> **Geoff_Lane said:**
> Not sure what backup you are referring to but in my penultimate sentence I did mention I did not have an up to date backup.

Geoff

Why not? If your data is important... Why is it not backed up. At present it looks disposable....

---

### Post by Geoff_Lane on 2022-08-04
> **ActionParsnip said:**
> Why not? If your data is important... Why is it not backed up. At present it looks disposable....

The purpose of my initial post was to highlight the effectiveness of testdisk in recovering data.  As I pointed out, the loss of data was annoying, not disastrous.

Of course backup is important and there are many methods of backing up.

Geoff

---

### Post by TheFu on 2022-08-05
I have backup religion, but sometimes use testdisk to restore files that haven't been around even a day that I process.  Sometimes, the processing has corruption in the source files and needs some extra help.  

IME, testdisk is a last resort and only after everything else, even recreating the data, is attempted first.  It is also easier if the drive has been zeroed completely before placing any data on the drive.  To that end, since it is a temporary drive for "sneaker*net" use (effectively), I zero the entire drive weekly just before formatting it.  Test disk won't fine any old data, just the newest stuff, which is my normal recovery need.

The downside to testdisk is that restore files get sequential names.
fXXXXXXXXX
fXXXXXXXX1
fXXXXXXXX2
fXXXXXXXX3
fXXXXXXXX4

Those aren't exactly useful.  Also, if there are multiple versions of the files, there might be multiple versions restored.  Then it becomes a best guess for which is the most recent, as all atime/ctime/mtime data is already lost.

Backups are much easier.  Please get backup religion.  For a business, you can lose your business without backups.  At home, it is usually about convenience, money, and living with someone else who is less interested in why/how all your wedding and baby photos were lost and just wants the data back.  Losing scanned copies of some paper bills isn't very important even if there is a $30 late-fee.  But if you have an expensive item with a long warranty and cannot produce the proof-of-payment + receipt for the entire period of the warranty, that can costs $20,000+.  I have a firesafe for things like that and a bank deposit box (free with the accounts)

---

### Post by Geoff_Lane on 2022-08-09
Zeroing the destination drive is a useful idea.

Whilst some people make a major error of judgement by not backing up properly in my case there really was not any data of any real importance... I have some backed up elsewhere on my home network, photos are generally on my phone and backed up on the cloud.   Documents, if I deem them important, I photo with camera then add text data to properties which makes it easy to find on the cloud.

Testdisk may be a last resort but it worked well for me, after getting used to the terminal commands.

Geoff

---

