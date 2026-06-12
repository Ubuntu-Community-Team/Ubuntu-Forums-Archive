---
title: "Fun with DVDs, a bit of a strange problem"
date: 2008-03-14
forum: Desktop Environments
---

### Post by madchaz on 2008-03-14
System
Kernel: Linux goku 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
All updates installed. 

Problem: I am trying to watch CD2 of a boxset (Mash season 2 Collector edition)
DVD 1 works fine. However, when I insert DVD2 in the drive, it spins and does nothing else. It doesn't spin fast and I can hear the head trying to read, but it never does anything else, until I eject it. It will sit there and try to read the DVD, never managing to do so. I can never even get it to open in anything else, much less read. No errors that I could find. It just hangs there. 

DVD 1 works 100% fine. Put it in and play it with Ogle. 

Anyone as an idea? They work fine on my PS2, but my tv isn't as nice as my computer monitor.

---

### Post by suibhne on 2008-03-14
very strange:

what's it like in vlc?

are you able to copy it?

---

### Post by madchaz on 2008-03-15
Can't open it in VLC. It just tries to read and fails only when I eject the dvd. 

I also cannot copy it. 

What I don't get is the first DVD works fine, but not the second or third. If it was a copy protection, I'd expect it to be on all 3 ...

Those are originals, btw, if anyone was wondering

---

### Post by suibhne on 2008-03-15
Is it even being mounted? can you see a dvd icon on your machine?

(if not, it is possible to force mount a drive)

---

### Post by Lantesh on 2008-03-16
Ok this may be a dumb question, but do you have the library file libdvdcss2 installed?  If not get it from Medibuntu.  Assuming you have that installed I have no idea why disk 1 would play and not disk 2.  That is just odd.

---

### Post by madchaz on 2008-03-16
libdvdcss2 is installed

The drive does not mount, that's the problem. It just spins, tries to read it and never does mount it. Trying to mount it in the console ends up with the mount command waiting indefinitely.

---

### Post by RedSquirrel on 2008-03-16
Maybe you could try mplayer. When you run it on the command line, it might give you some error messages.

There's no need to mount anything, by the way.

```
mplayer dvd://1
```It is possible to make the messages more verbose if you don't see anything useful with the default message level.

```
mplayer dvd://1 -msglevel all=6
```Check the mplayer manpage and documentation on the website.

[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

---

