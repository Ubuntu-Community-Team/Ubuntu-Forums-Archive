---
title: "terminal only apps?"
date: 2013-10-03
forum: Desktop Environments
---

### Post by RetroProf on 2013-10-03
I have a few apps which I must start from the terminal, e.g., XASTIR.  It should be possible to add these to the Dash and execute them from an icon, perhaps by writing a script and tying it to an icon from a library.  How does one do this--if it is indeed possible?  I wrote unix scripts years ago, before the days of the GUIs, but I'm relatively new to Ubuntu.  At this point I don't even know how to get a list of the apps of this type that I have installed.

---

### Post by deadflowr on 2013-10-03
This guide should help out, somewhat
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

Note that if the app needs to run in a terminal, to mark terminal = true.
If it doesn't then terminal = false.
The
```
[COLOR=#333333][FONT=UbuntuMono]gnome-desktop-item-edit ~/Desktop/ --create-new[/FONT][/COLOR]
```
command works well enough, though I personally create my own desktop files and edit them as I see fit.

The created launcher, if memory serves me, is placed in the users home folder /home/user/.local/share/applications.
To edit you can either open the text editor(gedit) and navigate to the file(you may need to enable hidden folders) or I drag the file from the file manager(home folder or files in newer versions of Ubuntu) into the gedit window.

Just make sure the file extension is .desktop, or else it'll be like any other text file.

---

### Post by RetroProf on 2013-10-03
Thanks, deadflowr.  That gives me something to chew on.

---

### Post by stinkeye on 2013-10-04
What I do is just make a quicklist entry in the gnome-terminal.desktop file.

Open gedit.
Hit the super key and search terminal and drag the terminal icon from dash and drop in the gedit window.

Then add quicklist items as shown by highlights...
```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.6.1
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
OnlyShowIn=GNOME;Unity;
Keywords=Run;
Actions=New;[COLOR="#EE82EE"]xastir[/COLOR];[COLOR="#FF8C00"]htop[/COLOR];
X-Ubuntu-Gettext-Domain=gnome-terminal

[Desktop Action New]
Name=New Terminal
Exec=gnome-terminal
OnlyShowIn=Unity

[COLOR="#EE82EE"][Desktop Action xastir]
Name=xastir
Exec=gnome-terminal -e "xastir"
OnlyShowIn=Unity[/COLOR]

[COLOR="#FF8C00"][Desktop Action htop]
Name=htop
Exec=gnome-terminal -e "htop"
OnlyShowIn=Unity
```[/COLOR]

In gedit go to** File > save as** and save to **~/.local/share/applications**

Desktop files in **~/.local/share/applications** will override the default ones of the same name in **/usr/share/applications**
Log out then back in. Drag and drop the terminal icon from the dash to the launcher 
and you should have  new right click quicklist items to launch your terminal applications.

To revert back to the default .desktop file, just remove the **~/.local/share/applications/gnome-terminal.desktop** file.

---

### Post by RetroProf on 2013-10-06
Thanks, Stinkeye.  It looks like that will solve the problem.

---

