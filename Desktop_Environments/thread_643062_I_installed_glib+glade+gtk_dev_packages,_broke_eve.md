---
title: "I installed glib+glade+gtk dev packages, broke every X-windows program in my system"
date: 2007-12-17
forum: Desktop Environments
---

### Post by DennisFerron on 2007-12-17
I'm running Ubuntu Gutsy Gibbon.  I installed several glib/gtk/glade dev packages, sorry but don't remember which ones.  (How, using apt-get or apt-cache, do I list the packages I have installed now?  Since my desktop and X windows apps are broken, I can't even get to Synaptic package manager.)  My question is, on Ubuntu Gutsy Gibbon which of the glib, gtk, or glade packages is *likely* to have caused a problem like the following, and how to I get rid of it or replace it:

I was trying to compile a program, and it kept complaining about missing dependencies having to do with Gnome or Glib or GTK or something.  I kept running "apt-cache search" and "apt-get", and installed any dev package with glib, gtk, or glade in it's name, but I never could get the thing to compile.  

I suspect one of the packages I installed broke my system, but I have no idea which one and I can't remember everything I installed.

After installing all these gtk development packages, everything was fine for a few hours browsing, until I noticed I couldn't open gedit.  Then I couldn't open anything on the gnome menus.  When I tabbed back to Firefox, Firefox went ka-blooey (popped out of existence for no reason).  One by one every program on by desktop self-destructed; then the desktop locked up.

I used ctl+alt+F4 to switch to another console and typed "sudo shutdown now".  For some reason, on my system "shutdown now" has never turned the computer off; it just does a warm reboot.  So I did the warm reboot and ctl+alt+F7 to get back to the gnome login screen.  When I logged in, it did not go to the desktop, but popped back with a message saying my X session lasted less than 10 seconds, and that it could indicate something wrong.  I clicked to view the error message and it was something like "glibc-2.0: pthreads issue."

I have since cold-rebooted and still have the same problem.  Will re-installing a package fix the problem, or is there some other package I need to get rid of?

---

