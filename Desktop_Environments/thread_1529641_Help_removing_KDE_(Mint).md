---
title: "Help removing KDE (Mint)"
date: 2010-07-12
forum: Desktop Environments
---

### Post by pstap92 on 2010-07-12
I'm on Linux Mint so I would assume the instructions are the same.
I installed KDE via installing kubuntu-desktop under the synaptic package manager. It changed the loading screen to Kubuntu and to be honest, I don't really like KDE at all.

Any help would be awesome :D.

---

### Post by wookieshaver on 2010-07-12
[COLOR=#3366ff][COLOR=darkblue]I would do this: Open a terminal or console prompt from utilities and type[/COLOR][/COLOR]

[COLOR=#3366ff][COLOR=darkblue]sudo apt-get install gnome[/COLOR][/COLOR]

[COLOR=#3366ff][COLOR=darkblue]Then upon reboot on the login screen you can choose gnome as the desktop rather than kde from the bottom of the screen before logging in.[/COLOR][/COLOR]
[COLOR=#00008b][COLOR=#00008b](This is assuming the gnome-desktop was not what you started with it was it is already installed)[/COLOR]
 
[/COLOR][COLOR=#00008b]Once your in you could then remove the kubuntu-desktop using the same method you used to install it only instead of install you could choose mark for removal. [/COLOR]
[COLOR=#00008b][/COLOR] 
[COLOR=#00008b][/COLOR]

---

### Post by AceRoom on 2010-07-13
Do you want to remove KDE altogether? Or do you want to go back to GDM or do you want to change the boot splash back to the original boot splash?

Removing KDE altogether:
Open up synaptic
Mark Kubuntu Desktop environment for "Complete Removal"
Search for KDE
Remove all the packages

If you just want to change the splash screen,
Install StartUp-Manager.
That will allow you to change the splash screen.

If you want to switch back to gdm
```
dpkg-reconfigure gdm
```

---

