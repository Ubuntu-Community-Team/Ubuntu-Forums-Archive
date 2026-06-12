---
title: "Desktop (xfce) broken - no icons - File Manager not running"
date: 2018-08-21
forum: Desktop Environments
---

### Post by vostoklake on 2018-08-21
Running Ubuntu Studio 16.04.1 on a 64-bit laptop, kernel 4.15.0-32-lowlatency 

A few weeks ago my xfce4 desktop stopped showing any desktop icons, although it still shows my previously selected wallpaper.
Also, File Manager (thunar, I believe), stopped working: it opens a blank window and hangs.
When I try to change the Desktop wallpaper in Settings Manager, it does nothing.

Thunderbird Mail also refuses to run - as my profile is on a network drive, this makes me think that the problem may be related to the two network drives I have auto-mounted on my desktop.

Running "xfwm4 --replace" just hangs.
Deleting all cached sessions and rebooting does nothing.

I thought I'd solved the problem last week by activating "Display chooser on login" and creating a fresh session - but today the fresh session also stopped working, and every new session I create has the same problem.

I created a new user and that doesn't seem to have the problem - however, without File Manager working, I'm not sure where to go from here to repair my main user.

HELP PLZ

---

### Post by vostoklake on 2018-08-22
Update - as I suspected, removing the network drives from fstab solves the problem. But:

a) I need those network drives for my work;
b) why are these network drives a problem now when they weren't until recently?

---

### Post by vostoklake on 2018-08-25
Okay, I seem to have fixed it, and here's what I did for future reference: I had been having a problem with the network drives not mounting at startup. I found this thread: [https://ubuntuforums.org/showthread.php?t=2350427](https://ubuntuforums.org/showthread.php?t=2350427) and I enacted BOTH solutions: editing /etc/fstab AND editing /etc/rc.local.

When I reverted the edit to /etc/rc.local but kept the edit to /etc/fstab, things seem to have gone back to normal.

Still scratching my head about WHY any of this might have happened... interested in comments.

---

