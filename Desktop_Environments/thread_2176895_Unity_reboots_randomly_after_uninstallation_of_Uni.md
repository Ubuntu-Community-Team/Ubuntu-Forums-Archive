---
title: "Unity reboots randomly after uninstallation of Unity-smart-scopes"
date: 2013-09-26
forum: Desktop Environments
---

### Post by zteam2 on 2013-09-26
Hi all!

First a little description of my system specs:

> OS: Ubuntu 13.04
Videocard: Nvidia 8800 GT
Processor: Amd athon X2 4800+
RAM 4 GB

For a while ago I decided to check out unity-smart-scopes, so I followed this guide to install it:

[http://www.webupd8.org/2013/04/how-to-install-unity-smart-scopes-in.html](http://www.webupd8.org/2013/04/how-to-install-unity-smart-scopes-in.html)

```
sudo add-apt-repository ppa:ubuntu-unity/experimental-certified
sudo apt-get update
sudo apt-get dist-upgrade
```

All  things went well, but after playing around with smart-scopes for a  while, I decided to uninstall it, so I purged the ppa with ppa-purge:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-unity/experimental-certified
```
 
it  all seemed to went smooth, but now Unity restarts itself, some times.

According to the syslog compiz is crashing then it happens.

```
kernel:  [ 7672.822760] gdbus[2278]: segfault at 603392008 ip 00007fb8f4ca0339  sp 00007fb8ea317ae0 error 4 in libc-2.17.so[7fb8f4c20000+1be000]
Sep 22 14:31:52 steelhead gnome-session[2161]: WARNING: Application 'compiz.desktop' killed by signal 11
Sep 22 14:31:52 steelhead gnome-session[2161]: WARNING: App 'compiz.desktop' respawning too quickly
Sep 22 14:31:52 steelhead gnome-session[2161]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Sep 22 14:38:05 steelhead gnome-session[2161]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
```

I first tried to reset compiz according to this guide.

```
dconf reset -f /org/compiz/unity --replace & disown

```

No luck, so I tried to reconfigure compiz

```
sudo dpkg-reconfigure compiz
``` 

and got this error in response:

> /var/lib/dpkg/info/compiz.config: 1: /var/lib/dpkg/info/compiz.config: [general]: not found
/var/lib/dpkg/info/compiz.config: 2: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 3: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 5: /var/lib/dpkg/info/compiz.config: [gnome_session]: not found
/var/lib/dpkg/info/compiz.config: 6: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 7: /var/lib/dpkg/info/compiz.config: integration: not found
/var/lib/dpkg/info/compiz.config: 8: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 9: /var/lib/dpkg/info/compiz.config: profile: not found
/var/lib/dpkg/info/compiz.config: 11: /var/lib/dpkg/info/compiz.config: [general_ubuntu]: not found
/var/lib/dpkg/info/compiz.config: 12: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 13: /var/lib/dpkg/info/compiz.config: integration: not found
/var/lib/dpkg/info/compiz.config: 14: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 15: /var/lib/dpkg/info/compiz.config: profile: not found


I also tried to reconfigure some other compiz packages:

```
sudo dpkg-reconfigure compiz-core 
sudo dpkg-reconfigure compiz-gnome 
sudo dpkg-reconfigure compiz-plugins-default 
```

Removing and creating a new user didn't work either.

Is there anything else besides to, boot up with a live-usb of Ubuntu 13.04 and perform a repair-installation I can do?

Best regards Zteam :P

---

