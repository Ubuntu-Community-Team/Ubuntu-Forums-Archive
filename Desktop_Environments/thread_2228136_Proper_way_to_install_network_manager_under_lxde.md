---
title: "Proper way to install network manager under lxde"
date: 2014-06-05
forum: Desktop Environments
---

### Post by PeterTaps on 2014-06-05
Folks,

I just built a minimal Ubuntu 14.04 box and installed lxde on it. 

Next, I installed the network manager:

$ sudo apt-get install network-manager
$ sudo reboot

After logging in, I was hoping to see nm-applet UI somewhere on the screen but I don't see anything.

I am used to using Openbox and lxde is a bit new for me.

Under openbox, I would install a program called "docker." Here are the things I used to do on openbox.

$ sudo rm /etc/xdg/autostart/nm-applet.desktop

Next, I would add the following lines to autostart:

docker &
(sleep 3 && sudo /usr/bin/nm-applet --sm-disable) & 

When I start openbox, I could see nm-applet UI in docker.


 I am wondering if all these steps are still required when under lxde.

Thank you in advance for your help,

Regards,
Peter

---

### Post by bapoumba on 2014-06-06
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118)

There is a current bug on lubuntu (although you do not say you are running lubuntu, but point out at lxde and openbox).

The work around is to manually add nm-applet to the Prefs > Default apps for LXSession > Autostart tab.

---

