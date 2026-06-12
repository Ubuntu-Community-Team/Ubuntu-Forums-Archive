---
title: "temporary unmounting system partition?"
date: 2009-02-07
forum: General Help
---

### Post by pioa on 2009-02-07
Hi!

I wanted to check my filesystem for integrity with e2fsck but it highly suggests me not to do that with a filesystem that is currently mounted.

Sure I could shutdown and run a live cd, but I am looking for a more comfortable way because I know linux can run completely in RAM (like live cd).

Is it possible to temporary unmount the system partition and to mount it later?

If so, how?

---

### Post by k3rnelmustard on 2009-02-07
By system partition do you mean /?  That's definitely not possible AFAIK.  Also, I'm not sure what you mean 'linux can run in RAM'.  Your whole root filesystem probably can't, unless you have 4GB of RAM or something.  Even if you did, you could probably only mount /usr in RAM.  I would just use a livecd/liveusb, one with an installation small enough that it CAN be run fully in RAM.

---

### Post by pioa on 2009-02-07
> **k3rnelmustard said:**
> By system partition do you mean /?
Yes.

> **k3rnelmustard said:**
> Also, I'm not sure what you mean 'linux can run in RAM'.
Just like a live cd does without modifying any harddisks without being asked to do so. But you are right, it's not only in RAM, also the CD...

---

### Post by taurus on 2009-02-07
Any reason why you don't want to fsck your root filesystem from the LiveCD?  It's probably the safest method.

---

### Post by pioa on 2009-02-07
> **taurus said:**
> Any reason why you don't want to fsck your root filesystem from the LiveCD?
- LiveCD needs a disc and a CD-ROM
- booting from CD takes long
- downtime not wanted
- Rebooting and LiveCD just to to check the filesystem? Other operating systems can do this while running (DOS to name a very old one and Windows to tell a very new one).

Hope this are enough reasons for justification.

---

### Post by Monotoko on 2009-02-07
You cant unmount C:/ and save it in RAM in windows :/

---

### Post by pioa on 2009-02-07
But you can start ScanDisk...

---

