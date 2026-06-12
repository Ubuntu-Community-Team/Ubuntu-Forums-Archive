---
title: "DVD Drive Does Not Mount On M1330"
date: 2009-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by robog2 on 2009-05-16
This is on a Dell m1330 running Ubuntu 9.04 (though I had a similar problem on 8.10).  

The dvd drive is not available in the places menu, but is visible in "Computer" in nautilus and has a mount location in "/media/" (both cdrom and cdrom0 are present).  When a cd is inserted, it does not mount, and the drive fails to recognize that one is present (though I hear it spin up).  I am positive that the drive itself works (and that the cds/dvds inserted work), but need help making it work in ubuntu.  

In 8.10, the drive would mount maybe one in ten times, but would not work correctly when it did; now it won't mount at all (after a clean install of 9.04).

I have thoroughly searched the forum, and have tried the solutions posted at [http://ubuntuforums.org/showthread.php?t=557405&highlight=m1330+dvd ]("http://ubuntuforums.org/showthread.php?t=557405&highlight=m1330+dvd")and the page to which it links to no avail.

Thanks,
Garrett

EDIT: This is on the x64 version of Jaunty, if it matters.

---

### Post by robog2 on 2009-05-16
Here are the results of ```
ls -l /dev | grep cdrom
``` in case someone asks:

```

lrwxrwxrwx  1 root   root           3 2009-05-16 17:56 cdrom -> sr0
crw-rw----+ 1 root   cdrom    21,   1 2009-05-16 17:56 sg1
brw-rw----+ 1 root   cdrom    11,   0 2009-05-16 17:56 sr0

```

---

### Post by robog2 on 2009-05-17
Bump... any ideas?  Should the thread be moved to Hardware and Laptops?

Thanks.

---

### Post by robog2 on 2009-05-17
I made a copy of this thread in Laptops and Hardware due to lack of replies.  I hope that is not a problem.

---

### Post by Declination on 2009-05-18
Hopefully you still check this thread. I find that the dvd drive on my m1330 is finicky if you don't put discs in perfectly. I frequently have to re-insert certain kinds of discs. Usually DVDs.

---

### Post by robog2 on 2009-05-18
It used to be that way for me until I updated to 9.04.  And even then it would not be able to write a cd successfully.  Thanks for the reply.

---

### Post by robog2 on 2009-05-18
Here's some more information; hopefully my problem will be more apparent with it:

When I try to mount (any) media manually:
```

sudo mount /media/cdrom0/ -o unhide
```
it returns:
```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

And when I do what it says:
```
dmesg | tail
```
I get this:
```
[  876.007501] sr: Sense Key : Hardware Error [current] 
[  876.007508] sr: Add. Sense: Tracking servo failure
[  876.013372] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 02 00 00 00 00 aa 00 0c 00
[  876.013395] sr: Sense Key : Hardware Error [current] 
[  876.013402] sr: Add. Sense: Tracking servo failure
[  876.013975] UDF-fs: No partition found (1)
[  876.053381] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[  876.053405] sr: Sense Key : Hardware Error [current] 
[  876.053413] sr: Add. Sense: Tracking servo failure
[  876.073386] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=32

```

Any help would be wonderful.  Thank you.

---

### Post by robog2 on 2009-05-19
Bump.

---

### Post by robog2 on 2009-05-20
Bump.

---

### Post by lhodapp on 2009-05-31
Hi.  Did you ever solve your problem?  I'm having the same issue I think.

---

### Post by robog2 on 2009-06-01
Indirectly.  A few days after my last post, my hard drive failed, which led me to call Dell Technical Support (the Education and Government number, as I am still covered by their 4-year Dell University Warranty, and they are amazing when it comes to support).  I told them that my optical drive never seemed to work, and now that my hard drive went and I could not boot, I had no way of reinstalling with a cd.  To check to see whether they were both bad, she had me completely dismantle the laptop by her instruction, so that I could unplug the optical drive and see if the laptop would then boot without it.  It did not, so she overnighted a new optical drive and hard drive to me (without any problems) and had me replace them.  I have since installed both and reinstalled 9.04 x64, and everything works perfectly.  

I think the new optical drive working has something to do with the brand; the one she sent was a different brand than the original, and works perfectly.  I don't remember what the old one looked like, but the new one has a yellow label (the old one may have had a white label, but I can't remember for sure).  Given that your hard drive is working, I would just tell them that the optical drive has never worked, will not recognize media, and will not burn media either, and they will probably replace it as they did mine.  If you did not order a Ubuntu-preinstalled m1330, you might want to tell them that Vista or XP is still installed, and go along with their troubleshooting, if you can (I didn't have to say anything about OS, as my laptop wouldn't boot at all).

Good luck; hopefully you will get this resolved as easily as I did!

---

