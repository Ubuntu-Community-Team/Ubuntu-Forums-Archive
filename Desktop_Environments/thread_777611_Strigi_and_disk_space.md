---
title: "Strigi and disk space"
date: 2008-05-01
forum: Desktop Environments
---

### Post by takowl on 2008-05-01
I noticed my home partition was running low on space, so I checked filelight and found that .strigi/clucene/ was taking up 90% of the disk space. A quick search turned up this: [http://ubuntuforums.org/showthread.php?t=725213](http://ubuntuforums.org/showthread.php?t=725213) but there are no apparent resolutions, or any suggestion of what's going on.

(32 bit) Kubuntu Hardy KDE4, clean install from the desktop CD.

Any ideas what's going on?

---

### Post by pape on 2008-05-02
I had the same problem (Kubuntu Hardy x86-64). One simple medicine is to remove strigi and the mess it caused:

sudo apt-get remove strigi-daemon strigi-applet

and

rm -rf .strigi     (given in home folder)

---

### Post by Zorael on 2008-05-03
Confirmed. Opinion, but while Strigi is hyped, it's a tremendous resource hog, so the first thing I do after installation is to purge it. :>

And KNotes. shoo shoo.

---

### Post by takowl on 2008-05-04
Pity--it shouldn't need to be such a resource hog. But yes, I've turned it off as well (slightly less drastic, I used kcmshell kcm_nepomuk to disable it).

---

### Post by takowl on 2008-05-07
I investigated a little, it seemed that strigidaemon was repeatedly re-indexing the same stuff. Launchpad doesn't seem to have anything on this, and a quick google didn't turn anything up. I've e-mailed Jos v.d. Oever to see if it's a known issue.

---

### Post by speeddad on 2008-06-05
I had the same problem.  After following pape's instructions (thanks), my 45 gig home partition went from about 96% full to 2.6% full.

I here are some of the problem files I found.

/home/user/.strigi/clucene/_1dpee.prx   was 1.0 GB
/home/user/.strigi/clucene/_1dpee.fdt   was 7.8 GB
/home/user/.strigi/clucene/_1dpee.tmp   was 8.7 GB
/home/user/.strigi/clucene/_p2hs.cfs    was 10.6 GB

There were 10 other files in /home/user/.strigi/clucene that were larger than 100 MB (8 over 900 MB).

---

### Post by Chessmaster on 2008-06-22
Hey, I had the same problem. I followed the fix above and removed Strigi. 

Does anyone know if this has been / or is going to be fixed? Couldn't find anything on launchpad (maybe I missed it). 

Cheers

---

### Post by takowl on 2008-06-27
Apparently, it has already been fixed in newer versions of Strigi (>= 0.5.9), but Ubuntu isn't going to package a newer version for Hardy. Jos van den Oever, the creator of Strigi, hasn't yet got round to backporting the relevant fix to 0.5.7.

The relevant bug report has, unfortunately, been marked as a duplicate of another that I don't think highlights quite the same problem. The better description can be found at:
[https://bugs.launchpad.net/ubuntu/+source/strigi/+bug/137751](https://bugs.launchpad.net/ubuntu/+source/strigi/+bug/137751)

I don't know how to un-duplicate-mark it, or even if it's worth doing so. It should be fixed for Intrepid, but it looks like there's little chance of the fix being backported to Hardy.

---

### Post by Guanine on 2008-06-28
Strigi is not that bad.I have been running it for a few months and my hard drive is still at 10%.

---

### Post by takowl on 2008-06-30
Are you running the default version in Hardy?

Evidently, something that not all users have sets the problem off. Presumably, if this issue had affected all users, the bug would long ago have been fixed...

---

### Post by venik212 on 2008-07-12
It is OK to manually remove (after purging strigi with Adept) all files in the /home/user/.strigi folder?

---

### Post by takowl on 2008-07-13
> **venik212 said:**
> It is OK to manually remove (after purging strigi with Adept) all files in the /home/user/.strigi folder?

I can't see that it could cause any harm to do so.

---

### Post by Craftycorner on 2008-11-29
I bookmarked the /clucene/ folder and emptied it, and will continue to do so treating it as a second trash bin.  That is one way of dealing with the clutter-a-muck.

---

### Post by takowl on 2008-11-30
Turning Strigi off should remove the need to empty its folder.

That said, the using-all-the-disk-space issue should be fixed in Intrepid. I haven't turned it on for long enough to find out.

---

### Post by chaddles on 2008-12-01
Still appears to be an issue on Intrepid, thanks for the tips on recovering the space though :-)

---

