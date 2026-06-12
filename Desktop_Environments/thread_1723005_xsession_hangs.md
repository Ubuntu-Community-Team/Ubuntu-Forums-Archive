---
title: "xsession hangs"
date: 2011-04-06
forum: Desktop Environments
---

### Post by deebee40 on 2011-04-06
after logging into my ubuntu 10.10 netbook edition, I see that my gnome desktop just hangs on the background desktop screen. when i check my .xsessions i see the following errors listed below. any idea on how to fix these error messages?

gnome-session[1583]: WARNING: Unable to find provider 'mutter' of required component 'windowmanager'
gnome-session[1583]: WARNING: Unable to find provider '''' of required component 'panel'
GNOME_KEYRING_CONTROL=/tmp/keyring-ObEeS8
GNOME_KEYRING_CONTROL=/tmp/keyring-ObEeS8
SSH_AUTH_SOCK=/tmp/keyring-ObEeS8/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-ObEeS8
SSH_AUTH_SOCK=/tmp/keyring-ObEeS8/ssh
gnome-session[1583]: WARNING: Could not launch application 'bluetooth-applet.desktop': Unable to start applicat            ion: Failed to execute child process "bluetooth-applet" (No such file or directory)

(polkit-gnome-authentication-agent-1:1651): GLib-GObject-WARNING **: cannot register existing type `_PolkitErro            r'

** Message: applet now removed from the notification area
** (nm-applet:1645): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1645): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
** (update-notifier:1778): DEBUG: aptdaemon on bus: 0
** (update-notifier:1778): DEBUG: Skipping reboot required

---

### Post by deebee40 on 2011-04-07
more stuff to add, it would appear that only my ubuntu 10.10 netbook edition windows manager is affected. I am successfully able to open the standard desktop edition and in safe mode. now why won't the windows manager come up in the netbook edition?

---

### Post by Krytarik on 2011-04-07
> **deebee40 said:**
> more stuff to add, it would appear that only my ubuntu 10.10 netbook edition windows manager is affected. I am successfully able to open the standard desktop edition and in safe mode. now why won't the windows manager come up in the netbook edition?
Because Unity in 10.10 depends on Mutter, whereas the "classic" desktop depends on Metacity or Compiz respectively.> **deebee40 said:**
> 
```
gnome-session[1583]: WARNING: Unable to find provider 'mutter' of required component 'windowmanager'
gnome-session[1583]: WARNING: Unable to find provider '''' of required component 'panel'
 
```
It seems like "mutter" isn't not installed, which also affects the panel. Therefore the both error messages. Also, I'm not sure if the value for "panel" is set correctly.

Make sure that all packages needed by Unity 10.10 are installed, by reinstalling its metapackage:
```
sudo apt-get install --reinstall unity
```Greetings.

---

