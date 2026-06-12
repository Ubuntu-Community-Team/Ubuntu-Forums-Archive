---
title: "KDE won't be default..."
date: 2007-03-05
forum: Desktop Environments
---

### Post by Pikestaff on 2007-03-05
Hey guys... I like messing around with the different desktops available in 'buntu, so I have the KDE, Gnome, and XFCE desktops all installed and I log into each regularly.  I do think I use KDE the most, though, and I feel the most comfortable with it, so I'd like to have KDE set as default.

When I first installed the other desktops I selected KDE as my default when it asked, and I've gone into the /etc/X11/default-display-manager file and it says /usr/bin/kdm like it should.  However, at the login screen, when I select default, it always goes into Gnome.  This isn't a huge problem, I can just manually choose KDE when I want it, but I'd like for it to be default rather than Gnome.

Any suggestions on how to fix this?  Thanks in advance! 8)

---

### Post by Dr. Nick on 2007-03-05
If you are going to use kde most often you may try installing kdm and using it instead of gdm.

---

### Post by aysiu on 2007-03-05
Sounds as if it already is KDM.

KDM remembers whatever you last logged into as the preferred desktop environment unless you deliberately choose to log into something else.

GDM, however, will ask if you want to make the desktop environment the default one every time you pick one other than the default.

Pikestaff should switch from /usr/bin/kdm to /usr/sbin/gdm

---

### Post by Dr. Nick on 2007-03-05
Thanks for the correction, I totally overlooked the kdm line.

---

### Post by Pikestaff on 2007-03-05
Thank you for the replies!  I switched from /usr/bin/kdm to /usr/sbin/gdm.  A couple interesting things happen now when I log in and out.  One of them is that I get the Xubuntu login screen now (although I can login as any desktop environment.)  Another is that I still get Gnome for default, regardless of what I was using in my last login.  When I click on default a box pops up telling me my default is KDE, and yet actually logging into default gets me into Gnome.

Heh, if any of that made sense.  Any ideas on what's going on?

---

### Post by igknighted on 2007-03-05
Try looking at [www.gnome-look.org](www.gnome-look.org) for a gdm theme that you may like better (if you don't care for the xubuntu one).  There is some nice stuff.  To install just log into gnome and go to system->admin->login screen and install the new theme (leave as .tar.gz, it wants it like that).

---

