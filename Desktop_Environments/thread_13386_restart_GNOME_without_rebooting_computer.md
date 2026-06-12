---
title: "restart GNOME without rebooting computer?"
date: 2005-01-31
forum: Desktop Environments
---

### Post by Jad on 2005-01-31
Hi, 
using
Press 'Ctrl + Alt + Backspace'
as described in [http://ubuntuguide.org/#restartgnomewithoutreboot](http://ubuntuguide.org/#restartgnomewithoutreboot)
shut down my computer
any idea?

---

### Post by Ufo on 2005-01-31
Hi

 One way to restart Gnome without rebooting computer (or actually restarting GDM):

Go to console CTRL+ALT+F1
$sudo /etc/init.d/gdm restart

I think this would work also from terminal, but I have not tried that.

---

### Post by Ufo on 2005-01-31
Hi again

I found some posts in google about same problem.

[http://groups-beta.google.com/group/linux.kernel/browse_thread/thread/7f3a9d5b8bf09ed3/5611736eda9e2d8e?q=%22ctrl%2Balt%2Bbackspace%22%2Bshutdown&_done=%2Fgroups%3Fq%3D%22ctrl%2Balt%2Bbackspace%22%2Bshutdown%26hl%3Den%26lr%3D%26sa%3DN%26tab%3Dwg%26&_doneTitle=Back+to+Search&&d#5611736eda9e2d8e](http://groups-beta.google.com/group/linux.kernel/browse_thread/thread/7f3a9d5b8bf09ed3/5611736eda9e2d8e?q=%22ctrl%2Balt%2Bbackspace%22%2Bshutdown&_done=%2Fgroups%3Fq%3D%22ctrl%2Balt%2Bbackspace%22%2Bshutdown%26hl%3Den%26lr%3D%26sa%3DN%26tab%3Dwg%26&_doneTitle=Back+to+Search&&d#5611736eda9e2d8e)

It looks like it could be somekind of "quick power off" feature.

---

### Post by Jad on 2005-01-31
the point is, Ctrl + Alt + Backspace was working fine as described in Ubuntu guide, but not it shud down the computer, 
Just wanted to check How, and Why it was changed?

I don't usally need to restart gnome, so its not a big problem, Just want to know Why and How

---

