---
title: "cannot write to local X display"
date: 2010-12-03
forum: Desktop Environments
---

### Post by lvm on 2010-12-03
I want a script which runs from cron to post notifications to desktop, so I added 

zenity --notification --text="$message" --display=:0

to the script and local: to /etc/X0.hosts

$ xhost
access control enabled, only authorized clients can connect
LOCAL:

but when this script runs instead of notification I get

AUDIT: Fri Nov 26 02:02:35 2010: 6095 X: client 28 rejected from local host (uid 0)

in kdm.log. What am I missing?

---

