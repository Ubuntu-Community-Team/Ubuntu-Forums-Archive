---
title: "Can't play audio cd's"
date: 2005-11-17
forum: Desktop Environments
---

### Post by chris_andrew on 2005-11-17
Hi,

I've been using linux for about 6 years now, but believe it or not, cannot get an audio cd to play with Breezy.  Am I doing something wrong?  My cd is on /dev/hdd, but when I mount it, it doesn't see the disk.

Any thoughts?

Many thanks,

Chris.

---

### Post by bonzodog on 2005-11-17
Is the CD auto-mounting?

---

### Post by chris_andrew on 2005-11-17
LOL, nice one.  Not sure if auto-mounted.  I'm used to Debian, does buntu do that?

---

### Post by bionnaki on 2005-11-17
maybe you have the same problem that I have: [http://www.ubuntuforums.org/showthread.php?t=79363](http://www.ubuntuforums.org/showthread.php?t=79363)

---

### Post by chris_andrew on 2005-11-18
Thanks, but not the same problem.  I don't see the disk at the shell, or in any app.

Thanks,

Chris.

---

### Post by dcstar on 2005-11-19
[QUOTE=chris_andrew]Hi,

I've been using linux for about 6 years now, but believe it or not, cannot get an audio cd to play with Breezy.  Am I doing something wrong?  My cd is on /dev/hdd, but when I mount it, it doesn't see the disk.

Any thoughts?

Many thanks,

Chris.[/QUOTE]
I had the same problem after I enabled DMA mode for my CD drive (thinking that it would improve performance).

Once I went back into /etc/hdparm.conf and turned it back off, it worked ok again!....

---

### Post by chris_andrew on 2005-11-26
dcstar,

Thanks for the advice.  Unfortunately, I checked my hdparm file and everything is #'d out, so I don't think this is the answer.

Thanks,

Chris.

---

### Post by RAV TUX on 2005-11-26
look into this thread....it worked for me!

[http://ubuntuforums.org/showthread.php?t=79959:p](http://ubuntuforums.org/showthread.php?t=79959:p)

---

### Post by stalefries on 2005-11-26
Try checking /dev/cdrom0.

---

### Post by chris_andrew on 2005-11-28
Hi,

I'll check my /dev/cdrom0 (think i've done this already, though).  I'd rather not follow the thread that was mentioned, as it seems like a lot of reconfiguring, when all of my sound is working fine apart from being able to play CD's.  

BTW, I have been able to play CD's on this hardware for a good few years, with other distros, including Debian.

Any thoughts appreciated.

Thanks,

Chris.

---

