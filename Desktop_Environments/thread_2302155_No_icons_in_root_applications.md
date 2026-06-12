---
title: "No icons in root applications"
date: 2015-11-08
forum: Desktop Environments
---

### Post by grzesiek811 on 2015-11-08
I've installed fresh kubuntu 15.10. There is problem with icons in root applications. When I start kdesudo dolphin, then dolphin start with no icons. Other applications like kate, systemsettings also have no icons.

[IMG]http://i.stack.imgur.com/nsEKt.png[/IMG]

Is there any solution?

---

### Post by bapoumba on 2015-11-08
Please see here about running graphical root applications : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
We do not provide support to running the graphical environment as root. You can look elsewhere about the root theme however.
Thread closed.

Edit : reopened.

---

### Post by seedsgrow2 on 2015-12-02
*We do not provide support to running the graphical environment as root.*

This is not about running the graphical environment as root. This is about occasionally running the file manager as root. I have done this for years on KDE with no problems. It makes some tasks more convenient as long as one is careful about it. One distro I have used, I don't remember which one, even had a launcher to open Dolphin as root set up and placed in the menu. With Kubuntu 15.10, the Plasma desktop it currently employs, and the current version of Dolphin, this function has been crippled. One question I have is whether this was intentional or whether it is a bug that hasn't been worked out yet. I have set up a launcher for Kate that opens it as root, and it seems to work just fine. I can therefore still do most of what I used to do by opening Dolphin as root easily enough, so crippling Dolphin's ability to run in root mode is no great tragedy. I have, however, also noticed that I cannot configure applications to have a different color scheme when running in root than when they run in user mode as I used to. System Settings 5 seems to have the same problems Dolphin has when opened with the kdesudo command. If I fight through the crippling of the interface, It does actually seem to allow me to make the changes, but the changes are not implemented.

---

### Post by sd08154711 on 2015-12-24
I think, your bug is already reported: [https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/1509562](https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/1509562)
I run Dolphin from XUbuntu and experience the same (as regular non-root user)

---

### Post by furumaro22 on 2016-05-15
adding  
XDG_CURRENT_DESKTOP="KDE"
to /etc/environment

solves the problem for me

---

### Post by alexsk on 2017-04-27
***furumaro22***
[I]adding
XDG_CURRENT_DESKTOP="KDE"
to /etc/environment

solves the problem for me [/I]


Thank you, this works for me as well!

---

### Post by oldos2er on 2017-04-27
Old thread closed.

---

