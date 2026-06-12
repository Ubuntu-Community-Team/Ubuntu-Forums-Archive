---
title: "[SOLVED] 32- or 64-bit Ubuntu"
date: 2007-09-24
forum: Dell  Ubuntu Support
---

### Post by CharlieFoxtrot on 2007-09-24
Just got my first linux machine. Ordered an XPS410 from Dell. So far so good as far as the hardware goes but communication with Dell, from ordring from their website on, is a hassle. I've tried to get an answer from them without success. 

My machine has a Core2 (64-bit) processor. I'm trying to determine whether Dell loaded the 32- or 64-bit Ubuntu. Can someone tell me how to determine which is installed on my machine?

---

### Post by neptho on 2007-09-24
Open a terminal, and type 'uname -m'.  The 64 bit version will say 'x86_64', 'i686', 'i386', etc, are all 32 bit.

---

### Post by CharlieFoxtrot on 2007-09-24
Thank you, neptho. It's 32-bit.

---

### Post by rsambuca on 2007-09-24
I'm pretty sure the dell rigs come with 32bit pre-installed.

Edit:  Ooops.  I type too slow.  I see you have your answer already!

---

### Post by neptho on 2007-09-24
You're welcome.  :)

My 6400 is a Core Duo (older model), which is 64 bit, but I've chosen to use the 32 bit version for several reasons:

i8k works.  Without this, there is currently no way to manually control your laptop's fans.
Flash 9 works.  No strange hacks required.
Binary-only releases of software designed for the 32 bit version of Linux, with their support libraries work.

I'd suggest , that unless you enjoy tinkering, just let it be.  :)

---

### Post by rsambuca on 2007-09-24
> **neptho said:**
> You're welcome.  :)

My 6400 is a Core Duo (older model), which is 64 bit, but I've chosen to use the 32 bit version for several reasons:

Actually, the Core Duo chips are 32bit processors.

---

### Post by neptho on 2007-09-24
Yep, you're right.  This one is the T2050 Yohan, I was thinking about the Sony which has a Core 2 Duo, rather than just a Duo.

---

### Post by rsambuca on 2007-09-24
> **neptho said:**
> Yep, you're right.  This one is the T2050 Yohan, I was thinking about the Sony which has a Core 2 Duo, rather than just a Duo.

Oh, and flash works very well on 64bit now.  Double click the script to install it.  No hacks required!  I don't know about that other stuff, though.

---

### Post by neptho on 2007-09-24
> **rsambuca said:**
> Oh, and flash works very well on 64bit now.  Double click the script to install it.  No hacks required!  I don't know about that other stuff, though.

There is no 64 bit usable i8k.  I looked at it, and my eyes crossed.  This is not a place I want to be meddling with code.  Good to know about Flash, though.

OP, please mark thread as solved.  :)

---

### Post by phenest on 2007-09-24
> **rsambuca said:**
> Oh, and flash works very well on 64bit now.  Double click the script to install it.  No hacks required!  I don't know about that other stuff, though.

I just downloaded Flash 9 and it says the x86_64 architecture is NOT supported.

---

### Post by rsambuca on 2007-09-24
> **phenest said:**
> I just downloaded Flash 9 and it says the x86_64 architecture is NOT supported.

There are two easy methods, both of which have scripts written for easy installation.  All you have to do is click on the script to run it.  The two options are

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

