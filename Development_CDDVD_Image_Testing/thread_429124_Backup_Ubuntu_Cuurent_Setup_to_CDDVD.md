---
title: "Backup Ubuntu Cuurent Setup to CD/DVD"
date: 2007-04-30
forum: Development CD/DVD Image Testing
---

### Post by witechguy on 2007-04-30
I need help!!

After reinstalling Ubuntu 3 times this weekend, I need to find a way to save a complete copy of my Ubuntu setup before it crashes etc on me again.  I'm looking for a program that will let me make a updated .iso file I can reload later via DVD/CD later.

Any Ideas??

Thanks


-- Wrong forums category I know my bad --

---

### Post by simonn on 2007-05-01
You shouldn't need to re-install, that is soooo windows. Linux does not have a registry to corrupt.

Try actually doing some trouble shooting.

Anyway, in linux everything is just a file so you can more or less just copy files or archive the files on a partition.

---

### Post by witechguy on 2007-05-01
What can I say?  I'm a late Linux Noob.  I wish I got into Linux when I was a teenager in the 90's,  Rather then just messing around with Microsoft.  I bet if the knowledge was all with Linux in how it all works, along with troubleshooting it then, I could trouble shoot it as good as I do with windows.

Ok, so if I just copy the whole **(File System)** to my backup USB drive, then burn it to a .iso it should reload the whole OS over again with installed packages, programs etc I installed earlier in time?

Someone told me to use a package known as PartImage. How good & easy is it to use this program?

---

### Post by ridgeland on 2007-05-11
In Windows I used System Backup - Restore (ntbackup) a lot.  WindowsXP did not install it by default though!!!  I wanted that ease in Linux and finally found it.
I use partimage and a LiveCD from SystemRescueCD
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Each month I make a full copy of my preferred Linux OS (Ubuntu)
I keep several OS on my PC (one is WinXP) 7 others are Linux.
My Ubuntu partition is about 3.5GB so that would fit on a DVD.  I keep Data on a separate partition and use links.  For 7 Linux OS I only have one Firefox bookmarks file.  All the Linux OS just use a link, so any new bookmark by one OS shows up for all the others.
I use Ubuntu 7.04.  Thanks to partimage I have a clone partition that is a very recent fully functional copy of my working OS.  In the clone I test new software to see if it's a keeper. 
I like this approach for several reasons.  I have a recent full system backup that can quickly be reinstalled if my hard drive dies.  I have a sand-box to test new software without polluting my working copy of Linux.  I can test most any Linux distro to see if it's worth keeping.  (I just put PCLinuxOS on last week.  I'll stay with Ubuntu.)  This fall I can easily put version 7.10 on the PC while keeping 7.04 around until I'm sure everything is running fine and nothing fell though the cracks. 

Partimage with SystemRescueCD is easy.  I assume the user knows how to use the command line to mkdir, mount, partimage, startx.   For clone installs also tune2fs and 'gedit /etc/fstab' and 'gedit /boot/grub/menu.lst'.  It's worth the effort to learn.

But crashes?  Most likely a little trouble shooting would solve it.  Give a little more detail about the crashes and maybe we'll find a simple file you can edit to get it going again without reinstalling.  SystemRescueCD boots from CD to let you work on your installed files, even corrupted ones.

---

### Post by ramjet_1953 on 2007-06-04
I do the ultimate backup.

I bought another HDD and installed it into one of those USB mini-boxes.

I use the Ghost for Linux (G4L) package to do a complete 1:1 backup of my system on a regular basis. It copies GRUB, as well so all I have to do is pop the HDD out of my laptop and put in the backup HDD.

A real no-brainer!

Regards,
Roger :cool:

---

### Post by Nighto on 2007-06-05
you can backup your instalation with dd:
```
dd if=... of=...
```
being *if* the input file and *of* the output file.

```
dd if=/dev/XdYN of=backup
```
being XdYN the root partition (sda1, hda1 etc.), or your entire drive by ommiting the partition number (only /dev/sda or /dev/hda, for instance).
And, for restoring, the oposite:
```
dd if=backup of=/dev/XdYN
```

---

### Post by ridgeland on 2007-06-05
I encountered too many problems with partimage for clones so now I use 
cp -a /dev/sdax /dev/sday.  
I do this when I am not using /dev/sdax as the root partition, that is I did not boot into the partition I want to copy. cp from the active partition could be very messy.  I format the target first so it's a blank partition.

