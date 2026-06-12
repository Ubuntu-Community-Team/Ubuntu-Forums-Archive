---
title: "&quot;There was an error starting the GNOME Settings Daemon.&quot;"
date: 2008-06-21
forum: Desktop Environments
---

### Post by BlackCow on 2008-06-21
So I haven't had this computer running to long. I just run a server on it mainly. When I log in to any of my user accounts it shows up with the tan screen for about 30 seconds, then a white box on the top right corner stays there for about 3 min! Eventually when it loads the white box shows up as an error box that reads,

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Is there a way to fix this? I google searched the error and got some people with similar problems but no solution. The last thing I did was install updates.

I don't want to lose any of my settings. If I can't fix it is there a way to reinstall Gnome without messing up the Ubuntu install (programs, files, settings, etc)?

---

### Post by puneit on 2008-06-21
Moving the .g* folders in the home folder to a new location and then restarting the system solves the issue but this also resets all customisations

---

### Post by BlackCow on 2008-06-23
I removed the following folders starting with g,

> 
.gconf
.gconfd
.gnome
.gnome2
.gnome2_private
.gnupg
.gstreamer-0.10
.gvfs


It did reset my settings except the window bar is still a color I set it to so something is making me think that I missed a file and didn't delete all my settings; I'm still getting the error. :(

---

### Post by BlackCow on 2008-06-27
I tried removing *.gksu.lock* and *.gtk-bookmarks* also but its still giving me the exact same problem. Are you sure there isn't something missing!

Is it at all possible to reinstall gnome or at least uninstall it and install xfce instead? (without messing with my other system files)

---

### Post by BlackCow on 2008-06-30
I created a new user and logged in, I had the same problem.

Do I have to reinstall Ubuntu?! I really don't want to.

---

### Post by collinp on 2008-07-01
No no, just reinstall Gnome and everything should be fine.

---

### Post by BlackCow on 2008-07-01
> **Hellow said:**
> No no, just reinstall Gnome and everything should be fine.

How do I do that?

---

