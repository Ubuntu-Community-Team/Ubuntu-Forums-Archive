---
title: "Synaptic Problem after crash"
date: 2006-07-29
forum: Desktop Environments
---

### Post by diw on 2006-07-29
Yesterday I downloaded the package flashplugin-nonfree through synaptic, and after download it asked me whether to install automatically, to which I said yes.  However, there was a problem with installation and the system just hung.  An hour later I was forced to switch off!

This morning I have a system update to perform, but I can't because I get an error message 'only one software management tool is allowed to run at the same time' - 'Please close the other application either aptitude or synaptic'

As I'm not too familiar with gnome I went into 'Ksysguard' ( I have kububtu installed as well) but could not find evidence of a previous session of synaptic.  Any advice please.

---

### Post by bullgr on 2006-07-29
this hapens to me to several times...
but with the reboot it must be ok
anyway... if you just want to upgrade the system and don't search for a specific package don't use synaptic, use the terminal.

the reason is that you can break anytime you want without hanging the system, just press control-c and the operation is stopped.

to update the system from the terminal, open a console and type

> sudo apt-get update

and after the list is updated type

> sudo apt-get dist-upgrade

to update your system.

hope i help :D

---

### Post by diw on 2006-07-29
Well many thanks for this.  After running apt-get update, the process stopped with an error message telling me to run 'dpkg --configure -a'.  This then completed the installation of flash which I was having problems with last night.  Not only did it complete the installation but it returned synaptic to its working condition.  Cheers!

---

