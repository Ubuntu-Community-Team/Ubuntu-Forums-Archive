---
title: "Need To configure Video"
date: 2006-04-14
forum: Desktop Environments
---

### Post by dmyhand on 2006-04-14
I have hosed the video on my Breezy install.  Used to, I could use the xf86config command to reconfigure things if I needed to.  What can I use in Breezy to reconfigure video?  I am at a command prompt for login.  GUI ain't gonna cut.  This must be down the old fashion way.  Thanks, Dennis

---

### Post by Tim___ on 2006-04-15
If I understand you then you need to fix the configuration of xorg in order to get you're graphical login back.


Try this:

"sudo dpkg-reconfigure xserver-xorg" and follow the prompts

then:

"/etc/init.d/gdm restart" or a simple "reboot" should do.

---

