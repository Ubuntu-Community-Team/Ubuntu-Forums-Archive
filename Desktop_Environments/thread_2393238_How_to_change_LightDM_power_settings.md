---
title: "How to change LightDM power settings"
date: 2018-05-31
forum: Desktop Environments
---

### Post by rwalkerIII on 2018-05-31
Upgraded from Ubuntu 17.10 to 18.04.  Afterwards, I had the following problems:

1. GDM would not let me login as it went into a login loop (syslog for that error follows).  That was resolved with dpkg-reconfigure gdm.
May 24 18:55:38 walkubu gnome-session[3392]: No protocol specified
May 24 18:55:38 walkubu gnome-session[3392]: Unable to init server: Could not connect: Connection refused 
May 24 18:55:38 walkubu gnome-session-c[3487]: cannot open display: :2
May 24 18:55:38 walkubu gnome-session[3392]: No protocol specified
May 24 18:55:38 walkubu gnome-session[3392]: Unable to init server: Could not connect: Connection refused
May 24 18:55:38 walkubu gnome-session-c[3488]: cannot open display: :2
May 24 18:55:38 walkubu gnome-session[3392]: gnome-session-binary[3392]: WARNING: software acceleration check failed: Child process exited with code 1 
May 24 18:55:38 walkubu gnome-session[3392]: gnome-session-binary[3392]: CRITICAL: We failed, but the fail whale is dead. Sorry....
May 24 18:55:38 walkubu gnome-session-binary[3392]: WARNING: software acceleration check failed: Child process exited with code 1
May 24 18:55:38 walkubu gnome-session-binary[3392]: CRITICAL: We failed, but the fail whale is dead. Sorry....
May 24 18:55:38 walkubu gdm-x-session: session exited with status 1

2. I could now login with GDM, but my secondary monitor (dual monitors) kept going black at frequent but random intervals--even while that screen was active.  This was not acceptable, so I installed and configured lightdm.

3. With LightDM, I do not have any login loop issues or secondary monitor frequently going to black.  However, I cannot set LightDM power settings to put the monitors to sleep.  I installed LightDM GTK+ greeter configuration app, but it just dies on a SEGV as soon as it's started.  I've read the LightDM is no longer supported as of Ubuntu 17.10, but at this time GDM is not an option.  Too many problems.

How can I set lightDM power settings for the monitors?

---

### Post by kazakore on 2018-05-31
You mean on the Greater screen?

[https://askubuntu.com/questions/403859/how-to-control-lightdm-power-saving-preferences](https://askubuntu.com/questions/403859/how-to-control-lightdm-power-saving-preferences)

Otherwise it should be your DE's Power Settings....


Also light-locker I think integrates with LightDM and offers some native power saving functions. Have you got that installed as well? Although be careful, as you can end up in a mess with various programs which want to handle screen locking/screensaver functions.....

---

