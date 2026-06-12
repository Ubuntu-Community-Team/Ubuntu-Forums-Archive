---
title: "Unwanted application autostart"
date: 2005-05-17
forum: Desktop Environments
---

### Post by npu on 2005-05-17
Where do I see/edit which programs are executed at a reboot?

For some odd reason, everytime I restart I automatically get two Gnome-Bittorrent "Open File" dialogs. I don't want them there. Must be some init-file, but I can't find it.
My System/Preferences/Sessions/Startup Programs is empty.

---

### Post by harryc on 2005-05-17
Run ps aux from a console. Look for the two Gnome-bittorrent entries. Note the PIDs. Issue a kill PID# from console on both of them.  Logout and save the session while doing so. Log back in.

---

### Post by tread on 2005-05-17
Yup, that should do it. What Harry is saying is, you probably saved the session with those two programs open.

---

### Post by jcooper on 2005-05-17
An easier way:

System > Preferences > Sessions.

Select Default in the list, then click Delete.

---

### Post by npu on 2005-05-17
Thanks!

---

