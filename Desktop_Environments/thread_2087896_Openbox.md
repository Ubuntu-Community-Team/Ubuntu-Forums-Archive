---
title: "Openbox"
date: 2012-11-24
forum: Desktop Environments
---

### Post by searchfgold6789 on 2012-11-24
Hi,
I like Openbox. It is much faster than the default Lubuntu environment and frees up a lot of RAM. 
However, when I log in, the configuration is apparently absolutely barebone. I get to choose themes and make tweaks with ObConf, but most things are left blank that I would prefer to be filled, for example Applications, and desktop icons, and *especially* a panel would be nice.
In fact, that's all I really need, is a panel. Can anyone point me to a guide or show me how to make a panel in OpenBox? I read on the OpenBox wiki that you need separate software, and I googled some, and found lists of them, but their function is unclear.
Much appreciated,
 - searchfgold6789

---

### Post by ibjsb4 on 2012-11-24
Not sure what your up to, but if your running Lubuntu why not just use whats there?  In terminal:

```
lxpanel
```

---

### Post by 2F4U on 2012-11-24
OpenBox does not come with a panel by default, you have to choose and install one yourself. Thats the obvious difference if you run a window manager (OpenBox) versus a desktop environment (LXDE). 

There are quite some panels you can choose from:

[http://penguininside.blogspot.de/2009/09/10-panel-dock-applications-for-your.html](http://penguininside.blogspot.de/2009/09/10-panel-dock-applications-for-your.html)
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by quequotion on 2012-11-25
I use openbox when I need to save resources or when compiz breaks down, but I didn't want to install all of lxde or any of lubuntu.

You can put together a fairly decent desktop with just openbox and lxpanel:```
sudo apt-get install openbox lxpanel
``` To start lxpanel with openbox, add it to **/etc/xdg/openbox/autostart**```
lxpanel &
```You probably want to use indicators, so install the plugin:```
apt-get install lxpanel-indicator-applet-plugin
```There's a configuration/customization manager for obenbox:```
apt-get install obconf
```I haven't installed an alternate file manager, but you might want to because:

If you open nautilus, it will daemonize; replace the desktop menu, and draw a background. You can **killall nautilus** to get the menu back, but the background will remain drawn. To avoid this you need to edit **/usr/share/applications/nautilus-auto-run-software.desktop**, **nautilus-folder-handler.desktop**, and **nautilus-home.desktop** were each has a line: ```
Exec=nautilus *something*
``` Change it to ```
Exec=nautilus --no-desktop *something*
``` I wouldn't advise altering nautilus.desktop, because it will affect the default desktop as well.

---

### Post by snowpine on 2012-11-25
The CrunchBang Forums Screenshot threads will give you a lot of great ideas how to customize your Openbox setup. They make a new thread each month; here's November:

[http://crunchbang.org/forums/viewtopic.php?id=22766](http://crunchbang.org/forums/viewtopic.php?id=22766)

---

