---
title: "Desktop clobbered during upgrade..."
date: 2014-10-11
forum: Desktop Environments
---

### Post by sambledsoe on 2014-10-11
I'm upgrading my U12.04 system (on another machine) to 14.04-- During "installing the upgrades" the installer stops and asks me if I want to keep the old, modified version of a system file (etc/default/rcs) or install the new default. It gave the option to compare the two files so I chose that, copied and pasted it into a manual log file of the upgrade. I saved the log but then accidentally hit a combination of characters (ctrl, alt or shift + some character) which made the screen jump and the launcher and taskbar disappeared. The keyboard was no longer responsive-- Alt-F2 did not bring up a terminal. The upgrade was barely started so I chose the option to replace and let the upgrade continue (it's still working).

I am unable to move windows about the screen but I can switch to the System Monitor which I happened to have running (but I can't stop it, except, maybe, by using it to kill itself). Right-clicking the screen brings up a menu with the following choices:

	Create New Folder
	Create New Document
	Organize Desktop by Name
X	Keep Aligned
	Paste (in faint lettering)
	Change Desktop Background

I can "Create New Document" which appeared on the desktop, double-click it and gedit would come up and I could see my manual log file but I can not do anything else-- how do I get the launcher back and what's going to happen to my 4+hour upgrade to 14.04? And, what key-combo did I hit to accidentally clobber the desktop? This has happened before and I simply re-booted, but I don't want to lose several hours of this upgrade. What's going on, please?

---

### Post by grahammechanical on 2014-10-11
I have no idea what happened. How could any of us have any idea of the keys you accidentally pressed? By the way we use Ctrl+Alt+T to bring up the terminal and Ctrl+Alt+F1 through to F6 to bring up a Linux command line interface (which is not the same as the terminal) and then Ctrl+Alt+F7 to get back to the desktop.

I have experienced an upgrade asking permission for accepting the replacement of a user modified Grub configuration file with a new default file. If we do not accept the Grub file being replaced by a new one we may end up with the Grub menu not loading the kernel that the upgrade brings in. Ubuntu uses Grub 1.99. whereas 14.04 uses Grub 2.0. there is a significant difference.

What can you do now? To restart Unity

```
setsid unity
```

to reset Compiz

```
dconf reset -f /org/compiz/
```

You might need to run

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

to trigger off apt-get to continue installing what has already been downloaded.

Do not forget that the upgrade from 12.04 to 14.04 also brings in newer versions of Compiz compositor/window manager and Unity and well as utilities. You may have lost Unity because the installation of the upgrade components stopped part way. Or it could have been that you switched not to a terminal but to a Linux command line console (tty)

Regards.

---

### Post by sambledsoe on 2014-10-11
Thanks,  grahammechanical, for the options-- I didn't try the ctrl-alt-Fi option but the keyboard was dead, only the mouse was working in a limited manner. My question "what key-combo...?" was because, maybe, this is some standard behavior of Ubuntu of which I am ignorant and had accidentally invoked. If not, then it is a system bug because it can (and has) result(ed) in inadvertant time and resource losing behavior. 

The upgrade eventually successfully completed, system restarted and I'm off in trusty-land, but, as I said, this has happened before and may again-- if anyone has experienced it and/or knows a work-around or solution I'd be grateful.

---

