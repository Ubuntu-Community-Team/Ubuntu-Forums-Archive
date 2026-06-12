---
title: "Mouse stops working"
date: 2009-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by barbtobias on 2009-11-12
I am running the new release of Ubuntu 9.10 on a Dell laptop.  I find that, after the system has been running for a short while (10 minutes to an hour), the mouse stops working.  I have both a Logitech wireless mouse connected by USB and the touchpad.  When they stop, neither will work although I can still use the keyboard and shortcut keys.  This happens whether I am in Firefox, Open Office, Evolution, or directly on the Ubuntu system.
I can shut the system down with Ctrl/Alt/Delete and choose shut down, let it rest a while, bring it back up, and the mouse (both) works again temporarily.

Any idea whether this is probably a hardware thing or software?  

Thanks much!

           Barbara Tobias

---

### Post by lidex on 2009-11-12
The thread is marked solved. Was that an accident?

---

### Post by barbtobias on 2009-11-12
It was marked solved when I opened it, but it did not seem to be so.  Unfortunately, I'm not sure how to mark it "unsolved."

           Barbara

---

### Post by lidex on 2009-11-13
> **barbtobias said:**
> It was marked solved when I opened it, but it did not seem to be so.  Unfortunately, I'm not sure how to mark it "unsolved."

           Barbara
The drop-down "thread tools" menu above first post is for marking solved. Never tried the reverse though. Could be a usb issue. Closest thing I found is [here]("http://www.uluga.ubuntuforums.org/showthread.php?p=8267830"). Most others I saw involved keyboard also. Can you post output of 
```
lsusb
```

---

### Post by NNing on 2010-02-11
Greetings,

I see this thread hasn't really gone anywhere since November. (I will try to mark it as unsolved after I post this - see if that helps).

That's a pity, cos I'm having the exact problem described by Barbara re mouse freezing randomly (but not always) in Ubuntu 9.10 - keyboard remains ok.

So far I have seen these suggestions online:

(a) update the Bios 
[http://www.intel.com/support/motherboards/desktop/sb/CS-022312.htm](http://www.intel.com/support/motherboards/desktop/sb/CS-022312.htm)
[http://www.uluga.ubuntuforums.org/showthread.php?p=8267830](http://www.uluga.ubuntuforums.org/showthread.php?p=8267830)

(b) add code to boot options (2007 advice) 
[http://ubuntuforums.org/showpost.php?p=3003669&postcount=32](http://ubuntuforums.org/showpost.php?p=3003669&postcount=32)

(c) try a command
[http://ubuntuforums.org/showthread.php?t=1308931&highlight=mouse+freeze](http://ubuntuforums.org/showthread.php?t=1308931&highlight=mouse+freeze)

(d) wait for 9.10 to release fix (seems a few people have UNSOLVED posts for this) - or - put an earlier version on.

(e) remove an update released by Firefox recently. (This was also suggested, but I think it freezes even if I don't use Firefox.) ...However, the mouse freeze thing IS RELATIVELY NEW. It didn't use to do it, but because I only put Ubuntu on a few weeks ago, it's hard to say, as I hadn't used it that much before the problem started.

Anyway, thought I'd send this back out to see if anyone has tried any of the above - save me some pain. 

If one of these works for me, will post.

NiNo.

---

### Post by lidex on 2010-02-11
I'd suggest you start a new thread or cabbage on to an ongoing one such as this:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1309015&page=15]("http://ohioloco.ubuntuforums.org/showthread.php?t=1309015&page=15")
I'm probably the only one subscribed to this one (and not for long) and OP is MIA :rolleyes:

---

### Post by NNing on 2010-02-11
Thanks for that.

I found another thread (not marked solved) so I've added to that. Unfortunately, no one else seems to have though.

[http://swiss.ubuntuforums.org/showthread.php?t=1367828](http://swiss.ubuntuforums.org/showthread.php?t=1367828)

The thread you suggested mentions all kinds of freezing and rolling back to a previous kernel. I am a TOTAL newby at all this so that will be fun!! (steep learning curve, this Ubuntu business.) If you have any pointers on this (changing kernel), feel free to drop them down, but no worries if you don't have the time/enthusiasm. I'll bug a friend about it instead....

Interestingly, NVIDIA graphics and Intel were mentioned re incompatibility with new drives. That's the hardware I have too.

cheers,
NiNo.

---

