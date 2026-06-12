---
title: "Suspend happening on idle despite being disabled"
date: 2015-05-20
forum: Desktop Environments
---

### Post by pgratz on 2015-05-20
I recently upgraded to Kubuntu 15.04 and I find that now when the machine is idle for some time (not sure how long, somewhere between 15 mins to an hour) the machine goes into suspend mode.  This is despite having my energy saving configurator deselecting suspend session (see attached image):

[ATTACH=CONFIG]262100[/ATTACH]

A couple notes which might be important, this is a laptop which is permanently attached to a monitor via HDMI and with the lid closed and the LVDS screen disabled. I'm using it with an external keyboard and mouse.

How can I disable this behavior, I really want this machine to work like a desktop and stay on indefinitely. 
Thanks!
Paul

---

### Post by pgratz on 2015-05-20
Also of note (forgot to mention)  The laptop is always plugged in.
Paul

---

### Post by user1397 on 2015-05-22
I had this same problem and found out the solution is way easier than I would've thought.  Thing is, the screen lock is not in the power options (weird right), to get to it either open your application launcher and type screen lock, OR go to system settings > desktop behavior > screen locking and you'll see the settings there.  cheers!

---

### Post by pgratz on 2015-05-22
Thanks for your reply.  I just checked in there and I already have screen lock after: set to never.  I did have lock screen on resume set so I unset that.  I'll see if that makes a difference and post after...

---

### Post by user1397 on 2015-05-22
> **pgratz said:**
> Thanks for your reply.  I just checked in there and I already have screen lock after: set to never.  I did have lock screen on resume set so I unset that.  I'll see if that makes a difference and post after...
hmm the lock screen on resume won't have anything to do with that, it is definitely about the first item (screen lock after... being disabled).  Maybe it has something to do with your monitor setups.  Have you tried to reproduce the problem when you're not plugged into the external monitors?  That would be a good test

---

### Post by pgratz on 2015-05-25
That's a good idea, I'll try disconnecting the external monitor when I leave from work today and see if it still goes to sleep (screen lock didn't do it).
Thanks!
Paul

---

