---
title: "How to make a shortcut in Unity?"
date: 2011-04-14
forum: Desktop Environments
---

### Post by DonSkoD on 2011-04-14
Hello
 
Im pretty new to linux.
I have installed Opera 11.10 from a tar.gz file.
 
Can i make a shortcut to Opera in the Unity menu-pane?
Even when i search for "Opera" i find nothing.
I can access Opera from Alt+F2 -> Opera.
 
thanks

---

### Post by Copper Bezel on 2011-04-14
Are you using the new Ubuntu 11.04 or the (current stable) 10.10? The handling for shortcuts is different.

In 11.04, as I understand it, you can create a launcher for Opera, then drag and drop it onto the dock.

---

### Post by 3Miro on 2011-04-14
Start Opera and see if it shows on the Unity bar. If it doesn't show and/or it doesn't let you say right-click "keep Launcher", then you need to make a menu entry for opera and then you should be able to make a Unity shortcut.

1. Open the Terminal (search for terminal in the menu)
2. go to /usr/share/applications
```
cd /usr/share/applications/
```
3. Make a new shortcut using Firefox as template:
```
sudo cp firefox.desktop opera.desktop
```
4. Edit the new shortcut:
```
gksudo gedit opera.desktop
```
You want to change the name at the top (change it for English and any other languages that you are using).
5. Edit the **Exec** line into
```
Exec=opera %u
```
6. Might want to edit the icon, but I am not sure what the appropriate name would be (try opera, but it may not work).

Now opera should show up if you search the global menu. If not, try logout/login. Once you start it that way, you should be able to pin it to the Unity bar.

---

### Post by DonSkoD on 2011-04-15
Thanks for the tips.
 
Actually a restart did the trick (of not being able to search for the program)
And then i did what you said
- activate Opera
- right-click the program in the unity-pane -> add to launcher

---

### Post by Andre-D on 2011-06-03
how should I make an icon to a .sh file in my user folder ?
the file in in ~\folder\run.sh

- so I guess the link should be made for only my user, not everybody.

---

### Post by mc4man on 2011-06-03
> **Andre-D said:**
> how should I make an icon to a .sh file in my user folder ?
the file in in ~\folder\run.sh

- so I guess the link should be made for only my user, not everybody.
You could create a desktop launcher, the command is /path/to/scriptname, then if wanting in the unity launcher move the desktop launcher to a storage area (~/.local/share/applications/ is good place. 
After moving then D&D on to the unity launcher.
Otherwise leave on Desktop and run from there.

Or just create a basic .desktop in ~/.local/share/applications/ , the .desktop name is not important, just simple and unique is good. Then after creating drag on to unity launcher if desired.

The Name= line is the displayed name, use Icon= to set icon of choice. (icon name or full path to icon
If needed to run in a terminal  and not in script then use a line - 
Terminal=true

Ex. basic .desktop running script in terminal (terminal not in script
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=/home/doug/bin/arip7-1
Name=Mplayer Extract
Icon=

```

Or add as a quicklist entry to existing or created launcher icon (.desktop
Ex.  of not needing a terminal (or already in script
```
[MplayerExtract Shortcut Group]
Exec=/home/doug/bin/arip7-1
Name=Mplayer Extract
TargetEnvironment=Unity

```
or needing some terminal help
```
[MplayerExtract Shortcut Group]
Exec=gnome-terminal -x '/home/doug/bin/arip7-1'
Name=Mplayer Extract
TargetEnvironment=Unity
```

---

### Post by Andre-D on 2011-06-04
Thank you very much, you explained the process very well.

---

