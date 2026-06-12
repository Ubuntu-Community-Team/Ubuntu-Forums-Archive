---
title: "Black screen after session logout"
date: 2011-02-28
forum: Desktop Environments
---

### Post by ozark_hillbilly on 2011-02-28
I found a similiar thread that had some info but it was for KDE.
I am running Gnome Desktop w/ 10.04.

My screen goes black after session logout and a soft/hard boot is necessary. Switch users works fine.

********************************************

This is the text from a previous thread:

Re: Black screen after logout
What videocard driver are you using?

In the past, some drivers (notably Intel's) made the X server crash when trying to regenerate the X session at logout. In essence, instead of shutting down X and starting it again, it tries to reuse the same process to save time and resources. If so, I think there will be a crash backtrace in /var/log/kdm.log.

You can disable this resetting behavior in /etc/kde4/kdm/kdmrc by finding the TerminateServer=true line and uncommenting it.

******************************************

Where would I look under Gnome /etc folder for something similiar if this might be the problem?

---

