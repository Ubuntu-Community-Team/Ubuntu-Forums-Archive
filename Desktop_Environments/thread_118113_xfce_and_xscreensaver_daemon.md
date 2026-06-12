---
title: "xfce and xscreensaver daemon"
date: 2006-01-16
forum: Desktop Environments
---

### Post by Jason-X on 2006-01-16
I can't get the "xscreensaver daemon" to automatically start when I log into xfce. If I go to "xfce settings manager" and click on "screensaver" I get this message:
[B]
"xscreensaver damon not running on display ":0.0,"
Do you want to launch it now?"[/B]

I have tried to start it by adding this line to my "Desktop/Autostart/start.sh" file:

**/usr/bin/xcreensaver -no-splash -W &**

This still does not work. Has anybody managed to make this work. If so how?

Many thanks
Jason

---

### Post by hollowhead on 2006-01-16
I had the same problem in fluxbox this works for me;

xscreensaver -nosplash &

in my startup file.

---

### Post by Jason-X on 2006-01-16
Thanks Hollowhead, I tried this and still no joy. :confused:

---

### Post by hollowhead on 2006-01-16
I'm stumped.  It is annoying I know -what would we do without those brillaint time waiting screensavers, they just get better and better.  I 've only just worked it out in fluxbox, took a couple of readings of the xsceensaver man file.  Have you tried looking at XFCE homepage or googling it?

---

### Post by bucho on 2006-04-24
Any luck?  I've just done a fresh install of Xubuntu, and the screensaver daemon refuses to automatically start.

Tony

---

### Post by redcharlie on 2006-06-28
Lines 53 and 54 from /etc/xdg/xfce4/xinitrc:
> 53 # Launch xscreensaver (if available), but only as non-root user
54 test $UID -gt 0 -a -z "$VNCSESSION" && xscreensaver -no-splash &

You can chech to see that you have the same.  If it's already there and not working, maybe try removing the tests and just have it always start.

---

### Post by guysmiley25 on 2007-01-22
I know this thread is old but I ended up here, So if you have, you may have the same problem.

**[COLOR="Red"]Solved:[/COLOR]** Check out [this]("http://ubuntuforums.org/showthread.php?t=342906&") thread for the solution.

---

