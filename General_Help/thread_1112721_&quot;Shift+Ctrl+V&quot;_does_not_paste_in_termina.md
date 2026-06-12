---
title: "&quot;Shift+Ctrl+V&quot; does not paste in terminal"
date: 2009-03-31
forum: General Help
---

### Post by zigx on 2009-03-31
Hi all,

for some reason i am unable to "Shift+Ctrl+V" to paste into the terminal.  i am using intrepid with gnome.

Under Edit > Keyboard Shortcuts >Edit > Paste  i DO have it set to "Shift+Ctrl+V" 

When i attempt to paste plain text the cursor just flashes... any ideas?

FYI

This is an intrepid install using a home directory from a hardy install i had.  I know in Hardy i could paste.

Thanks.

---

### Post by Excedio on 2009-03-31
Shift+Insert will do the trick

---

### Post by drs305 on 2009-03-31
Highlighting with a mouse and middle clicking in the terminal will also work. Sorry I can't tell you why SHIFT-CTRL-V isn't working.

---

### Post by Ocxic on 2009-03-31
ctrl-shift-v does not work because the terminal captures those key combinations for things like ctrl-C,ctrl-z, etc.

when when you press ctrl-shift-v it's that termial that is capturing those commands, not gnome.

---

### Post by hikaricore on 2009-03-31
There are settings you can change to resolve this as I used this key combo in gnome.
I'm not on a gnome system at the moment so I can't tell you where they are.  sowwies.

---

### Post by drs305 on 2009-04-01
This may restore it, if the combination was inadvertently changed or corrupted:
```

gconftool-2 --type string --set /apps/gnome-terminal/keybindings/paste '<Ctrl><Shift>v'

```

---

### Post by ActiveFrost on 2009-04-01
Any ideas on how to get the same effect on "CTRL + V" ( for pasting data into terminal ) ? :)

---

### Post by drs305 on 2009-04-01
> **ActiveFrost said:**
> Any ideas on how to get the same effect on "CTRL + V" ( for pasting data into terminal ) ? :)

You would just change the code in the previous line to "<Ctrl>v". Since the code is for amending the gnome-terminal, that should do it. 

The code is a shortcut manner of making changes to settings also accessible via *gconf-editor*. Open it in a terminal with that command (no sudo required as it is for your personal settings). You can see the path to the effected area by looking at the command: /apps, gnome-terminal, keybindings.

In this case, to see if "<Ctrl>v" is already reserved, you can do a search with Edit, Find and tick/select the "Search also in key values". On a fresh Jaunty install, it did not come up with any results. Of course, if you change it and later decide you don't want it or it conflicts elsewhere, you can change it back by running the command to reset it.

---

### Post by zigx on 2009-04-21
drs305, thanks a lot!!

---

