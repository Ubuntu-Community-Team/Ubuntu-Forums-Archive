---
title: "Unity - customise launchers"
date: 2011-04-29
forum: Desktop Environments
---

### Post by oscarBravo on 2011-04-29
I'm giving Unity a go for a while to see if it grows on me. Two questions about launching apps:

First, I used to have a launcher on the top panel to open gnome-terminal with a custom geometry, as I like my terminals larger than default and don't like to have to manually resize them. Any idea how I can customise a launcher in the new unity interface?

Second, when I had that launcher, each time I clicked it it would open a new terminal. Now when I click on the terminal icon it switches to the running terminal. I can create a new terminal window with ctrl-shift-n, but I want to be able to create one with a single click on whichever workspace I'm on. Similarly for browser windows.

Any ideas gratefully received.

---

### Post by ankspo71 on 2011-04-29
Hi,
I don't know how to set window geometry in the shortcuts themselves, but windows size options are possible by installing compizconfig-settings-manager. When you launch compizconfig-settings-manager you will find settings for "Window Rules". 

A size rule like this works for me:  (see screenshot)
class=Gnome-terminal 800 600

You will also find settings for the Unity desktop in compizconfig-settings-manager too.

---

### Post by ankspo71 on 2011-04-29
Hi,
To launch a multiple instances of the same application, click on the application icons in the unity launcher using the middle mouse button. The left click is currently reserved for exposing/presenting multiple windows of the same application. 
Hope this helps.

---

### Post by mc4man on 2011-04-29
If you only want a new 'default' terminal size then just set in the terminal's > edit > profile preferences

While the single l. click on an icon is reserved , you can add additional r. click 'quicklist' entries to do whatever you wish

that's done by editing the apps .desktop

Ex. for gnome-terminal - added 2 new quicklists, one to open a new terminal, another to open a larger terminal (added blue
This is for a laptop where the middle click is a pain at times

gksudo gedit /usr/share/applications/gnome-terminal.desktop

```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.32.1
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-terminal
[COLOR="Blue"]X-Ayatana-Desktop-Shortcuts=NewTerminal;NewLargeTerminal;

[NewTerminal Shortcut Group]
Name=New Terminal
Exec=gnome-terminal
TargetEnvironment=Unity

[NewLargeTerminal Shortcut Group]
Name=New Large Terminal
Exec=gnome-terminal --geometry=120x40
TargetEnvironment=Unity[/COLOR]
```

Can be done for any launcher icon - here is Ex. for home folder icon
[http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity](http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity)

Edit: i'll probably go back into the .desktop and adjust the 2 new Exec='s to how I have the orig. one - Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
This will keep the menu's in the terminal which I prefer, so the 2 new entries would be like 
```
X-Ayatana-Desktop-Shortcuts=NewTerminal;NewLargeTerminal;

[NewTerminal Shortcut Group]
Name=New Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
TargetEnvironment=Unity

[NewLargeTerminal Shortcut Group]
Name=New Large Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal --geometry=120x40
TargetEnvironment=Unity
```

---

### Post by fishbulb1022 on 2011-07-24
If you want to add the geometry option to the launcher, remove the old launcher, then as root, go to /usr/share/applications and edit the properties of the launcher there. Then open the dash and drag the launcher from there to the dock.

---

