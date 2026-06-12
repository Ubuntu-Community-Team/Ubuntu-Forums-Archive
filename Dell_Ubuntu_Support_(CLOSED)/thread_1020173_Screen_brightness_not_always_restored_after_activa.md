---
title: "Screen brightness not always restored after activating display on Dell Mini"
date: 2008-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hackel on 2008-12-23
On my Dell Mini 9, running Ubuntu 8.10-lpia, after g-p-m turns off my display due to being idle, when I come back often the brightness of the display will not get restored.  The screen appears very dark, possibly at the lowest setting, although Ubuntu *thinks* it is correct.  If I hit the brightness up or down keys, it will be restored immediately, and the level displayed is near the right where it should be, not at the left where you would expect if the brightness really was all the way down.

This behaviour is inconsistent.  Sometimes it works fine.

Another, possibly related issue, is that when I change the brightness up or down with the keyboard, it will very briefly flash to full brightness before going back to where it should be.  If I use the slider in g-p-m the brightness changes smoothly without this flashing.

---

### Post by Mig Daddy on 2009-01-07
I have a similar problem running the 8.04+ version of the Dell OS.  I like to keep the screen on the dimmest setting in order to preserve the battery.  I find that certain programs will increase the brightness.  I have tried playing around with the settings on power manager, but to no avail.  Like hackel said, it doesn't happen all the time and it is quite easy to remedy, but it certainly is annoying.  I am fairly new to Linux and have just started using Ubuntu.  I think it may be a permissions issue.  Please help; it will be much appreciated.

---

### Post by dragonmojo on 2009-01-08
I am assuming many people are experiencing this (I too am having the same brightness issues)?

Dell Mini OS v8.04
:?:

---

### Post by chorca on 2009-02-17
I've got this problem in 8.10. An easy way to replicate it is to turn the brightness all the way down, close the lid, open it again, and see that the brightness is back at the max.

For me, tapping the brightness up/down once doesn't restore it, I hafta turn it all the way back down through the 10 steps or so.

---

### Post by Ryback on 2009-03-28
Does anyone have any ideas on how/if this can be fixed?  I'm getting a bit fed up of having to manually adjust my brightness down each time I boot/resume to conserve the battery life.  I'm not sure if it's something that would have been fixed in a bios update, but I started on A01 and am currently running A04 and the problem still persists.

---

### Post by dorkmo on 2009-03-28
i too have the same problem. when i lower it, it goes back up.

i notice that if im reading a webpage and im idle for a min, when i touch the down arrow to read on the brightness with reset up to 50% or so.

---

### Post by HumanUSB on 2009-03-29
I have this same problem with 9.04 beta.  It is really bothersome to have to keep doing this over and over every time I plug it in, close the lid and so on.

---

### Post by jaqrah on 2009-03-30
I am running 8.10 on my dell mini.

System>Preferences>Power Management

On AC Power tab, I have it set for 5%.  For Battery tab, I have **reduce back light** enabled.

I don't ever have issues with these settings.  Even when I plug in AC power, the screen flashes brightest setting and then re-adjusts to my chosen setting level.

Maybe I am lucky. ;)

---

### Post by Ryback on 2009-04-02
Jaqrah, what is it you set to 5% on the AC power tab?  I don't have any brightness settings available there.  Maybe this is another reason for me to reinstall with 8.10...

Cheers.

---

### Post by kokoshka on 2009-05-13
Same issue, new 8.04 install (back from 9.04) on the Dell Mini.  Whenever the brightness is changed by a method other than the function keys (auto dim after idle or closing the lid) the screen returns to a brighter state.  I did not have this issue under bios version a01, now on a06, maybe this is causing problems?

---

