---
title: "How to change resolution?"
date: 2005-08-31
forum: Desktop Environments
---

### Post by ~Gh05t~ on 2005-08-31
Hi all,
ive installed kubuntu 5.04 on my asus-notebook and its very nice. But when i plug an external monitor on it the resolution doesnt fit (my notebook is using 1680x1050, my monitor is a 1280x1024 LCD), so my desktop is missing its borders  :-? .
How do i change KDEs resolution? Can i define a seperate resolution for VGA-out and keep the resolution on my notebookscreen?

Thanks for help
~Gh05t~

---

### Post by f1dave on 2005-08-31
Not sure about the second question, but to change the resolution in kde right click your desktop and select configure desktop. Then go to display, and choose your resolution there.

---

### Post by ~Gh05t~ on 2005-09-01
ok, now it works. Problem was, that there was only one resolution defined in xorg.conf, so i could only select one resolution in KDE-display menu.

But how to do the second thing? Is that possible?

---

### Post by gnutux on 2005-09-01
You need to add an extra line on the xorg.conf in your Kubuntu installation. Just add 1280x1024 on the line under your flatscreen's resolution. Restart the X server, then there would be an extra option in the KDE Control Centre. Just change it w/ the Control Centre each time you plug your external monitor.

gnutux

---

### Post by ~Gh05t~ on 2005-09-02
yeah, ive added other resolutions in my xorg.conf, but is it possible to set another resolution for VGA out by standard? I do ONLY want the 1680*1050 resolution for my notebooks display. But i will NEVER use that resolution for VGA-out, but 1280*1024, 1024*768 or 800*600. If i could set default resolution for VGA-out to 1024*768 i would only have to plug in the monitor/beamer... no other changes.

---

