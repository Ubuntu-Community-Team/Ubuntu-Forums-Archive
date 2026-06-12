---
title: "increase speed of  data transfers (copying or moving)."
date: 2009-06-20
forum: General Help
---

### Post by autocrat25 on 2009-06-20
I'm having a slight problem while copying data from ubuntu onto any flash or pen drives. The transfer rates are are quite reasonable at 6 to 8 mbps for pendrives but it takes ages for the transfer to complete. For example a 600mb data at 4mbps took around 4 mins :shock:!!! This is very annoying :mad: so please can anyone come up with a solution for this? :sad:

Thanks in advance.

---

### Post by thewolfman on 2009-06-20
Buy a faster PC!

---

### Post by HavocXphere on 2009-06-20
> **thewolfman said:**
> Buy a faster PC!
Umm. No. The limitation is not the PC itself.

> **autocrat25 said:**
> I'm having a slight problem while copying data from ubuntu onto any flash or pen drives. The transfer rates are are quite reasonable at 6 to 8 mbps for pendrives but it takes ages for the transfer to complete. For example a 600mb data at 4mbps took around 4 mins :shock:!!! This is very annoying :mad: so please can anyone come up with a solution for this? :sad:
600mb in 4 minutes is either 2.5mBps or 20mbps. (The first being bytes and the second being bits per second). Which is slow.

Pretty much all computers these days support USB 2 so that is unlikely to be the limiting factor. I know one can check this in ubuntu...but I can't remember how.

I'd say that the quality of the flash stick is the problem. e.g. I've got 2 memory sticks here, the one is more than twice as fast as the other. It depends on the type of memory used within the memory stick. Sometimes it is even a mix of fast & slow memory. Generally name brand flash sticks are faster.

---

### Post by schmolch on 2009-06-20
I have the same problem with anything connected to usb.
I get only about 1MB/s for my usb-sticks, usb-hdds and sdhc cards.

---

### Post by shane2peru on 2009-06-20
No this actually is a problem that many are experiencing.  It is quite annoying to say the least.  It seems to be noticed more with 64bit users.  Here are a few other threads to read up on:

[http://ubuntuforums.org/showthread.php?t=1150108&highlight=slow+usb+transfer](http://ubuntuforums.org/showthread.php?t=1150108&highlight=slow+usb+transfer)

[http://ubuntuforums.org/showthread.php?t=1061236&highlight=slow+usb+transfer](http://ubuntuforums.org/showthread.php?t=1061236&highlight=slow+usb+transfer)

I don't really have an answer.  There is also a bug report on it.  Quite annoying though.

Shane

**EDIT:**  Oh you can try Gnome Commander (it's in the repos) or just using command line and see if that works any faster for you.  It seems a little faster for me.  I avoid Nautilus like the plague for transfers to USB.

---

### Post by autocrat25 on 2009-06-21
Or is there any application like teracopy (for windows) that can help increase the transfer rates?

---

### Post by hibliss on 2009-06-21
> **shane2peru said:**
> No this actually is a problem that many are experiencing.  It is quite annoying to say the least.  It seems to be noticed more with 64bit users.

Agreed. I have two Ubuntu machines, transfer rates are considerably better on my 32 bit install then the 64 bit. This bug carried from 8.10 to 9.04.

I have one of the best Sandisk Cruzers on the market, Titanium with high transfer speeds, but on my 64 bit install they often drop to under 1mBps.

I also have no solution, but have searched in the past and only found out it was a known bug with no solution.

---

