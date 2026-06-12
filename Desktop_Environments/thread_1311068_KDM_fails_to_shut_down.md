---
title: "KDM fails to shut down"
date: 2009-11-02
forum: Desktop Environments
---

### Post by antisho on 2009-11-02
I'm running Kubuntu 9.10. When I try to logout, shutdown, or restart, KDE gives me a dialog, and if I confirm nothing happens; everything keeps running. Subsequent attempts don't even pop up the dialog. 'kdmctl' also fails, leaving my only option for logout to kill X, and for shutdown to use 'shutdown' or 'halt' from the command line. Google has been of no help. I want to be able to logout and shutdown from within KDM so it can save my settings; any suggestions?

---

### Post by ScottMinster on 2009-12-23
I have the same problem.  I installed KDE on my Ubuntu install to check out the 4.x progress.  It looks nice, but I'm not able to logout.  I have the exact same situation -- logout brings up the dialog, and confirming the logout makes the dialog go away but no actual logout.  And further attempts to logout don't bring up the dialog at all.

My only recourse is to find the 'startkde' process and kill it.  That seems to kill enough processes to make KDE go away.

I figure I'm missing some package, but I don't know what that would be.\

Edit: I'm still using GDM from my Unbuntu install, not KDM, so I don't think the login manager is the problem.

---

