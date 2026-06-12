---
title: "dmenu Package"
date: 2008-05-04
forum: Desktop Environments
---

### Post by ShareBuntu on 2008-05-04
Does anyone know how to customize dmenu? As soon as I install the deb package, it launches automatically on startup. I'm looking for the file where it's launched from so I can add arguments to it. Any ideas?

---

### Post by Diabolis on 2008-07-24
> **cardinals_fan said:**
> I use the terminal for package management, downloading, writing, monitoring, and a couple other things.  I use the GUI for browsing, media playing, spreadsheets, and chess.

For all GUI users who need an easier way to launch apps, check out dmenu.  I discovered it when I used dwm, and now I can't live without it.  It's in the repos.  Install it and make a script with the following:```
#!/bin/sh
$(dmenu_path | dmenu -fn '-*-terminus-*-r-normal-*-*-120-*-*-*-*-iso8859-*' -nb '#000000' -nf '#FFFFFF' -sb '#0066ff')

```
Bind the script to your preferred key combo, and enjoy!

Don't forget to make the script executable

```
chomd +x script.sh
```

---

### Post by ShareBuntu on 2008-07-26
Thank you for the response. Any idea how to bind the created script to a key combo?

---

### Post by urukrama on 2008-07-26
What DE and window manager are you using?

---

### Post by ShareBuntu on 2008-07-26
> **urukrama said:**
> What DE and window manager are you using?

Gnome and xmonad.

---

### Post by Diabolis on 2008-07-26
1.- type this in the terminal:
```
gconf-editor &
```

A window will open that looks like a windows registry. Navigate to:
**/apps/metacity/global_keybindings/**

2.- Edit **run_command_X**, where X is the number of your choice. "Value" is the key shortcut that you want to use.
**Example: run_command_1  <Alt>F2*

3.- Now navigate to:
**/apps/metacity/keybinding_commands/**
Edit **command_X**, where X is the same number that you choose before. "Value" is the command that you want to run.
***Example: command_1 $(dmenu_path | dmenu -fn '-*-terminus-*-r-normal-*-*-120-*-*-*-*-iso8859-*' -nb '#000000' -nf '#FFFFFF' -sb '#0066ff')*

Notes:

*gnome already uses the key shortcut <Alt>F2 by default, it works for me because I modified it.

**dmenu executed only if I pasted the whole command.
It wouldn't work by trying to execute the shell script, at least I couldn't. Maybe someone knows how to correctly execute a shell script from gconf-editor.

I modified my script so it is easier to read:
[PHP]#!/bin/sh

font='-dejavu-dejavu-medium-r-normal-*-*-120-100-100-m-0-iso8859-*'
background='#FDFF00'
foreground='#000000'
selectedBackground='#0066ff'
selectedForeground='#ffffff'

$(dmenu_path | dmenu -i -fn $font -nb $background -nf $foreground -sb $selectedBackground -sf $selectedForeground)
[/PHP]

---

