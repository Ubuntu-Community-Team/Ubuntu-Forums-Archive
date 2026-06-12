---
title: "desktop theme does not load at startup"
date: 2009-02-24
forum: Desktop Environments
---

### Post by dspisak on 2009-02-24
I was trying to have Firefox 3.0.6 recognize Adobe Reader as a plugin.  I was unsuccessful.  While trying other PDF related programs available in Synaptic I may have inadvertantly deleted a file that affects the desktop.  It was late at night and I may have selected "remove completely" instead of "remove" and deleted a configuration file.  Here is the problem.

After I login the standard gnome theme appears.  When I go to "Appearences" to select the Human theme the desktop suddenly changes to the Human theme.  What do I have to do to have the Human theme start or install automatically?  Is there a file I have to re-install?  TIA.

I am running ubuntu 8.10-amd64.

---

### Post by dspisak on 2009-02-27
Several other folks have asked for help with a similar problem. Is there anyone who can help us?  Thank you.

---

### Post by hictio on 2009-02-28
A long shot, but...
Turn it on, let it boot, and login.
Select the theme you want, and set it up like you want it.

Close everything and anything, and goto:

System > Preferences > Sessions > Options

Click on 

"Remember Curretly Runing Application"

---

### Post by dspisak on 2009-03-02
Hictio, thanks for the tip.  In the meantime I also tried to load Open Office 3.0.  However, Archive Manager always reported that the tar.gz file was corrupted.  I reloaded OO2.4 and now my Human theme starts automatically.

Lesson learned: be very careful when you delete a program or a file, a critical file included in a package also may be deleted with unintended consequences.

---

### Post by syed.rakib.al.hasan on 2011-01-27
this post seems helpful.

mitch wrote on 2011-01-08:
> 
I had this same issue on my i7 box (no SSD though) in both Ubuntu 10.10 and Linux Mint 10. I was able to fix the issue by following the solution posted here <https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809> post #68 which adds a short delay to the daemon loading on startup.

Basically it involves editing /etc/xdg/autostart/gnome-settings-daemon.desktop and changing line 4 to:

Exec= bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

Hope this helps.


reference: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296")

---

