---
title: "DVDshrink/DVD Decrypter"
date: 2005-11-01
forum: Desktop Environments
---

### Post by BLTicklemonster on 2005-11-01
I get these errors when running:

[img]http://www.hawkwinds.com/tickle/dvdshrink.jpg[/img]



[img]http://www.hawkwinds.com/tickle/dvdcrypter.jpg[/img]

I installed them with wine. I set dvd decrypter to run as a windows app, and I try to get it to autodetect. 

I also went to alt+f2, typed winecfg, and added both as windows apps, and had each one autodetect drives, and they each picked up the dvd rom and the dvd rw.

What am I doing wrong here? Are there lib files I need to be aware of? I know that the site (boss?) that shows how to install them is for hoary, but I would imagine that they'd work in Breezy, no?

---

### Post by BLTicklemonster on 2005-11-01
Bah. I installed the new wine, and it's working now. Sheesh. Well, if anyone else has these problems, you now don't have to spend twice as much time getting screenshots and uploading them and posting your problem. Just read this. :rolleyes:



*edit:

whoa, cool, it works like it did in windows.

---

### Post by pompeyjohn on 2005-11-11
i there, 

I seem to be having the same problem that the optical drive is found by the wine autodetect, but it does not show in applications.

What version of wine were you, and are you now running?

I am running 0.9.1 which I believe is the latest version.

Thanks in advance,

---

### Post by pompeyjohn on 2005-11-12
anyone? :D

---

### Post by pompeyjohn on 2005-11-13
ok, got a little bit further. I was clicking around in the winecfg app (ALT F2 - winecfg) and did the following.

Highlight the letter for the cd drive (in my case it is D) and then click on show advanced below. Underneath path you should see drive type. Mine was set to local hard disk. Change this to CD-ROM, save and exit.

Now I get the drive found in DVD Shrink :D  But...... still not in DVD Decrypter :???:

---

### Post by Kokanee on 2005-11-13
Why not use xDVDshrink as a native Linux solution?  I've benn using it and it works great.  You can get an RPM package from [their website]("http://dvdshrink.sourceforge.net/") which can be converted to a DEB easily with ALIEN.

---

### Post by MetalMusicAddict on 2005-11-13
I would have WINE (winecfg) autoconfigure you drives for you then edit ones the way you want them. Make sure you have your "Windows version" set NT4.0.

There is a .deb [HERE]("http://www.force-majeure.info/breezy/dvdshrink_2.6.1-4_ubuntu_unofficial.deb") for xDVDShrink.

---

### Post by kittcankitt on 2005-11-13
For some reason, xDvdshrink constantly gives me errors.  As nice as it would be to work without wine, the only thing that really seems to work (and in a reasonable amount of time) is using the dvdbackup method and then using dvdshrink in wine.  

By the way, same problem here about detecting my ext. dvd-rw.  Actually it did work one day and nothing has changed on my computer and now it doesn't work detecting any of the drives.  I haven't really needed to figure it out yet because the above method is working.  If some "wine" expert out there could shed some light on the situation about the drives it would be nice to have it run properly.

---

### Post by qalimas on 2005-11-22
Does xDVDShrink bypass ALL encryption like the DVDShrink/DVDDecrypter combo on Windows?

---

### Post by BLTicklemonster on 2005-12-06
[QUOTE=MetalMusicAddict]I would have WINE (winecfg) autoconfigure you drives for you then edit ones the way you want them. Make sure you have your "Windows version" set NT4.0.

There is a .deb [HERE]("http://www.force-majeure.info/breezy/dvdshrink_2.6.1-4_ubuntu_unofficial.deb") for xDVDShrink.[/QUOTE]
Refresh my memory, about how does one go un"deb"ing a deb file?

---

### Post by BLTicklemonster on 2006-09-09
BAM. And it died, just like that. No answer. Well, fortunately dapper lets you open debs and install them with a package installer. ;)

---

### Post by bones78 on 2006-09-10
I got dvd decrypter to see my dvdrw, but get this error when starting dvd decrypter:
I 21:54:23 Searching for SCSI / ATAPI devices...
E 21:54:23 DeviceIoControl(IOCTL_STORAGE_QUERY_PROPERTY) Failed! - Device: '\\.\F:'
E 21:54:23 Reason: Invalid parameter
I 21:54:23 Found 1 DVD±RW!

Wine is set to nt4 for decrypter.  Latest wine installed.  Any help to get decrypter to work would be great.  
P.S.  Decrypter is the only one I know of to bypass arccos on sony discs.

Cheers

---

### Post by BLTicklemonster on 2006-09-10
I gave up. When you install Ubuntu on a machine with a dvdrom and a dvdrw, then install some dvd writing software, you still have to do stuff to make the dvdrom and dvdrw usable. Not in that other operating system. I have a fresh install (did ubuntu and windows the same day) of that other ... oops, I said it's name didn't I? oh well, I took the fresh install of windows, installed nero on it, and dvdshrink, and it works like a charm. 

Why can't ubuntu do this?

---

