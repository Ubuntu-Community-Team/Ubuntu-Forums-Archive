---
title: "After loading screen, black screen with wait cursor!"
date: 2008-04-24
forum: Desktop Environments
---

### Post by pj_rage on 2008-04-24
I'm very new to linux.  About 3 months ago I installed Gutsy (I think, it's version 7.10 anyway) on a laptop I had kicking around.  It worked fine, no problems, but then I never really used it.  A couple days ago I decided I would start toying around again, and finally got my display settings right so that it took up the whole 1600x1200 screen and looked great.  I had logged in/out to get the settings to change, but not restart.

Then, I installed tcl8.5 because I wanted to start trying out tcl.  For the record, this laptop isn't on the net and can't be, so I can't use the apt-get stuff I see everywhere.  Anyway, I downloaded the package, copied it over, double clicked it, and it seemed to install just fine.  As soon as it was done, I wanted to try a script I wrote out, so I tried to open a terminal.  I was able to move the mouse and select it from the menu, but it didn't open.  I tried a few times, and it let me click, but just didn't do anything.  I tried a few other programs, and tried viewing my computer and stuff and nothing would open/happen.  So I figured it needed a restart.  So I did, and right after the ubunut loading screen where the progress bar advances, where it would normally go staight to a visual login screen, it went to a black screen with the animated wait cursor.

I did a ton of searches and all I can find are people with the same problem, but none of the threads ever found a resolution.

I've redone my xorg.conf file a bunch of times by doing sudo dpkg-reconfigure xserver-xorg, but nothing changed anything.  It seems that you really just change your display settings, but mine seem fine because I can see the cursor just fine.  I CAN boot from the live CD, no problem.  I even copied over the xorg.conf file that the live CD filesystem has, and that didn't work.  I also compared the live CD gdm.conf file and it is the same (except for auto login being false on my HDD install) to the HDD install.

It's like it's paused waiting for something, but I don't know what?  I can CTRL ALT F1/F2/etc to view all the consoles, log in that way, and mess around, but I can't get the xserver started for the life of me.  If I remove the lock from /tmp/.X0-lock and type startx, it will bring me back to the black screen with the waiting hand.  If I CTRL ALT F7, then CTRL ALT BACKSPACE BACKSPACE it will reset it, and go right back to the black screen with the waiting hand.

I'm not sure what to do.  I really would rather solve this problem than to reinstall or anything, if for no other reason than to increase my linux knowledge!

Any ideas?

---

### Post by Periswell on 2008-04-24
is this hardy? did gusty work? if so did you use a iso cd install or update manager?

---

### Post by pj_rage on 2008-04-24
Yes, it's Gutsy Gibbon version, originally installed with the iso CD, and I installed the tcl8.5 that evidently broke it by downloading the package from the web, copying it over, and double clicking it inside of the ubuntu graphic interface (when it was still working).  Seemingly, this package is what broke it, because right after it finished, I couldn't open anything, and as soon as I rebooted, it wouldn't go back in.

Evidently this package broke something, for some reason, I'm just trying to pinpoint what it was and how to fix it.

---

### Post by pj_rage on 2008-04-28
Anyone have any ideas?

---

