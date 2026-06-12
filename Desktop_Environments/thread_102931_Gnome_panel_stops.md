---
title: "Gnome panel stops"
date: 2005-12-13
forum: Desktop Environments
---

### Post by GrumpyBob on 2005-12-13
I am experiencing system hang ups with Breezy, and I hope someone can suggest how to track down and identify the problem, and how to kick the system back into action without a reboot.  I've searched the form for similar problems, but haven't identified a post describing this.

What happens is that every so often an application (usually nautilus) stops responding.  An error will pop up about it not responding, and allowing a forced quit.  If the app is stopped, it cannot be restarted.  Subseqnet attempts to start an application from the Application menu of the gnome panel cause a lock up of the panel, and the selected app doesn't seem to start.

Where should I look for a log of events that might shed light on what's going on?  It's a bit of an irritation to have this happen  - albeit only every 1 to 3 days.

System is an IBM R52e Laptop, running Breezy.

Robert

---

### Post by teaker1s on 2005-12-13
try either installing 'system monitor' and you can see whats running easily or 
command
'top'

will list resource hogs by cpu usage and 'kill' will kill highest cpu usage

---

### Post by kaamos on 2005-12-13
Try "killall nautilus" from the terminal when this occurs.

Also with top it might be a good idea to use the command "top -u **username**", so that you see only your own processes. 

Hope this helps!

---

### Post by GrumpyBob on 2005-12-13
Thanks for these suggestions - will try when next it happens (probably tomorrow).

R

---

