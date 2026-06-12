---
title: "Moving windows in X causes process freezes"
date: 2006-11-02
forum: Desktop Environments
---

### Post by aaahoopy on 2006-11-02
Hi all,

I imagine this is a long standing issue, but I did not see anything in the quick google search I did, so I thought it might be prudent to discuss it.  

I am running a default install of edgy with the Xen 3.0.3 binaries and having installed a large number of things from automatix2.  I am running my desktop from dom0.

I noticed this morning while moving windows that beep media player would stop.  It is not something I recall experiencing before, so I experimented with it a bit.  

While moving a window continously for a long time:
beep media player will stop
mplayer xxx.mp3 from a konsole will freeze and then spit out a cacophony after releasing the window
mplayer xxx.mp3 played from an xterm living in a XVNC desktop does *NOT* stop
MPG123 xxx.mp3 played from a console will *NOT* freeze

So the key thing here appears to be that eventually X enabled child processes will freeze up waiting for the X server.  I swear I have heard something like this before, but I have certainly never experienced it this badly.  My new system a considerably nicer system than my old one, so I am guessing this is something to do with Xen.  I will reboot my system and rerun these tests and report the results.

John

---

### Post by aaahoopy on 2006-11-06
> **aaahoopy said:**
> Hi all,

I imagine this is a long standing issue, but I did not see anything in the quick google search I did, so I thought it might be prudent to discuss it.  

I am running a default install of edgy with the Xen 3.0.3 binaries and having installed a large number of things from automatix2.  I am running my desktop from dom0.

<SNIP>

It took a while, but I did finally have a chance to reboot, and I am guessing that the problem is due to the fact I am using the nv driver.  When I booted to the standard edgy kernel, I saw the music player stop within a second of starting to move the window.  I also tried moving around windows on my laptop which has an ATI Radeon Mobility that is well supported, and did not see the same issue.

So there is a yet another reason not to use the nv driver folks.

John

---

