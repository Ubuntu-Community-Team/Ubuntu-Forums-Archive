---
title: "&quot;This folder is empty.&quot;"
date: 2010-10-30
forum: Desktop Environments
---

### Post by james_xxx on 2010-10-30
In Kubuntu 10.10, using KDE 4.5.2, the message "This folder is empty." is always smack in the middle of my Folder View, which is set to show the contents of my Desktop directory.

Aside from putting something in that directory, is there anything that can be done to make this message go away?

It's a small annoyance, but still an annoyance I would like to get rid of.

Thanks!

---

### Post by ankspo71 on 2010-10-31
Hi,
I don't think it is possible without modifying the source of plasma_applet_folderview.so. If you would like to try to modify the source code then compile it for yourself, then try this command in the terminal:
```
cd Desktop
apt-get source plasma-widget-folderview
```
That will download the folderview widget source codes and place it on your desktop. Note that this widget belongs to the kdebase metapackage if you can't download it this way. I'm not in my Kubuntu to see if source code is available this way, but it should work.

Downloadable source package for KDE 4.5.1:
[http://packages.ubuntu.com/maverick/plasma-widget-folderview](http://packages.ubuntu.com/maverick/plasma-widget-folderview)

Also, I don't know if this will get rid of the "This folder is empty" message, but there is a screenlet applet that works like a folderview alternative. It is meant for GNOME desktop users, but it should work for KDE users too. [http://www.omgubuntu.co.uk/2009/04/folderview-screenlet/](http://www.omgubuntu.co.uk/2009/04/folderview-screenlet/) . Installation of screenlets is required for this, which can be found in Synaptic Package Manager and Software Center.
Hope this helps.

---

