---
title: "Full system freeze when changing nvidia-settings"
date: 2008-07-20
forum: Desktop Environments
---

### Post by endersbean3k1 on 2008-07-20
I was trying to trade my secondary monitor for a TV a couple hours ago when I encountered and issue upon finalizing the settings. The problem is almost identical to the one here: [http://ubuntuforums.org/showthread.php?t=741249](http://ubuntuforums.org/showthread.php?t=741249) the main difference being, I'm running Gutsy.

I was extremely disheartened to break my perfect linux record. Now, in one evening, I have gone from 0 to 3 freezes under linux. 


Alright, so here it is as I describe:

I'm running Gutsy, kernel 2.6.22-14 (had a different X-server issue with upgrading to 15, found some info, didn't care enough to change over). I have an nVidia 6800 on which I have been using a dual monitor setup for an extended period of time.

I opened nvidia-settings, disabled the secondary monitor (twinview), and enabled the TV. When I hit apply, it works quite nicely, giving me 15 or so seconds to accept the changes. I moved my mouse around a bit on the TV to make sure it was working, everything seemed fine. Here's the issue: the first time I think I canceled the changes, although I may have just let the timer run out, or hit the X to close the countdown, and this did not create a problem, and I went back to my original settings. 

However, when I tried to apply the settings a second time, my system completely froze up. I could do nothing. Tried an X-server restart... nothing. I had to hard boot (that's the term, right?) and tried again, but this time hit cancel (dunno what compelled me). Same result. This time before trying again I searched the problem, and found the above link. The hack worked for me as well. When the 'accept settings' dialog came up I killed nvidia-settings via the gnome system monitor, and the settings stayed, and I was able to use the TV.

Then, I went to change the settings back. I got some other sort of conflict, which I received while experimenting with the setup to switch between my monitor and TV as a secondary display. I wasn't worried, I'm not terribly familiar with the nvidia-settings nuances, and figured I had a setting slightly off. It made sense that I would see the same errors if I didn't remember the process right when I repeated it, only switching which screen was active. This time when it asked me if I wanted to auto correct the inconsistency, I went to X out the window, but the entire system froze when I clicked.

It seems to me that whenever I attempt to return to previous settings when the system is displaying anything not written specifically in xorg.conf, I freeze. I have no idea if this assessment is accurate, but it's the only thing that I can come up with, considering that I definitely got the same error that froze me last before I had changed the screens at all. 

Any ideas? Thanks in advance guys.

---

