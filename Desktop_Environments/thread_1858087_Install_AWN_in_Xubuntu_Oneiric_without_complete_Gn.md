---
title: "Install AWN in Xubuntu Oneiric without complete Gnome"
date: 2011-10-11
forum: Desktop Environments
---

### Post by dentaku65 on 2011-10-11
Hi,
in my path for escaping Unity I encountered Xubuntu :-)

I found a way to install the AWN docky without porting all the Gnome stuff connected to the awn package.

Here the command:

```
sudo apt-get -no-install-recommends awn-settings awn-applet-animal-farm awn-applet-awn-notification-daemon awn-applet-awn-system-monitor awn-applet-awnterm awn-applet-bandwidth-monitor awn-applet-battery-applet awn-applet-cairo-clock awn-applet-cairo-main-menu awn-applet-comics awn-applet-common-folder awn-applet-cpufreq awn-applet-dialect awn-applet-feeds awn-applet-file-browser-launcher awn-applet-garbage awn-applet-hardware-sensors awn-applet-indicator awn-applet-mail awn-applet-media-control awn-applet-media-icon-applet awn-applet-media-player awn-applet-notification-area awn-applet-quit-applet awn-applet-related awn-applet-shinyswitcher awn-applet-showdesktop awn-applet-stack awn-applet-thinkhdaps awn-applet-todo awn-applet-volume-control awn-applet-weather awn-applet-webapplet
```

I'm using it for a while now and it is pretty good, even without xfce-panel ;-)

Compiz required.

bye

---

### Post by tetsuo76 on 2012-09-22
Many thanks for this.  There is a typo. It should be "--no-install-recommends"

Apart from that it works great!

---

