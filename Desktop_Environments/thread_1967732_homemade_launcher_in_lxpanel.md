---
title: "homemade launcher in lxpanel"
date: 2012-04-28
forum: Desktop Environments
---

### Post by dawnlove on 2012-04-28
I've managed to make a launcher in /usr/share/applications. (lubuntu 11.4) to open/close optical drive. But it will only work if you open "/usr/share/applications" and click on it. It does not show up in menu and of course I can't choose it in lxpanel. Any help would be great

this is my launcher
> [Desktop Entry]
Name=eject 
Type=Application
Comment=eject close
Icon=/home/dove/icons/eject.png
Exec=eject 
Exec=eject -T
Categories=Utility;
#NoDisplay=true


---

### Post by MG&amp;TL on 2012-04-28
[http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html#category-registry](http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html#category-registry)

"Utilities" should be "Utility"-should now show up in 'Accessories'.

---

### Post by dawnlove on 2012-04-28
> **MG&TL said:**
> [http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html#category-registry](http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html#category-registry)

"Utilities" should be "Utility"-should now show up in 'Accessories'.

I believe I had that right and it didn't show up in 'Accessories"

---

### Post by Dennis N on 2012-04-28
Suggestions:

Use full path to the executable after "Exec="
Have only one "Exec=" line.

---

### Post by dawnlove on 2012-04-28
> **Dennis N said:**
> Suggestions:

Use full path to the executable after "Exec="
Have only one "Exec=" line.
would that look like?
"Exec=eject && eject -T"?

the launcher works great from "/usr/share/applications" with two "Ejects" it just won't show up in menu

---

### Post by dawnlove on 2012-04-28
> **dawnlove said:**
> would that look like?
"Exec=eject && eject -T"?

the launcher works great from "/usr/share/applications" with two "Exec=" it just won't show up in menu
to get launcher to both open and close I need two Exec='s

---

### Post by Dennis N on 2012-04-28
I'm thinking Two Exec lines may not conform to the .desktop file specification, and that possibly is why it's not showing up in the main menu. 

From the specification:

> The Exec key must contain a command line. A command line consists of an executable program optionally followed by one or more arguments

Exec=<path to executable>Name <optional arguments>

---

### Post by Dennis N on 2012-04-28
> **dawnlove said:**
> to get launcher to both open and close I need two Exec='s

You did make a shell script, right?

Exec= should be followed by the path to and name of the shell script.

The script itself would contain your eject and eject -T commands.

---

### Post by dawnlove on 2012-04-28
> **Dennis N said:**
> You did make a shell script, right?

Exec= should be followed by the path to and name of the shell script.

The script itself would contain your eject and eject -T commands.

a little over my head (shell script) although [http://www.freeos.com/guides/lsst/ch02sec01.html](http://www.freeos.com/guides/lsst/ch02sec01.html)
makes it seem like I could. the problem with this when I make my launcher with only one "Exec=" it still doesn't show in menu ether and my (two Exec)launcher will work from "/usr/share/applications"

---

### Post by Dennis N on 2012-04-28
Tested this and it shows up in the menu (accessories):

```
[Desktop Entry]
Type=Application
Icon=shellscript
Name=Ejector
Comment=Eject a CD	
Categories=Utility;
Exec=eject
StartupNotify=true
Terminal=false
```

and works to open the tray. Adding the second "Exec=" did nothing - it was ignored. 

I saved it as ejector.desktop in ~/.local/share/applications/

If it was more complex, a shell-script would be in order, but eject is a built in command so it works anyway.

Good Luck.

---

### Post by JC Cheloven on 2012-04-28
> **dawnlove]to get launcher to both open and close I need two Exec='s [/quote] You shouldn't: the command "eject -T" is supposed to open the tray if it's closed and vice-versa.

[QUOTE=dawnlove said:**
> I've managed to make a launcher in /usr/share/applications. (lubuntu 11.4) to open/close optical drive. But it will only work if you open "/usr/share/applications" and click on it. It does not show up in menu and of course I can't choose it in lxpanel. Any help would be great
this is my launcher 
[Desktop Entry]
Name=eject
Type=Application
Comment=eject close
Icon=/home/dove/icons/eject.png
Exec=eject
Exec=eject -T
Categories=Utility;
#NoDisplay=true

Your above .desktop file works nicely for me, with only one Exec:
```

[Desktop Entry]
Name=eject
Type=Application
Comment=eject close
Icon=/home/jc/kk/mete-saca.png
#Exec=eject
Exec=eject -T
Categories=Utility;
#NoDisplay=true 
```
Apart from the evident icon change, my file is /usr/share/applications/eject.desktop, the owner is set to root, and the permissions are rw for the ownwer, nothing for everybody else. And not executable.
The icon appears in my lxde menu (using lubuntu 11.04 here), under accesories, and works nicely as expected. Hope some detail in the above will help you.

Anyway: if you want to have this function at hand, ¿shouldn't be better to assign it to a keyboard shorcut? In Lubuntu you have to edit manually a file for that, which is ```
~/.config/openbox/lubuntu-rc.xml
```. I think you'll figure out how to do it looking at other shorcuts (look for "<keyboard>" in that file). If you like the idea and have any trouble, please come back to ask ;)

JC

---

### Post by dawnlove on 2012-04-29
> **Dennis N said:**
> Tested this and it shows up in the menu (accessories):

```
[Desktop Entry]
Type=Application
Icon=shellscript
Name=Ejector
Comment=Eject a CD	
Categories=Utility;
Exec=eject
StartupNotify=true
Terminal=false
```

and works to open the tray. Adding the second "Exec=" did nothing - it was ignored. 

I saved it as ejector.desktop in ~/.local/share/applications/

If it was more complex, a shell-script would be in order, but eject is a built in command so it works anyway.

Good Luck.

 Many thanx your desktop entry showed up in my menu but did not close drive until I added a the second "Exec="? see below

> [Desktop Entry]
Type=Application
Icon=/home/dove/icons/eject.png
Name=Ejector
Comment=Eject a CD	
Categories=Utility;
Exec=eject
Exec=eject -T
StartupNotify=true
Terminal=false

many thanx again

---

### Post by dawnlove on 2012-04-29
screenshot of my lxpanel
[http://dl.dropbox.com/u/40074872/2012-04-29-093639_1920x1080_scrot.png](http://dl.dropbox.com/u/40074872/2012-04-29-093639_1920x1080_scrot.png)

---

