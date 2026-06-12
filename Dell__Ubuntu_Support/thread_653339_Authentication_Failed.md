---
title: "Authentication Failed"
date: 2007-12-29
forum: Dell  Ubuntu Support
---

### Post by JeanP Niptik on 2007-12-29
I'm using ubuntu 7.10 It was installed and it worked well. I have it on my laptop.
But I don't like it because it doesn't ask for a password or user name. It just boot up up and straight.

So i was afraid someone can access my files. So I tried to find a way to ubuntu ask for a password when it
boots up.
So i i went to system menu and to administration and i found where there is a check mark ubove my user name that says 'automatic login' and unchecked it.
thinking that it will not automatically log me in but it will ask for a password.

Then i restart. When i restart ubuntu loads up to a window that pops up and said 'Authentication failed'.
And it stops there nothing. I tried to restart again still the same window appears-Authentication failed.

I can't use my laptop anymore its logged or something. Can anyone help please.

JeanP

---

### Post by neptho on 2007-12-30
Try resetting your password.

When your computer is starting up, press 'Esc' to get into the GRUB menu; choose the second kernel option, "Recovery Mode",  Let it start up; this will be all in text mode.

When you're at a shell, you may then run 'passwd yourname', where yourname is your login name.  Press ctrl-d (or type logout, and press enter), and resume life as normal (hopefully).

---

### Post by icheyne on 2007-12-30
[http://ubuntuforums.org/showthread.php?p=3605925](http://ubuntuforums.org/showthread.php?p=3605925)

---