I think that with cp a partition with 3GB used of 7GB will copy only 3GB, but with dd it would copy 7GB.  Right or Wrong?

We're off subject though.
What WiTechGuy really wanted was a way to remaster and create a live CD.
I suggest researching/google-ing 'remaster'.  I recently checked out a good book from the library "Live Linux CDs"  It might be in the book stores.  It's an excellent starter for remastering.  I did a few passes of it.  It's not too hard.  With the book's help I was able to add/delete programs and create the Live CD (install CD) more like I want it.

---

### Post by pixeldotz on 2007-06-09
a pet project of mine that i oh-so-love working on.

non of the tools are mine of course and i just like the sense of booting a backup i can restore.

using the backup.tgz.bz2 method i create a compressed backup file with everything i want included. the folders i exclude are ones that won't make a difference in the backup process.

make sure you have ISO master installed.
[HTML]http://littlesvr.ca/isomaster/downloads.php[/HTML]

download your favorite livecd distro that has extraction/compression support.

using isomaster, you can open the livecd iso, and ADD the backup file to it. then save as a new iso and burn that to cd/dvd.

boot your newly created livedisk and extract your backup file to the sda/hda of your choice then recreate the excluded folders before you reboot your box. you could create a small script to do this for you (i have not).
the not-so-easy part of this is recreating grub if you're restoring a backup to a new hdd.

this method works nicely for me. i could post you the exclusion list and the complete method i use if you'd like.

seems like a bit of overkill but i like a livecd with a backup file on it.

---

### Post by cchester on 2007-06-20
> **ridgeland said:**
> In Windows I used System Backup - Restore (ntbackup) a lot.  WindowsXP did not install it by default though!!!  I wanted that ease in Linux and finally found it.
I use partimage and a LiveCD from SystemRescueCD
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Each month I make a full copy of my preferred Linux OS (Ubuntu)
I keep several OS on my PC (one is WinXP) 7 others are Linux.
My Ubuntu partition is about 3.5GB so that would fit on a DVD.  I keep Data on a separate partition and use links.  For 7 Linux OS I only have one Firefox bookmarks file.  All the Linux OS just use a link, so any new bookmark by one OS shows up for all the others.
I use Ubuntu 7.04.  Thanks to partimage I have a clone partition that is a very recent fully functional copy of my working OS.  In the clone I test new software to see if it's a keeper. 
I like this approach for several reasons.  I have a recent full system backup that can quickly be reinstalled if my hard drive dies.  I have a sand-box to test new software without polluting my working copy of Linux.  I can test most any Linux distro to see if it's worth keeping.  (I just put PCLinuxOS on last week.  I'll stay with Ubuntu.)  This fall I can easily put version 7.10 on the PC while keeping 7.04 around until I'm sure everything is running fine and nothing fell though the cracks. 

Partimage with SystemRescueCD is easy.  I assume the user knows how to use the command line to mkdir, mount, partimage, startx.   For clone installs also tune2fs and 'gedit /etc/fstab' and 'gedit /boot/grub/menu.lst'.  It's worth the effort to learn.

But crashes?  Most likely a little trouble shooting would solve it.  Give a little more detail about the crashes and maybe we'll find a simple file you can edit to get it going again without reinstalling.  SystemRescueCD boots from CD to let you work on your installed files, even corrupted ones.

Hi,

Could you post a step by step on how to do this. It seems to be an answer I was looking for and could not get.

Also how do you setup linking? I tend to do what you said and try and keep other Linux OS on my computer and would like to do this and does it work if you are using Windows too?

Thanks

---

