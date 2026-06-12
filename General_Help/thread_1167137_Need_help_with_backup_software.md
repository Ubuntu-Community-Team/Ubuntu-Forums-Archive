---
title: "Need help with backup software"
date: 2009-05-22
forum: General Help
---

### Post by mercules2178 on 2009-05-22
I am working on becoming free of windows. As I find software to replace the ones I am currently using I am uninstalling them. I use Acronis to manage my disks and backups. Is there a comparable program for ubuntu? Other than my games I am almost done with win!?&*

thx

---

### Post by magump on 2009-05-22
I made a post on March 14, 2009 regarding backup that I use.  I have used Ghost, tried Acronis but it wouldn't recognize my Linux drive to do a restore.  Backup was ok.  I now use Partimage from a live cd.  If you download a copy of Parted Magic at [http://sourceforge.net/project/showf...roup_id=248002](http://sourceforge.net/project/showf...roup_id=248002) (the current version is 4.1) you will be able to make an image of your drive(s) and back them up to a usb hard drive, as I do.  I do a lot of experimenting and sometimes have to revert to a previous installation.  I also use, once in a while, Image for Windows which also has Image for Linux if you use windows once in a while.  Parted magic is free, Image for Windows is around $40.00.  (I have no affiliation with Image for Windows).  You can restore your complete system in about 6 to 10 minutes.

Magump

---

### Post by mercules2178 on 2009-05-22
I see that this is for the i386 architecture, does this make a difference when I have a 64 bit machine?

---

### Post by magump on 2009-05-23
As far as I understand, Parted Magic should work on a 64 bit machine, as a 64 bit machine can also run 32 bit programs but I'm not sure.  If I were you I would try Parted Image and make a backup of your system.  After backing it up, you can also simulate a restore to verify your backup.  If it successfully verifys your backup, you should be ok.  Another solution would be to download a copy of SystemRescue.  It is 64 bit compliant.  64 architecture info can be found at:
[http://www.sysresccd.org/Sysresccd-manual-en_Booting_the_CD-ROM#standard-kernels:_.28rescuecd_and_rescue64.29](http://www.sysresccd.org/Sysresccd-manual-en_Booting_the_CD-ROM#standard-kernels:_.28rescuecd_and_rescue64.29)

It can be downloaded at:[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

The reason I prefer Parted Image is because it has a file browser included so I can copy and paste the path/image name into Partimage.  Otherwise you have to rely on memory or written records to remember the path.

Hope this helps.  Perhaps someone out there can add to this info.

---

### Post by magump on 2009-05-23
I found this posted in the Parted Magic forum:

Re: 64-bit Version

Postby Patrick Verner » Mon May 11, 2009 12:15 pm
What could a 64 bit kernel possibly have to do with it? That doesn't even make sense. Any decent 64 bit processor should run just fine on 32 bit OS. I currently have a i7 920.

What do you mean by bugs in 4.0?

The post can be found at Partedmagic forums here:  [http://partedmagic.com/forum.html](http://partedmagic.com/forum.html)

magump

---

