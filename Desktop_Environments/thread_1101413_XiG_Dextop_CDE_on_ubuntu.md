---
title: "XiG Dextop CDE on ubuntu?"
date: 2009-03-20
forum: Desktop Environments
---

### Post by bukhara on 2009-03-20
Hello everyone,

I found a package named 'XiG Dextop CDE Motif' on a torrent site. I suppose it contains the port of CDE for the Linux environment. Has anybody tried to install it on ubuntu? I read somewhere that it had been built for an early version of Red Hat, do you think it would work on ubuntu as well?

---

### Post by bukhara on 2009-03-21
Well...nobody?

---

### Post by zizban on 2009-04-30
Late to the party, but I actually have this on CD. I'll dig it out and give it go if you wish.

---

### Post by zizban on 2009-04-30
I'm giving it a go but oh my the pain (so far).

---

### Post by zizban on 2009-04-30
I think I know what is going on and if I'm right (and I'll know when I go back to work tomorrow) then this wont work on Ubuntu or any other modern Linux distribution. We'll see tomorrow.

---

### Post by zizban on 2009-05-01
This wont work on Ubuntu for many reasons.

First, it's dependent on Xfree86 and Ubunbtu (and nearly everyone else) uses Xorg.

You could do a plain Debian install and install Xfree86 yourself but that will make installing anything else non-trivial as Debian will be looking for Xorg.

However, DeXtop does run but it's buggy and crash prone.

So unless you really, really and I mean REALLY want it, I'd give up the idea. Too much suckage.

---

### Post by unrandomsam on 2010-08-25
I know this is ancient but someone might find it.

You can build the included sources for X11R6.4 (X Consortium) and put them in /usr/X11R6 and it won't interfere with the Xorg stuff in /usr.

(It builds 100% with intel's compiler icc you just have to change gcc to icc in the main Makefile)

It works really well with XiG's xserver on an LFS system.

---

### Post by zizban on 2010-09-13
I'm surprised you got it working. If you ever read this, can you post how you did it?

---

### Post by mghis on 2010-10-27
I'm also interested to get it working... Can anyone help me?

---

### Post by zizban on 2010-10-30
I'm trying to track down my old XiG CD. It's around here, somewhere.

---

### Post by mghis on 2010-12-18
> **zizban said:**
> I'm trying to track down my old XiG CD. It's around here, somewhere.

Did you found the XiG CD? I'm really interested to get it working!

---

### Post by zizban on 2011-03-14
I found my CD!

---

### Post by mghis on 2011-03-18
Does it work with the included X server?
Can you get it to install properly?

---

### Post by zizban on 2011-03-20
No to both. It makes empty directories.

---

