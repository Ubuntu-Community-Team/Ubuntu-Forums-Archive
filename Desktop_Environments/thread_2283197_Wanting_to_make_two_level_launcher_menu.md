---
title: "Wanting to make two level launcher menu"
date: 2015-06-19
forum: Desktop Environments
---

### Post by RayTomes on 2015-06-19
I am a new Ubuntu 14.04.2 with gnome user coming from Win-XP. On windows I had set up a direct menu list from the start button (one less click than standard) with 10 items (picture, sound, text, comms, etc) with an average of 5 items in each. Already I have made the launcher icons quite small (18 pixels) and almost filled it up. Is there some way to make a two level menu like I have on windows, preferably with auto open without clicking.

Also, Ideally I can read what each one is at both levels of menu.

In a related matter, is it possible to name the disk icons in the launcher as I have 3 the same size.

---

### Post by v3.xx on 2015-06-19
What about this?

[http://www.webupd8.org/2012/08/add-stacks-to-unity-launcher-with.html](http://www.webupd8.org/2012/08/add-stacks-to-unity-launcher-with.html)

---

### Post by RayTomes on 2015-06-19
Thanks v3.xx I bought it for $2.99. The basic idea is good, However I am having trouble maing it display decently as it keeps opening the drawers with descriptions out of the window. Will persist.

---

### Post by v3.xx on 2015-06-19
It's free, it's a ppa :?  Do ppa's now charge for software?

Anyhow, I do not run the Unity desktop.  I just knew about it.  Hope it works for you.

---

### Post by CantankRus on 2015-06-20
You can manually create your own launchers with quicklists.
eg I created a launcher to run various scripts I have.
_MyScripts.desktop_
```
[Desktop Entry]
Version=1.0
Name=Scripts         [COLOR="#FF0000"]#name shown in launcher[/COLOR]
Exec=xdg-open /home/glen/scripts    [COLOR="#FF0000"]#command to run[/COLOR]
Type=Application
Icon=/home/glen/Documents/coloured_folders/scripts-folder.png   [COLOR="#FF0000"]#path to icon(google image search png...transparent background images look best)[/COLOR]
Comment=My personal scripts    [COLOR="#FF0000"]# words here will be searchable in the dash[/COLOR]  
StartupNotify=false

[COLOR="#FF0000"]# This sets the order of the Quicklist.[/COLOR] Must match the [Desktop Action [COLOR="#800080"]xxxxxxx[/COLOR]]
Actions=[COLOR="#800080"]Background[/COLOR];Brightness;Cursor;ClockToggle;Ping;Speed;Screensaver;zsync;Test.txt;TestScript;RunTest;TooltipToggle;Upper2lower;WallChanger;Reboot;separator;edit-launcher;


[Desktop Action [COLOR="#800080"]Background[/COLOR]]
Name=Background Reset       [COLOR="#FF0000"]#name shown in the quicklist menu[/COLOR] 
Exec=/home/glen/scripts/background-reset-gradient.sh     [COLOR="#FF0000"]# quicklist command to run[/COLOR]
OnlyShowIn=Unity
StartupNotify=false

[Desktop Action Whatismyip]     [COLOR="#FF0000"]# this one is not in the "Actions=" list so does not show in the quicklist menu [/COLOR]
Name=Whatismyip
Exec=/home/glen/scripts/whatismyip
OnlyShowIn=Unity

[Desktop Action zsync]
Name=Sync Daily Iso
Exec=gnome-terminal -e "/home/glen/scripts/zsync.sh"
OnlyShowIn=Unity

[Desktop Action Test.txt]
Name=Test.txt
Exec=xdg-open "/home/glen/test.txt"
OnlyShowIn=Unity

[Desktop Action Cursor]
Name=Change Cursor
Exec=gnome-terminal --geometry 100x34+303+176 -e "/home/glen/scripts/change-cursor-trusty"
OnlyShowIn=Unity

[Desktop Action TestScript]
Name=Test Script Edit
Exec=xdg-open /home/glen/scripts/aatest.sh
OnlyShowIn=Unity

[Desktop Action altyo-fix]
Name=Altyo Fix
Exec=/home/glen/scripts/altyo-fix.sh
OnlyShowIn=Unity

[Desktop Action Screensaver]
Name=Screensaver OFF/ON
Exec=/home/glen/scripts/toggle_screen_blanking.sh
OnlyShowIn=Unity

[Desktop Action Notes]
Name=Notes
Exec=xdg-open "/media/Data/Notes"
OnlyShowIn=Unity

[Desktop Action open-command]
Name=Open command in Terminal
Exec=/home/glen/scripts/xsel-terminal.sh
OnlyShowIn=Unity;

[Desktop Action RunTest]
Name=Test Script Run
Exec=gnome-terminal -e "/home/glen/scripts/aatest.sh"
OnlyShowIn=Unity

[Desktop Action ClockToggle]
Name=Clock-Toggle
Exec=/home/glen/scripts/toggle-clock.sh
OnlyShowIn=Unity

[Desktop Action TooltipToggle]
Name=Tooltip-Toggle
Exec=/home/glen/scripts/tooltips-toggle-trusty.sh
OnlyShowIn=Unity

[Desktop Action Brightness]
Name=Brightness
Exec=/home/glen/scripts/brightness.py
OnlyShowIn=Unity

[Desktop Action Reboot]
Name=XP Reboot
Exec=/home/glen/scripts/Reboot_to_Windows
OnlyShowIn=Unity

[Desktop Action WallChanger]
Name=WallChanger Random
Exec=/home/glen/scripts/wallpaper-changer-compiz-cube.sh
OnlyShowIn=Unity

[Desktop Action separator]
Name=______________________________________
Exec=
OnlyShowIn=Unity;

[Desktop Action edit-launcher]
Name=Edit Launcher
Exec=gedit /home/glen/.local/share/applications/MyScripts.desktop
OnlyShowIn=Unity;

[Desktop Action Ping]
Name=Ping Test
Exec=/home/glen/scripts/pingtest.sh
OnlyShowIn=Unity

[Desktop Action Speed]
Name=Speed Test
Exec=/home/glen/scripts/speedtest.sh
OnlyShowIn=Unity

[Desktop Action Upper2lower]
Name=Upper to Lower
Exec=/home/glen/scripts/upper2lower.sh
OnlyShowIn=Unity
```
Create the .desktop files in **~/.local/share/applications**
[ATTACH=CONFIG]262725[/ATTACH]


You can also copy an application launcher from /usr/share/applications to ~/.local/share/applications.
You can then edit this copied file to add your own quicklists.
eg I copied my /usr/share/applications/nemo.desktop file to ~/.local/share/applications
and added quicklists for nautilus and to clear recent....
_~/.local/share/applications/nemo.desktop_
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Nemo
Comment=Access and organize files
Exec=nemo %U
Icon=/home/glen/.icons/GartoonRedux/scalable/places/user-home.png
Terminal=false
Type=Application
StartupNotify=false
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Utility;Core;
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nemo
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=1.7.2
Name[en_AU]=Nemo

Actions=Nautilus;Clear;

[Desktop Action Nautilus]
Name=Nautilus
Exec=nautilus --new-window
OnlyShowIn=Unity;

[Desktop Action Clear]
Name=Clear Recent
Exec=sh -c "echo > ~/.local/share/recently-used.xbel"
OnlyShowIn=Unity;
```
[ATTACH=CONFIG]262724[/ATTACH]

---

### Post by RayTomes on 2015-06-20
> **v3.xx said:**
> It's free, it's a ppa :?  Do ppa's now charge for software?


It was in USC and had price of $2.99, but in the software itself it invites you to donate.

---

### Post by RayTomes on 2015-06-20
> **CantankRus said:**
> You can manually create your own launchers with quicklists.
eg I created a launcher to run various scripts I have.
...

Thank you CantankRus. I need to learn a bit more before I start trying to do thia, but it will be a handy reference for when I do.

---

