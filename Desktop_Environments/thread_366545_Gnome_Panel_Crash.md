---
title: "Gnome Panel Crash"
date: 2007-02-21
forum: Desktop Environments
---

### Post by endlesssnowfall on 2007-02-21
Whenever I start a session, I see gnome panel starting up and then crashing, and a window titled "Bug Buddy" quickly appears but then disappears.  This repeats several times, until I don't even see gnome even starting up anymore.  I tried deleting .gconf .gconfd .gnome and .gnome2 files, but this didn't help anything.  I am using Beryl so the window decorations are still working, and Nautilus is still working too, if that means anything.  Any suggestions?

---

### Post by louis_nichols on 2007-02-21
I think that might be a bug in beryl. Especially if you're using the svn versions. I used to get those errors to.

Best is to not use beryl until this problem is fixed. Or use the stable branch of beryl, the 1.x

---

### Post by endlesssnowfall on 2007-02-21
I removed Beryl, but gnome still crashes.  My KDE session is unaffected though.

---

### Post by louis_nichols on 2007-02-21
Does this happen for all users? Isn't there a possibility the installation is broken and you need to reinstall gnome-panel?

---

### Post by Dragonath on 2007-02-21
(Hi, I'm new here.)

I think I have the same problem. It surfaced about a month ago - I couldn't log on because even though all the apps started merrily working and then the X window manager thing suddenly got a signal 15 from somewhere and decided that it would be better to keep me on the login screen. A temporary fix that I used until I got fed up (i.e. today) involved logging onto root (which magically had no problems at all) and deleted ICEauthority and esd_auth files out of my home folder. A few weeks ago this let me log on without problems (as long as I deleted the files before logging on), but the situation got worse again, and now it doesn't work again.
I'd really want to know what is it with my account that makes the session crash yet lets root  log on? Failsafe GNOME worked, but that didn't really get me closer to what I wanted.

---

### Post by endlesssnowfall on 2007-02-21
For me, failsafe GNOME doesn't work, and it happens for all users.  Reinstalling gnome-panel doesn't help either.

---

### Post by ssafika on 2007-02-23
Hi all!

I have exactly the same gnome-panel loop problem. After a few hours of keep trying to solve it, now I give up. If anyone knows the solution for this problem, please share with us. Now I have to use KDE, but it isn't for my taste.:confused: :( 
I tried to:
- delete .gnome* files from the home directory
- remove/install gnome-panel
- remove/install gnome
- kill gnome relevant processes

None of them helps.

Failsafe Gnome doesn't work, same as normal Gnome.
When I log in as another user it works fine. (Why? Where is the problem?) 

I use a few months ago the compiz engine, but I always have problems, so it was removed from the system.
Last package I installed before this crash shows up, was the ntfs-3g driver from a package, but I don't think that this caused the problem.
Generally my system is updated regularly.

Best wishes,
    Safi.

God Save Us All From Microsoft!

---

### Post by endlesssnowfall on 2007-02-24
I'm stuck with KDE as well, but I would love to have my Gnome back.  I've tried all the things you've tried, including different kernels, but nothing seems to work, not even logging on as a different user.

---

### Post by ElBarto87 on 2007-02-24
I have the same problem. I kinda new to Linux, and I don't know too much.
I've tried to reinstaling gnome-panel and gnome, without any progress.
When I log into "Failsafe Gnome" I get this message:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in."

Is this of any help?

---

### Post by ElBarto87 on 2007-02-24
I don't know if it helps all of you guys, but with me, it worked just to do:

Right click "Main Menu" -> "Edit Menu's" -> "Revert"

---

### Post by theRaven13 on 2007-05-06
right click where?

---

