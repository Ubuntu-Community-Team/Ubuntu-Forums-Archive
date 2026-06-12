---
title: "firefox trying to restore old connections"
date: 2016-06-18
forum: Desktop Environments
---

### Post by Skaperen on 2016-06-18
if i reboot while *firefox* was running, restarting *firefox* will cause it to try to restore old connections.  **is there a way to turn that off? ** i also find that sometimes it tries to do this for recently closed connections (*firefox* exiting in all cases).

---

### Post by &amp;KyT$0P# on 2016-06-18
Halting the system while Firefox is running is a good way to get your Firefox [profile]("http://kb.mozillazine.org/Profile") corrupted.  If you don't like to risk losing your personal Firefox-related data, you should quit Firefox normally before shutting down or rebooting the system.  That's one way to stop the unwanted behavior.

You might also try setting about:config > browser.sessionstore.resume_from_crash to false if you don't ever want session restored after improper quitting of the browser: [http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash]("http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash")

---

### Post by Skaperen on 2016-06-18
i run many concurrently logged in users and sometimes i leave one or two running firefox because i am in a hurry to shutdown.  more often i am seeing this even when i make sure firefox is exited for on all users.  this issue has existed for many versions of firefox and on both Ubuntu 14.04 LTS (from System 76 and regularly upgraded) and Ubuntu 16.04 LTS (fresh install).

i am trying the *about:config > browser.sessionstore.resume_from_crash = false* setting for now (as of this reply).

---

### Post by &amp;KyT$0P# on 2016-06-18
and if that doesn't work, check the value of about:config > [browser.startup.page]("http://kb.mozillazine.org/Browser.startup.page")

---

### Post by Skaperen on 2016-06-24
> **halogen2 said:**
> Halting the system while Firefox is running is a good way to get your Firefox [profile]("http://kb.mozillazine.org/Profile") corrupted.  If you don't like to risk losing your personal Firefox-related data, you should quit Firefox normally before shutting down or rebooting the system.  That's one way to stop the unwanted behavior.

is there a signal that i could send to all firefox instances to have them do a graceful exit?  apparently SIGTERM is not it.

---

### Post by &amp;KyT$0P# on 2016-06-24
No there is no such signal, even SIGINT isn't handled "nicely".  As far as quitting Firefox nicely by command line, it's apparently possible: [http://forums.mozillazine.org/viewtopic.php?p=14223227#p14223227]("http://forums.mozillazine.org/viewtopic.php?p=14223227#p14223227")

I tested it in Lubuntu 14.04, and the command as written in that thread will sometimes pick out non-Firefox windows, but some using of [FONT=Courier New]wmctrl -l[/FONT] and [FONT=Courier New]wmctrl -i -c <id>[/FONT] should be able to discern all Firefox windows.  Make sure though that Firefox doesn't prompting about anything on exit, otherwise this won't quit Firefox.

However, I'm not sure how useful that will be to you, as I can't figure out a way to get wmctrl run as root (or sudo) to access windows of other users though - via root it does nothing and via sudo it still seems limited to the sudo'ing user...
Maybe it could run on logout?

---

