---
title: "synaptic started in xfce4 Launcer no longer request root authentication"
date: 2014-01-10
forum: Desktop Environments
---

### Post by rwohlhueter on 2014-01-10
[Ubuntu 13.10, 64-bit, xfce desktop]
I generally have started synaptic from the xfce4 Launcher, where the behavior has been to open a window requesting root authentication, then opening the main synaptic window.  After a recent security update, that behavior has changed: now I get a messenge that synaptic has not been started with root privilege and therefore will function only very limitedly.  
Looking at the entry in the "xfce-appfinder" ,  I see that the actual launch command is "/usr/bin/synaptic-pkexe".  That command, issued from the command line, asks for root authenication (in the terminal).  Running `synaptic` from root terminal or as "su" works.
So it's just an annoyance, but one I don't understand.  Any hints?

---

### Post by Frogs Hair on 2014-01-10
I use the XFCE session and not Xubuntu and still get a password prompt no matter where synaptic is opened from. I too received and installed security updates on 1-9 but, I don't think they were XFCE specific. Launcher Command: ```
synaptic-pkexec
```

---

### Post by ajgreeny on 2014-01-10
If you look in /usr/share/applications you may find two files for synaptic; one **synaptic.desktop** file with **Exec=synaptic-pkexec** and another **synaptic-kde.desktop **(probably only if you have any kde applications installed) with just **Exec=synaptic**, the latter of the two apparently being the one you are now finding in your menu.

Perhaps the two have got muddled up somehow or other in your system.  You should be able to change back easily enough by editing your menu with a right click->Properties->Edit menu, which opens alacarte.  A **Main menu** item may also be available in the settings section of your menu if the plain xfce system is the same as Xubuntu.

---

