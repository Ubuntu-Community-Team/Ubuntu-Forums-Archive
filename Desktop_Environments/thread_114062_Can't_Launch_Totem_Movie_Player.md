---
title: "Can't Launch Totem Movie Player"
date: 2006-01-07
forum: Desktop Environments
---

### Post by dsierpin on 2006-01-07
Hey all-

Just installed Breezy 2.6.12 on my AMD64 hp.  I had to install the fglrx driver to get the video to work, and now when I launch Totem I get the following message:

Totem Movie Player

The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.

Here is the output of ps:

```

david@ubuntu:~$ ps r
  PID TTY      STAT   TIME COMMAND
 7922 pts/0    R+     0:00 ps r

```

Any ideas?

Thanks in advance.

---

### Post by nalmeth on 2006-01-07
2.6.12 is the kernel version I believe. 
Did you install the 64-bit version? Or the standard i386?

---

### Post by el toro on 2006-01-07
Perhaps fudging with the Multimedia Systems Selector (System > Prefs > MSS) will do it?

---

### Post by dsierpin on 2006-01-08
Thanks for the help guys.  I did install the AMD64 Breezy.

I messed with the Multimedia Systems Selector, and it got Totem to open.

I have an AVI file that I can't get it to play, but I'll work on it and report back.

Thanks again!

---

### Post by dsierpin on 2006-02-08
Okay, well I got it working by downloading whatever multimedia codecs I was missing with Automatix (thanks Arnieboy \\:D/ ).  But I had to get my modem working before I could download anything, which I did by installing hsfmodem.  But hsfmodem doesn't work with 64-bit yet, so I installed the 32-bit version of Ubuntu.  Hope this helps somebody.

---

### Post by Noremacam on 2006-02-11
[I've had this problem as well]("http://www.ubuntuforums.org/showthread.php?t=119963&highlight=totem"), but I run the 32 bit version of ubuntu. It tells me 
"The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector."

Nothing I've done can fix it.

---

### Post by dsierpin on 2006-02-13
Did you try the getting the multimedia codecs with Automatix?  Worked like a charm for me.

---

