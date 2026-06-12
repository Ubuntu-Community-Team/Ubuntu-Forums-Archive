---
title: "Window appears black"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by tmcfulton on 2008-02-13
Hi, I'm having a bit of trouble here, take a look at the screenshot. 

[Here]("http://s224.photobucket.com/albums/dd270/T_McFulton/?action=view&current=Screenshot.png")

Using Ubuntu 7.10, all latest updates. This happens when desktop effects is disabled, and it's worse when desktop effects are enabled. I had the following plugins installed for a time: compizconfig-settings-manager gnome-art usplash startupmanager.

They're not installed anymore.

The output of "compiz" is:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

This was a problem before, uninstalling the package "compiz" solved the problem for a while (and strangely, Desktop effects still worked), I reinstalled the package later with no problems for a short while, then this started again. Uninstalling compiz no longer fixes the problem.

Any help would be appreciated.

Thanks.

---

