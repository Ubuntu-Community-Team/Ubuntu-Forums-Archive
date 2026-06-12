---
title: "Unable to log in - Xsession errors"
date: 2016-03-26
forum: Desktop Environments
---

### Post by liste on 2016-03-26
Hello,

I'm running Ubuntu Desktop 14.04, and after some recent problems, I am unable to log into the desktop.  Here is my .xsession-errors file:

```

Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: gnome-session (Unity) main process (11233) terminated with status 1
init: unity-settings-daemon main process (11207) killed by TERM signal
init: Disconnected from notified D-Bus bus
init: logrotate main process (11090) killed by TERM signal
init: update-notifier-crash (/var/crash/libstdc++6-armhf-cross.0.crash) main process (11117) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_bin_Xorg.0.crash) main process (11121) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_lib_ibus_ibus-ui-gtk3.1000.crash) main process (11133) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_lib_ibus_ibus-ui-gtk3.1001.crash) main process (11136) killed by TERM signal
init: xsession-init main process (11200) killed by TERM signal
init: hud main process (11217) killed by TERM signal
init: unity-panel-service main process (11249) killed by TERM signal

```

I've tried a bunch of things, like running apt-get -f upgrade to update my packages, dpkg --configure -a, [COLOR=#000000]dpkg-reconfigure[/COLOR] --all (which ends with an error for initramfs-tools), but when I run dpkg-reconfigure initramfs-tools, it will usually reconfigure correctly.

Please let me know if any other information would be useful.  Thank you.

---