### Post by ridgeland on 2007-06-20
Steps I used for partimage backup:
1 - boot from the Live CD --- SysRescueCD
boots to root - prompt is % not $ or #
2 - % mkdir /mnt/ExtDrive (I use an external 250 GB hard drive but this is optional)
3 - % mount /dev/sdb1 /mnt/ExtDrive (or a second partition to write to, if no ExtDrive)
4 - % partimage
select source partition, target (i.e. /mnt/ExtDrive/Ubuntu.2007.06.20)
I use Compression = None, Autosplit = if no space left
This makes a full clone of the source partition.
Ten minutes to do the whole thing once you've done it a few time.
Result: a carbon copy clone of the source partition
Initially I had errors and was using compression, so I don't bother with compression, I have enough space.
Negatives: Source is fixed size (i.e. 8GB) target takes up only used space (i.e. 3.5GB) but to restore or clone to a new partition requires an 8GB target partition.  If new target partition size does not equal original partition size problems can occur.  Also UUID can become a real issue.  The clone copies everything, that includes the UUID, now two paritions have the same UUID, and grub and fstab are using UUID by default.  So when you boot where are you? old partition or new partition, some of both?
Now I've changed my approach.
Still I boot with SysRescueCD, then at the prompt:
% mkdir /mnt/ExtDrive
% mount /dev/sdb1 /mnt/ExtDrive
% mkdir /mnt/ExtDrive/sda7 (make a target directory)
% mkdir /mnt/a7 (a mount point for the source partition)
% mount /dev/sda7 /mnt/a7
% cp -a /mnt/a7/* /mnt/ExtDrive/sda7
/mnt/a7 is the source partition I want to copy
"cp -a" means copy archive (see $ man cp)
/mnt/ExtDrive/sda7 is the target directory
Now this can be copied to a new partition.  
The improvements over partimage:
Does not use UUID so no tangled mess with grub and fstab.
Partition sizes do not have to be the same, just large enough.

I've used cp -a to backup Windows before resizing partitions to make room for Linux on other's PCs.  Now I use a Dell-Ubuntu that does not have a Windows parition.  I still have my old PC with Windows if I ever need it.  Windows is only one partition with files.  It has no bearing on the above steps.

What do you mean by linking?

---

### Post by cchester on 2007-06-20
Thanks for the info.

As far as the Linking it was for another post where the user was saying how to backup and restore his system and he was saying that he has firefox linked so that all of his Linux Os's could all use the same bookmarks and when he added new ones it made it so the other ones got the new bookmarks too. 

It was him I wanted to get the instructions from as far as how to backup and restore my system and also the linking because it sounded cool.

Your instructions are good too but they seem complicated and hard but I will give it a go anyway because I need a solution.

Thanks Again Alot

---

### Post by ridgeland on 2007-06-21
It may have been one of my posts about linking.
Linking works great in Linux.  

I did not succeed in trying to link Windows->Firefox bookmarks to LInux->Firefox bookmarks.  But I don't use Windows and the internet at the same time so I didn't waste much time searching for a solution.  I unplug the DSL anytime I want to see something in Windows, due to virus, attacks and MS's phone-home programs.

The good stuff in LInux:
I created a partition called /UserHome
I mount it automatically in fstab with the line:
/dev/sda14      /UserHome       ext3    defaults        0 0
In /UserHome I have a directory /UserHome/Firefox.
Again this is for Linux to Linux linking:
From your working copy of Firefox copy the bookmarks.html file to /UserHome/Firefox/bookmarks.html
The working copy is in a hidden folder.
/home/your_id/.mozilla/firefox/some_string/bookmarks.html
Using Nautilus in  /UserHome/Firefox right click on bookmarks.html and choose 'Make Link'
A new file is created that is a link.
Copy the link and paste it back in /home/your_id/.mozilla/firefox/some_string
Now using Nautilus in /home/your_id/.mozilla/firefox/some_string change the name of the original bookmarks.html to bookmarks.html.beforelink 
change the newly pasted file name from "link to bookmarks.html" to bookmarks.html
Now when you launch firefox it will be using the bookmarks file in /UserHome/Firefox. To have a second Linux share this same bookmarks file just copy the link and paste it like above in the next Linux, or even in the same Linux for a different user ID, in a different /home/next_id/.mozilla...
It takes a longer to explain it than to do it.  Now any Linux+User combination that uses the link to bookmarks shares any adds or deletes etc.
I did something similar for Thunderbird but there the link level is at the "some_string" directory, a folder not a file.  And I changed the "some_string" to "myname_mail.default" and edited profile.ini to reflect the change.

---

### Post by cchester on 2007-06-21
Thanks again for the info. I will have to implement this for all my Linux OS that I use.

Would still like to maybe find a way to include windows too because when I have Linux running my wife complains that she doesn't have her Windows bookmarks to use. I am right now just exporting them and then importing them into Firefox in Linux so she can have them but I like the linking idea. Her other complaint was that if she made a bookmark that was in Firefox in Linux then when I switch to Windows for her she has to recreate it there too but to me it is no big deal when I have to do it but for her it seems to be a big deal. Then again she doesn't like having to do any extra steps when it comes to computers. Just point, click and you are there. Shes a little lazy I know.;)

I will be printing both sets of your instructions today.

Thanks again.

---

### Post by ridgeland on 2007-06-21
Amusing.

My wife also wants no more effort than a single click.
But she was very fast to abandon Windows when using the web.
Like me she unplugs her DSL line before booting into Windows.
She uses Windows more than I do, a few things like her Quilt programs are Windows only.

I think ntfs-3g is the best way to mount Windows partitions.
But a cool stable link like in Linux doesn't exist, as far as I know.

Since you can have both partitions open during Linux boot, you can write some scripts to copy bookmarks from Windows to Linux.  Or if Linux is the "official" bookmarks file, then a script on closing to copy the bookmarks to Windows.  Just run Firefox from a script and add a line before or after to copy the files.  (Ugh, It's a bad feeling to help someone use Windows for the internet.)
ED: I assume you use only Firefox in Windows.  IE will not have a nice bookmarks file.

When your Windows anti-virus subscription is due again try to tell her why there is no annual fee in Linux.

Anyway good luck.  If you don't get the Linux links to work, post back where you got stuck.

---

### Post by cchester on 2007-06-22
"Since you can have both partitions open during Linux boot, you can write some scripts to copy bookmarks from Windows to Linux. Or if Linux is the "official" bookmarks file, then a script on closing to copy the bookmarks to Windows. Just run Firefox from a script and add a line before or after to copy the files. (Ugh, It's a bad feeling to help someone use Windows for the internet.)
ED: I assume you use only Firefox in Windows. IE will not have a nice bookmarks file."

I don't know how to script yet would love to learn. Yep Firefox and Thunderbird. On IE when the site says it will only work with it. I do my best to stay in Ubuntu. Trying to ween off my wife from Windows but there is always that one program that she needs in it that she can't do with out and I have tried my best to run them in Wine and Crossover with no luck. It is weird to me that her stuff seems to be so simple of a program most 2D but yet I can't get them to run and that includes Cedega too but Cedega has been a lot more of a miss as of late for me than the other 2.

Going back to Firefox does your wife feel it is different in Linux than Windows in the way it looks? Mine does and  say she doesn't like the way the same page in Windows and Firefox doesn't display the same as in Firefox and Linux. I have yet to find a way to make them display the same even though they are the same program, same web page just a different OS. That would help on the converting too.

As far as Virus Programs go I use a free one so she doesn't care. I take as many precautions as I can in Windows to protect ourselves with all kinds of software and hardware.

Thanks again.

---

### Post by ridgeland on 2007-06-22
Visit
[http://tldp.org/guides.html](http://tldp.org/guides.html)
Download some pdfs like "Bash Guide for Beginners"

Here is a simple script I used in FedoraCore 4 to turn on NumLock before starting Firefox.

```
#!/bin/bash
#
#  Firefox with NumLockOn
#
numlockx on
firefox 
```

I gave the script a name ending in .sh, but in Ubuntu I don't use the .sh because it caused problems with cron jobs.  You can add the script with an icon (Firefox's) to the panel.

Pages don't look the same.  Probably true, probably due to fonts used.  Check/Compare Firefox settings in Content -> Fonts and Colors.  In Ubuntu use "msttcorefonts" to get the Microsoft TrueType core fonts.  Search in Symantics Package Manager.  If not there visit:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 

My view of Windows and MS may be a little negative.  But I paid for it on the old PC, my wife paid for it on her PC so I keep it on those PCs and use it when I need it.  Just never for the internet.  I tried some with Wine but decided it's easier to just dual boot.

---

### Post by cchester on 2007-06-22
Thanks again for the info I will give it a go.

I tried last night to do what you just were saying and checking out what settings were in Firefox for Windows and wrote them down then went into Linux and put in the same info. The thing is the fonts still didn't seem to display correctly. Don't really understand what is going on there.

Yeah I use it too because I paid for it. Heck I paid for Vista ended up hating all the issues with it and put XP back on even though I did like aero desktop. So my new Vista sits in the box since but I bought it so I will keep it.

I know that if I can get the look and feel in Ubuntu just right and the settings in Firefox so it looks right maybe then she will feel like everything looks and displays the same and my wife should be ok then. The games I will just have to work on.

Funny thing is for the last few days Windows XP has been shutting down out of the blue no reason, no error, nothing and today when it happened again to my wife I chuckled and she said what is so funny and I said I was in Linux all night and most of the morning until she wanted me to restart and the computer never shut down once. So I said and now you see why I love and use Linux. She gave me a dirty look.:p

Still curious though what is causing it. I haven't been able to find an answer yet.:(

---

