---
title: "adding to desktop global menu dropdown"
date: 2014-04-01
forum: Desktop Environments
---

### Post by Richard J Moore on 2014-04-01
Is it possible to add to the destop global menu on/off button dropdown menu? The one with system settings, Displays, Startup Applications .... Suspend, Shutdown.

I would like to add command line/terminal option to this list in the hope I can lanch a command line to do some debugging in the 2 minutes it takes for the untity lancher and  desktop icons to appear.

Richard

---

### Post by 3rdalbum on 2014-04-01
Two minutes to log in is very strange. Unfortunately I don't know where to begin with helping you to fix it.

You can't add items to that menu as far as I know, but you might be able to launch a terminal with Control-Alt-T. And you can definitely get to a terminal with Control-Alt-F2.

---

### Post by Richard J Moore on 2014-04-02
Unfortunately at the time I want to diagnose what's causing the unity launcher to take more than 2 minutes to appear Ctrl-Alt-T is not active.  All I can do is switch to a text terminal ctrl-alt-f1. But other things available from the global menu do seem to launch.

Richard

---

### Post by RainerEL on 2014-04-02
Hi Richard,

I stored the following under ~home/.local/share/appilcations/Utilities.desktop :

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=
Name=Utilities
Icon=/usr/share/icons/Humanity/categories/48/applications-other.svg
X-Ayatana-Desktop-Shortcuts=Synaptic;UpdateManager;CompizConfig;Htop;GetUpdates;NautilusActions;GconfEditor;ForceQuit;ScreenShot;SeachFiles

[Synaptic Shortcut Group]
Name=Synaptic
Exec=gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
TargetEnvironment=Unity

[UpdateManager Shortcut Group]
Name=Update Manager
Exec=/usr/bin/update-manager
TargetEnvironment=Unity

[Htop Shortcut Group]
Name=Htop
Exec=htop1
TargetEnvironment=Unity

[GetUpdates Shortcut Group]
Name=Update Sources
Exec=getupdate1
TargetEnvironment=Unity

[NautilusActions Shortcut Group]
Name=Nautilus Actions
Exec=nautilus-actions-config-tool
TargetEnvironment=Unity

[CompizConfig Shortcut Group]
Name=Compiz Settings
Exec=ccsm
TargetEnvironment=Unity

[GconfEditor Shortcut Group]
Name=Gconf Editor
Exec=gconf-editor
TargetEnvironment=Unity

[ForceQuit Shortcut Group]
Name=Force Quit
Exec=xkill
TargetEnvironment=Unity

[ScreenShot Shortcut Group]
Name=Screen Shots
Exec=gnome-screenshot --interactive
TargetEnvironment=Unity

[SeachFiles Shortcut Group]
Name=Search For Files
Exec=gnome-search-tool
TargetEnvironment=Unity


Then I darg and drop the Utilies to the Launcher. It may be required to allow Utilities.desktop to execute. With right mouse click You see the entries.

Take a look, You can change it to the commands what ever You like.

Hope this helps and regards Rainer

---

### Post by Richard J Moore on 2014-04-03
Thanks, that's a useful technique. For the problem I was referring to it doesn't apply though I've installed this anyway. As I said it's very useful.
I was wrong when I previously stated that Ctrl-Alt-T didn't work it does. So that fixes my immediate problem. An I suspect the real culprit in making desktop startup very slow is Symantec AV.

Richard

---

### Post by Frogs Hair on 2014-04-04
14.04 will include an on/off setting in the configuration editor for the global menu. I sure it won't take long for applications like Unity Tweak to make the setting more accessible.  [http://www.omgubuntu.co.uk/2013/11/unity-trusty-global-menu-switch](http://www.omgubuntu.co.uk/2013/11/unity-trusty-global-menu-switch)

---

