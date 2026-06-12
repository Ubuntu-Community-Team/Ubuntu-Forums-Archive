---
title: "gksu / Xubuntu is not usable with Tablet computer"
date: 2006-08-29
forum: Desktop Environments
---

### Post by bcw on 2006-08-29
Hello,

I put Xubuntu on my Fujitsu Stylistic 3400s computer, which is a slate with a touchscreen.  It works fine (I'll put up a wiki entry for it once I've finished sorting it out).

Xubuntu provides gksu for administrative access.  I use XVkbd and xstroke for text entry by the stylus.  I use XVkbd for password entry, as I use a mix of capitalization and special characters for my passwords and passwords are masked by '*' characters, and while xstroke will make any character, it's not dead certain to get some of the less often used characters right the first time.

gksu takes over all the screen, greying out all other programs.  I can't use XVkbd to enter my password, so I can't do any administrative work, like installing new software.

Nowadays, not only are universities mandating laptops for students, some are mandating tablets.

If there's a simple solution, please let me know.  If not, this must be changed so that Xubuntu can be used with tablet computers (IMNSHO).

'gok' is unusable.  It insists the stylus can't be the primary input device, and does not rotate to match the screen orientation either.  I have not been able to get it to work on either this Fujitsu or my ST5032.

Please let me know if you have a solution, or I'll enter a bug on gksu.

So far, kdesu works fine in this situation - it does not close out all other programs when run.

Cheers,
Bret

---

### Post by mssever on 2006-08-29
I think you want to use gksudo --disable-grab. See man gksudo for more info. I don't know if this can be set in a config file or if you'll have to call it every time with that option (or alias it or do some sort of scripting).

By the way, out of curiosity, what advantage do tablets have over regular laptops? I can type faster than I can write, so being able to write on the screen doesn't seem terribly valuable.

---

### Post by bcw on 2006-08-31
> **mssever said:**
> I think you want to use gksudo --disable-grab. See man gksudo for more info. I don't know if this can be set in a config file or if you'll have to call it every time with that option (or alias it or do some sort of scripting).

I've discovered that I can change this system-wide by editing the 'gksu.schemas' file and changing the first entry from 'false' to 'true'.

I'll include this in my wiki entry for my two Tablet computers.

I've also entered this as a bug, as this fix is rather arcane.  I understand the choice is made for security reasons - but it's unusable now, so some other way needs to be found to cover the problem.

> By the way, out of curiosity, what advantage do tablets have over regular laptops? I can type faster than I can write, so being able to write on the screen doesn't seem terribly valuable.

Printed or script handwriting is slow, but (at least for recent generations) was taught to and practiced by most people, so it's available.  It requires extensive practice.

QWERTY typing is faster, but is only developed by a long period of  practice.  It also requires a keyboard, and for long periods of use, a particular work setup - to avoid RSI & back problems.

The original IBM Thinkpad idea was just that - a slate to help someone think.  That's what I intend for my Tablet.

There are several ideas for rapid text entry - and all will require some investment on my part practicing them.  I'm looking at the IBM SHARK method, the Fitaly keyboard (available as a free option with the XVkbd in GNU/Linux), and some other schemes I've found in my initial searching.  I've already got XVkbd & xstroke working.

With a tablet, I'm free to move around, free to not sit in a typing posture, free to draw pictures, free to pull diagrams around.  Once I've put in the practice with a chosen text entry method, I will manage what an average (probably not top) typist can do, which will do for me.  And I'll have a pad to think with.

Thanks for the tip about 'gksu'.

Cheers,
Bret

---

### Post by mroven on 2008-06-12
Hey!  I know this is kind of an old thread, but I found it because I was trying to solve a similar problem.  

I needed to enter a system password with a virtual keyboard (XVkbd) but couldn't because of the screen being locked out by gksu in Xubuntu 8.04.

Well, after quite a bit of looking around, I found:

/usr/bin/gksu-properties

Run this and a little pop-up will let you disable screen grab.  After you run that, you will be able to enter passwords with XVkbd.

-mroven

---

