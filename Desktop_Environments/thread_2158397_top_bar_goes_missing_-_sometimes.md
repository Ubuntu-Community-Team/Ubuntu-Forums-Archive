---
title: "top bar goes missing - sometimes"
date: 2013-06-28
forum: Desktop Environments
---

### Post by jasonjob on 2013-06-28
I've had this issue off and on again since installing 12.04 (clean install, not upgrade).

Sometimes when I boot up, the top bar of the Gnome desktop is missing.  If I log out then log back in again, it appears.

I think I've finally found how to locate the log that would tell me what's going wrong (syslog - or is there a dedicated Gnome log that I just cannot find?), and this is what it has to say:

Jun 29 11:07:04 Carnelian gnome-session[2516]: WARNING: Could not launch application 'gdu-notification-daemon.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-disk-utility/gdu-notification-daemon" (No such file or directory)

This is the only log entry for gnome-session, so I suppose it's the issue at hand.  I have no gnome-disk-utility directory;  I don't know if I should, and if I should where it went, or, if I shouldn't, why the system tries to load this daemon from there.

So - is this daemon responsible for Gnome's top bar?  Is its failure to load why my top bar goes missing?  Should there be a matching entry for a successful load (following my log-out/log-in)?  Cos there isn't.

I'm using Ubuntu 12.04.  I log in to a classic Gnome desktop (not Unity or the modern Gnome), with compiz.

---

### Post by Frogs Hair on 2013-06-29
The gnome-panel dependency list in synaptic is fairly large and the gnome-settings-daemon is listed, but I don't find gdu-notification-daemon on my installation(!3.04) which is Gnome 3.6. I did locate some bug reports related to gdu-notification-daemon. I do have the Gnome session fall-back-session installed so the lack the daemon may be due to different Gnome versions or it has a new name.    

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/770254](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/770254)

---

### Post by Jonor on 2013-06-29
I get a different but somewhat parallel issue to this in that the top of maximised directory windows is lost behind the gnome classic top panel.

---

### Post by jasonjob on 2013-06-29
> **Jonor said:**
> I get a different but somewhat parallel issue to this in that the top of maximised directory windows is lost behind the gnome classic top panel.

I've had something similar to this in the past - I vaguely recall it being due to a setting in Compiz (specifically the one that allows windows to occupy the same space as the top bar - under Window Management - Move Window - Constrain Y - this keeps the windows in the workspace, and off the top bar).

---

### Post by Jonor on 2013-07-01
Thanks for the thought, i reject compiz acceleration options wherever possible so it probably is not that in my case.
Having the file manager handle the desktop as an advanced option does not seem to help either.
Hardware graphics maybe ? Do you have a dual core 64 bit amd CPU with onboard radeon graphics ?

---

### Post by jasonjob on 2013-07-11
Bump.

So, does nobody else have this happen?  Am I even looking in the right place for startup failures?  Cos I've looked up with this gnome-disk-utility is, and I can't see how it would affect my top bar.  I think it's something else, but I've no idea where to look - I cannot find a log file that details what Gnome does as it starts up.

---

### Post by Jonor on 2013-07-11
It isn't that you occasionally switch off the power to the monitor completely and then switch the puter on before 
the monitor so that the display resolution defaults to the wrong thing ?
This would possibly produce what you must be observing.

---

### Post by jasonjob on 2013-07-13
Nope, not that.  The resolution is fine.  The bottom panel is fine.  Desktop is fine.  But top panel just doesn't display (sometimes indicator.applet.complete crashes  - so it seems that that is also running but not showing).

---

