---
title: "KDE notifications apparently broken (NOT Kubuntu)"
date: 2012-05-04
forum: Desktop Environments
---

### Post by suzumeuta on 2012-05-04
Since a few days ago I haven't been able to show KDE notifications without having to log out and back in. 
Every reboot, notifications get overtaken by NotifyOSD instead of appearing in the Notifications plasmoid as usual.
I am positive that it still worked right after upgrading to 12.04, and broke after some recent update three days ago. No configuration was altered manually before this (and since the system was totally installed and configured as 11.10 was).

Note that I am not using Kubuntu, but Ubuntu with KDE desktop on top*. This configuration has been working properly for years, as demonstrated by the fact that it works again after a logout (not reboot). 
As well, note that I use lightdm. I tried KDM just in case, but no difference.

I would post the X session errors file, but out of a generic DBUS complaint**, it contains absolutely no information related to this. When it doesn't work, and when it does. Those two programs are not very verbose. It seems that they might be starting in the wrong order (knotify4 before notify-osd), but no error messages appear.

Because this is a KDE issue, you might be tempted to redirect me to Kubuntu, but that's not the base distro I installed. I just installed KDE alongside Unity, starting from Ubuntu 12.04. This is no Kubuntu.

Please help. This is too time consuming due to having to reboot after every change (as a logout solves the problem temporarily, it cannot be used to check if it's fixed, so the full X minutes of restart have to pass between each attempt). I just can't do it by myself right now.


*) If you ask me why, it's more convenient since I got firefox and so on from the install disk, and I mix and match Qt and GTK apps. I prefer KDE's window manager and notifications, and Krusader, but otherwise I use mostly default Ubuntu stuff.

**) To be precise:
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.

---

### Post by TLArevo on 2012-07-01
Hi, I have the same issue under same configuration I tried disabling notify osd but it did not work and I checked every where possible but still no luck :(

---

### Post by TLArevo on 2012-07-03
I was able to solve the issue , answer is you just need to disable the Notify-OSD in dbus servers to do that only you need to rename the file

sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled

remember you may have disable other Notification services such as Xfce if they are available hope this works , cheers :)

---

