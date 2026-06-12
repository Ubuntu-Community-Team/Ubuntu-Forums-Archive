---
title: "Problems changing monitors with Ubuntu 9.04"
date: 2009-06-04
forum: General Help
---

### Post by deserthowler on 2009-06-04
I work for WorldCare charity in Tucson, Arizona.

I set up a computer with Ubuntu 9.04 a few days ago and it worked fine.  Video, Wi-Fi, and sound all worked.  I used a KVM with a flat screen monitor because this set-up gives me more work bench room.

We put it in our store for sale.  Today it was demonstrated in the store using a different monitor.  I got it back and using another monitor found the video to be totally unacceptable.  I tried dpkg-reconfigure xserver-xorg from tty1 with no luck.  On earlier versions of Ubuntu this worked.  I rebooted and got a total mess with the video and could not switch to tty1.  The whole thing became totally unusable.

I've had problems with other versions of Ubuntu doing similar things when changing monitors.  I would like to be able to give away computers with Ubuntu but not if this is going to happen.  I am not in a position to support these machines.

Any ideas?

Earl

---

### Post by dhughes on 2009-06-04
Are there any bent pins on the monitor's connector? 

 Will it work with an Ubuntu LiveCD or is the video also fuzzy?

---

### Post by deserthowler on 2009-06-04
> **dhughes said:**
> Are there any bent pins on the monitor's connector? 
No, there aren't any bent pins.  The monitors that showed the problem were used on machines running Windows and worked fine.
 > **dhughes said:**
> Will it work with an Ubuntu LiveCD or is the video also fuzzy?
It wasn't fuzzy.  It was incomplete.  The Gnome Window manager didn't have title bars.  Sometimes, when  window was closed, fragments of it remained on screen.
Then, after reconfiguring xorg the screen was totally distorted and unreadable.
THOUGHT:  Did I disable ALL screen effects?  The computer has a very small video card.

Earl

---

