---
title: "Ubuntu starting up apps that aren't in the startup program list"
date: 2008-04-27
forum: Desktop Environments
---

### Post by luke16 on 2008-04-27
Whenever I startup ubuntu, I have a number of apps that startup with it, such as audacious, deluge, an open nautilus folder, firefox, and a terminal. At one point in time, I had added these to system>preferences>sessions>startup programs, but have since deleted them from there, but they still launch everytime I boot ubuntu. I have made sure that the "automatically remember apps" box is unchecked on the session options tab. I have looked in /etc/init.d/ for the app names, but they aren't there. I don't know what else ubuntu uses for its launch script, or where else to look. Also, the startup apps aren't loaded consistently every boot up time. Sometimes there are 2 audicious instances running (even though this should be impossible) after boot up, and sometimes the open nautilus window or the terminal don't show up. It doesn't seem to matter whether I close down everything manually before I restart the OS or not.

I was hoping that upgrading to hardy would fix this, but now along with the apps launching at startup, the bootup splash screen is replaced by terminal output early in the start up process, and the only thing I can determine that could be causing this is firestarter, because its the only thing that I can tell fails to start. When shutting down, the computer also pauses when reading /etc/init.d/ script for about a minute everytime. I haven't jotted down exactly what it says yet. I don't know if this could be related or not.

---

### Post by conundrumx on 2008-04-29
I am getting this issue as well.  I'm running Hardy, and have been since beta (4 or 5, I think) if that helps narrow it.

---

### Post by conundrumx on 2008-04-29
More digging yielded ~/.gnome2/session

If you edit it you'll find your ghost start up programs there, simply remove the line and restart your session (log out, log back in).  It seems like newly added applications don't cause this problem, but that's not definitive.

---

