---
title: "Broken keyboard short cuts"
date: 2012-06-20
forum: Desktop Environments
---

### Post by hwychld on 2012-06-20
Some of my keyboard shortcuts have stopped working - like ctrl-alt-L to lock the screen.  I have tried recreating the shortcut via the keyboard settings but no luck.  I have tried changing the shortcut to something else but no luck.  

Any ideas how to fix this?  What config file holds the keyboard shortcut mappings?

Thanks in advance.

---

### Post by LinXNut on 2012-06-20
I'm sorry I'm not sure how to fix this, but I know the keyboard configs are located somewhere in the X11 folder.
```
/usr/share/X11/xkb
```Also I found this site which *may* help. [Link]("https://help.ubuntu.com/community/Howto:%20Custom%20keyboard%20layout%20definitions")

---

### Post by hwychld on 2012-06-21
Thanks for the reply LinXnut.  I have looked through those directories and it seems like they are for keyboard layout, and assigning special characters to keys.  It seems like what I need would be an abstraction layer (or two) up.  I didn't see anything in those files for the keyboard shortcuts.  I do appreciate the info, learned a thing or two poking around in there.

Anybody have any idea what config file keyboard shortcuts (like ctrl-alt-L to lock the screen and ctrl-t for a terminal window) are stored in?

---

### Post by LinXNut on 2012-06-21
Actually another thing you could try is "Gconf-editor"? Type these in a terminal.

```
$ sudo apt-get install gconf-editor
```After installing, type:

```
$ gconf-editor &
```1.) Double click apps.
2.) Go down to "metacity", and double click.
3.) Open "Keybinding_commands"

I have never used this before, but this may help your situation. :popcorn:

---

### Post by hwychld on 2012-06-21
I will give it a shot.  I already have the gconf-editor installed but didn't know it had keybinding stuff in it. Thanks again.

---

