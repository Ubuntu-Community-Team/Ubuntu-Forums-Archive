---
title: "How to ensure that systray gets loaded before nm-applet.desktop?"
date: 2014-06-22
forum: Desktop Environments
---

### Post by PeterTaps on 2014-06-22
Folks,

I am running minimal Ubuntu 14.04 + openbox + network-manager.

In the past, when I bring up openbox, "ps" would reveal that nm-applet is running (because of /etc/xdg/autostart/nm-applet.desktop). However, there would be no visible icon for me to configure wireless, etc.

The following is the workaround I used to use:

1. sudo apt-get install docker
2. sudo rm /etc/xdg/autostart/nm-applet.desktop
3. Edit autostart and add the following two lines
 
docker &
(sleep 3 && nm-applet) &

This ensured that docker runs before nm-applet and the icon becomes visible under docker.

However, I would prefer to use /etc/xdg/autostart/nm-applet.desktop, if possible, and not go through this workaround. So, it is possible to perhaps create "docker.desktop" and make nm-applet.desktop dependent on it? Or, is there a better solution?

Another related question. So far I have not used any panel with openbox. I am leaning towards lxpanel. I understand lxpanel already has systray and therefore I won't need docker anymore. If I do switch to lxpanel, how can I ensure that lxpanel runs first before nm-applet kicks in?

Thank you in advance for your help.

Regards,
Peter

---

