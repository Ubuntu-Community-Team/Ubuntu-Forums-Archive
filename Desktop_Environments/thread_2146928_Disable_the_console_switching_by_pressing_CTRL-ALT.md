---
title: "Disable the console switching by pressing CTRL-ALT-F1"
date: 2013-05-20
forum: Desktop Environments
---

### Post by cccc on 2013-05-20
Hi

Howto disable the console switching by pressing CTRL-ALT-F1...F6 under LXDE?

---

### Post by 2F4U on 2013-05-20
Why would you want to do that? It may be your last option to get into the system if the desktop environment doesn't start or won't let you login.

---

### Post by epikvision on 2013-05-20
> **2F4U said:**
> Why would you want to do that? It may be your last option to get into the system if the desktop environment doesn't start or won't let you login.

Isn't console switching available on Ctrl-Alt-<F1-F7>?  Surely, having one down is ok.

---

### Post by cccc on 2013-05-20
> **2F4U said:**
> Why would you want to do that? It may be your last option to get into the system if the desktop environment doesn't start or won't let you login.

I would like to disable, because I try to create a very simple Thin Client and I don't need to switch into the system.

---

### Post by zombifier25 on 2013-05-20
**NOTE: Be very careful**
As root, in the folder /usr/share/X11/xorg.conf.d, create a new file named 50-novtswitch.conf, with its content being:
```
 Section "ServerFlags"
Option "DontVTSwitch" "true"
EndSection
```
Save, reboot.

Of course, like others have said, it may be the only way to recover your system when X fails, so consider yourself before doing.

---

### Post by cccc on 2013-05-20
> **zombifier25 said:**
> **NOTE: Be very careful**
As root, in the folder /usr/share/X11/xorg.conf.d, create a new file named 50-novtswitch.conf, with its content being:
```
 Section "ServerFlags"
Option "DontVTSwitch" "true"
EndSection
```
Save, reboot.

Of course, like others have said, it may be the only way to recover your system when X fails, so consider yourself before doing.

Thx a lot, I've done and it works well now.

---

