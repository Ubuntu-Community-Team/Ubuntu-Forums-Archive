---
title: "hibernate blank screen issue, can't do anything"
date: 2007-04-10
forum: Desktop Environments
---

### Post by martz on 2007-04-10
Greetings,
  I just reinstalled Ubuntu to my laptop (IBM T40, 512Mb ram) which had windows xp on it.  xp basically died (kept getting the bsod) so I decided to switch back to ubuntu.  I downloaded the live-DVD (edgy) , it ran fine (i've run ubuntu before on the laptop so this wasn't a surprise).  The installation went fine, everything loaded great.

Then I had to leave my apartment and goto work, so I told the laptop to go into hibernate.  Waited for it to do it's thing, looked like it was done (screen was off I'm pretty sure), so I closed the lid and went to work.  When I opened it at work, it was off.  So I turned it back on.  It went through the Ubuntu splash screen (where the bar loads from left to right) and then goes to a blank (black) screen.  And sits there as long as you let it.  Mouse doesn't show up, caps lock light won't work, etc.

So I booted in recovery mode, no problems... got to the command line and typed 'startx'... which led to the same blank screen.

So I figure hibernate had something to do with it.  And I don't know how to fix it any other way... so I decided to reinstall.  So I plug in the liveDVD again, and try and get it to boot.  EVEN IT ENDS UP WITH A BLANK SCREEN

WTF

anyone have any ideas what's happening?

p.s. sorry if this is in the wrong plane, feel free to move
p.p.s. I am now reinstalling via the text mode, so I'll keep you apprised of what happens

---

### Post by martz on 2007-04-10
Reinstallation via text mode complete.

I STILL GET THE BLANK SCREEN!

Please help

---

### Post by martz on 2007-04-10
Followed the directions here:

[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

First I tried using my ati card instead of vesa, but that gave the same results.  Using the vesa choice and the rest defaults fixed the problem.  I've even rebooted once just to make sure.  I'll have to fix my driver problems later, but now I can at least see the desktop manager and get into gnome.

---

### Post by knightnet on 2007-04-10
Have you POWERED OFF?

I had an odd problem with suspend/resume (all screen controls go transparent and screen refreshes are messed up). Rebooting didn't help - only an actual power off and then power back on again restores normal function.

Regards, J.

---

### Post by martz on 2007-04-10
yeah i rebooted... kinda hard to do all those things and not.  now it's back to not working, i've been trying to use the ati drivers, not the vesa ones, no luck...

---

