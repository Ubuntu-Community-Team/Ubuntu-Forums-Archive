---
title: "Gnome Settings Daemon"
date: 2007-10-19
forum: Dell  Ubuntu Support
---

### Post by Changturkey on 2007-10-19
I have this problem where the 'gnome-settings-daemon' will not start, this was not a problem until after I installed the restricted nvidia drivers. I looked at another thread that had a similar problem, and the suggestion was to reinstall gutsy, with a new .iso, but I really don't want to do that.

---

### Post by ionman on 2007-10-20
I have seen this problem before. You can add it to your session startup items by doing the following:

Go to System -> Preferences -> Sessions
Click Add
Give it a name
For the command type: gnome-settings-daemon
Hit OK
Close that window, logout and then log back in and you should be good to go.

- ionman

---

### Post by Changturkey on 2007-10-20
Thank you.

---

