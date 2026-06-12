---
title: "Crashing?"
date: 2006-01-14
forum: General Help
---

### Post by e2k on 2006-01-14
Hi!
I've had a slight problem with crashing lately.. Occasionally when I leave my computer on for the day, I get a big surprise when come home; ubuntu has crashed.  The usual scenario is this: I see a frozen screensaver image, everything is locked (can't even set numlock on/off, definitely a complete crash). The only way to get out of it is to do a hard power off (with the button) and restart the machine. I've never seen any problems like this on my past distros, what could it be? Please tell me what configs you want to see, since I have little experience on what to look at while solving problems like this.. :)

---

### Post by 23meg on 2006-01-14
It might be screensaver related; have you tried using a blank screen or display power management instead of screensavers? 

Also check your logs (Applications / System Tools / System Log) for errors reported while you're away.

---

### Post by BathroomNinja on 2006-01-14
check out your logs: 
/var/log/Xorg.0.log           <--- current log
/var/log/Xorg.0.log.old      <--- log from last boot

Also, run the memory test at boot.  You should see it as an option below the normal kernel.  Let it do a few passes on your memory.   If all of this still comes up with nothing, try booting to the Ubuntu Live CD and let it sit for a day or so (however long it normally takes to freeze on you).  That will help narrow down the problem to hardware or software.


Stealth Edit - 23Meg is fast.  His suggestion is a much better place to check your logs (looks pretty).

---

### Post by e2k on 2006-01-14
Thanks for your fast replies, I'll leave it on without xscreensaver for now and see what happens.. :)

---

### Post by 23meg on 2006-01-14
Also check if you're getting crashes in other 3d apps if the problem seems specific to 3d screensavers.

---

### Post by aysiu on 2006-01-14
Something else you can try is creating a new user on your system and using that for a day or two. If the new user isn't experiencing these crashes/lock-ups, something may be wrong with your current user profile.

---

### Post by e2k on 2006-01-16
It seems as if the problem laid in xscreensaver.. Disabled it, and haven't seen a single crash in 2 days. Might have something to do with 3d screensavers and ati? Don't know, but thanks for your suggestions, which solved this problem :)

---

