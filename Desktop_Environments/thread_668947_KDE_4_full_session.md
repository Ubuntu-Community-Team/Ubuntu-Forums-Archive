---
title: "KDE 4 full session?"
date: 2008-01-15
forum: Desktop Environments
---

### Post by telepete on 2008-01-15
I really need help with this. I installed KDE 4 as per the instructions on the Kubuntu website. The installation went smoothly and I can see all of the KDE 4 applications in my KDE 3 menu. When I log out I can only log back in as 'default', 'KDE' (3.5), or 'failsafe'. Why doesn't KDE 4 appear in this menu like the instructions say? I am running Kubuntu 7.10 64 bit.

Anybody out there?

Thanks in advance,
pete.

---

### Post by sauronsmatrix on 2008-01-18
that is strange, are you sure you installed it properly as per these instructions from kubuntu official site?:

>     * Remove previous KDE 4 packages, they are not compatible (apt-get remove kdelibs5 kde4base-data kde4libs-data)
    * Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main to your /etc/apt/sources.list
    * Install kde4-core, note that PPAs aren't authenticated so you will likely get a warning when installing
    * KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager.
    * To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 then and run /usr/lib/kde4/bin/startkde in the Xerphyr xterm.

---

