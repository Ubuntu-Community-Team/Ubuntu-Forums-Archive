---
title: "Turn off automatic update."
date: 2006-04-30
forum: Desktop Environments
---

### Post by Titus A Duxass on 2006-04-30
breezy 5.10, gnome, mythtv, using a tv as a monitor.

How can I turn off the automatic update system at the command line.
I cannot do it at the desktop because the buttons are below the tool bar.

---

### Post by Sef on 2006-04-30
System > Administration > Software Preferences > Internet Preferences > unclick check for updates automatically

---

### Post by cilynx on 2006-04-30
Edit /etc/cron.daily/apt

That's the scripts that does the "apt-get update" every day.

---

### Post by Titus A Duxass on 2006-04-30
Thanks, fixed.

---

