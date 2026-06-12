---
title: "Xfce has stopped working in Xubuntu"
date: 2007-10-05
forum: Desktop Environments
---

### Post by tico on 2007-10-05
Hi,

I' ve been using Xubuntu for 5 months now and today, when I' ve logged in, my Xfce desktop was misconfigured. All laucher were not working and I couldn't even log out, since the logout applet and the corresponding icon in Xfce menu were not working (logout launcher was only giving me the option "quit panel", what would only close my panels). Tried to fixe it and no result. I've then logged in as root, created a new user and I've get the same result: all new users I create has the same behavior: no panel working, all Xfce stuff not working I can't even get Xfce' configuration tools: when I do in terminal " xfce-setting-show, I get the following error message:

~$ xfce-setting-show

(xfce-mcs-manager:5761): libxfce4util-WARNING **: Invalid XDG_CACHE_HOME directory `/home/zuquinha/.cache', program may behave incorrectly.

(xfce-mcs-manager:5761): libxfce4util-WARNING **: Invalid XDG_DATA_HOME directory `/home/zuquinha/.local/share', program may behave incorrectly.

(xfce-mcs-manager:5761): libxfce4util-WARNING **: Invalid XDG_CONFIG_HOME directory `/home/zuquinha/.config', program may behave incorrectly.

(xfce-mcs-manager:5761): libxfce4mcs-CRITICAL **: mcs_manager_set_string: assertion `value != NULL' failed

So, I've decided to uninstall the whole Xfce and Xubuntu metapackages, restarted the system and logged in as root using Fluxbox. I've installed Xfce4 and Xubuntu metapackages, created a new user and I was getting the same troubles.

How could I fix this? Why root user works fine with Xfce and all other users don' t?
Anhy help is really welcome.

Thanks a lot.

---

### Post by tico on 2007-10-06
Solved: there was no more free space in my home partition, so Xfce couldn't write the configuration files.

---

