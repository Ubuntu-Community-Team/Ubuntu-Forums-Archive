---
title: "Live USB problems."
date: 2009-06-02
forum: General Help
---

### Post by HBBFrum on 2009-06-02
I recently created a fully native install of Ubuntu on a 16 GB sandisc USB drive.  I was able to update it, install both Java, and Flash, and it worked the next time I booted from it.  Then I booted from it again and it just deleted all the things I had done, it's a clean install again without my ever tampering with it.

Thankyou ahead of time.

Post Script:  I am not a pro on using live USB's obviously, what I initially did was to set the system to use all access space as the place to store settings, programs, etc.  It still says that 5% of the access space is used, which would coincide with the amount of data I added to the system.

---

### Post by MichaelSammels on 2009-06-02
Did you install Ubuntu to the USB stick, or are you simply running the Live Version? (Hint, if it is the Live Version, "Live Session User" will appear at the top right).

If it was a live session, nothing is saved when you logoff.

---

### Post by HBBFrum on 2009-06-02
> **MichaelSammels said:**
> Did you install Ubuntu to the USB stick, or are you simply running the Live Version? (Hint, if it is the Live Version, "Live Session User" will appear at the top right).

If it was a live session, nothing is saved when you logoff.

Originally, that is what would happen, it would not auto-login, and that is the way I had it set, just to let me log right in, now it just automatically boots into Live Session User, and before I redo the USB I want to fix all of it.

---

### Post by MichaelSammels on 2009-06-02
You will need to install to the USB Drive then. When you have logged in as Live Session User double click the Install icon and follows the on screen instructions.

---

### Post by HBBFrum on 2009-06-02
Hmm, I had just used the USB startup creator, I guess that does not do the same thing.

---

### Post by MichaelSammels on 2009-06-02
No, that's much like the LiveCD - it is normally used for System Recovery. :)

---

### Post by HBBFrum on 2009-06-02
I guess I will need to boot from a live CD first then install it to the USB.  I will try this later on today and come back.

---

### Post by MichaelSammels on 2009-06-02
Yup, let us know if you run into any more problems. Good luck :)

---

### Post by HBBFrum on 2009-06-02
Yes, thank you.

---

### Post by HBBFrum on 2009-06-02
I seem to be doing it, waiting for it to fully Install as we speak.

---

### Post by HBBFrum on 2009-06-02
So, I installed it, to the USB drive of course, now the computer boots up with "Grub: Error 21"  which heavily surprised me.

I guess I need to remove grub and fix the windows boot loader.

Or while installing it, was I supposed to select the USB device as the boot loader installation place instead of "HD0?'

EDIT:  I am going to try a command I found on the forums.

EDIT:  Nevermind, can't get internet.  Trying SuperGrubDisc

EDIT:  I love SuperGrubDisc.

Trying again, this time, I will change the location of the boot loader.

---

### Post by HBBFrum on 2009-06-02
It worked, but it seems dead slow compared even to a normal live USB or live CD.  How does that make sense?

---

