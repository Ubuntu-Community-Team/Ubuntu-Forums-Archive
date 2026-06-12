---
title: "x11vnc tray icon"
date: 2007-11-27
forum: Desktop Environments
---

### Post by NTolerance on 2007-11-27
I'm running x11vnc on my Ubuntu PCs for remote access.  It works well, but I would like to have a visual notification if the GUI is being manipulated remotely.  A notification area icon would be great.  I was looking on the x11vnc site about this, and it claims that a tray icon is available:

[http://www.karlrunge.com/x11vnc/#faq-gui-tray](http://www.karlrunge.com/x11vnc/#faq-gui-tray)

I used this howto for setting up x11vnc:

[http://ubuntuforums.org/showpost.php?p=2757451&postcount=6](http://ubuntuforums.org/showpost.php?p=2757451&postcount=6)

I see that the tray icon requires a program called /usr/bin/wish, but I don't have that installed nor do I see it in Synaptic.  Any ideas?

Edit:  Looks like the wish package is actually named tk8.4 in the repos.

Edit2:  Added -gui tray to my x11vnc command line stored in /etc/gdm/Init/Default.  This caused GDM to freak out and I couldn't type anything in the login box.

---

