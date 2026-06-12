---
title: "removing libsmbclient, also tries to remove other packages. why ?"
date: 2008-11-13
forum: Desktop Environments
---

### Post by ynilesh on 2008-11-13
nilesh@ubuntu:~$ sudo apt-get remove libsmbclient
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxbase2.6-0 libsvga1 libiso9660-5 libdvbpsi4 libxosd2 libvlc0 libenca0 mplayer-skins libwxgtk2.6-0 libggi2 libgii1 libmatroska0 libdvdnav4 libgii1-target-x libtar libvcdinfo0 libebml0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  amarok amarok-xine digikam gimp-gnomevfs gnome-applets gvfs-backends kaffeine kaffeine-gstreamer kdebase-kio-plugins kmail kmailcvt libgnomevfs2-extra libsmbclient libxine1 libxine1-misc-plugins
  libxine1-plugins mozilla-mplayer mozilla-plugin-vlc mplayer nautilus nautilus-cd-burner nautilus-sendto nautilus-share sound-juicer vlc vlc-nox vlc-plugin-esd vlc-plugin-pulse
0 upgraded, 0 newly installed, 28 to remove and 11 not upgraded.
After this operation, 130MB disk space will be freed.
Do you want to continue [Y/n]? n

---

