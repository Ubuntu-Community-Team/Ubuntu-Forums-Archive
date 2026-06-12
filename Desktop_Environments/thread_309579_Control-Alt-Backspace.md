---
title: "Control-Alt-Backspace"
date: 2006-11-29
forum: Desktop Environments
---

### Post by Canordis on 2006-11-29
I have a habit of switching virtual desktops on Gnome with the familiar C-M-Direction accelerator. This, however, tends to put my hands inadvertently on the Control and Alt keys, often when I'm backspacing something and killing my X server accidentally in the process. Yes, I'm a dolt. ](*,) 

Question is, is there a solution for this? A way of changing control-alt-backspace to something else, or of using a different key as a modifier (I'd love to use the Windows key for workspace switching and related nonsense, but it doesn't seem to be usable as a modifier... help?) I'm about to start changing all my control-alts to control-shift. :-|

---

### Post by jpkotta on 2006-11-29
I think the only way to get access to "Windows Key" as a modifier is xmodmap.  The traditional name for this key is "Super".

Put this in your ~/.xsession file and it should map Super to modifer 4, then you can use it in Gnome key settings and it should come up as <Mod4>.  The most important line is the last.  You can test this by simply running the commands in a terminal, ~/.xsession simply sets them automatically when you log in.

```

xmodmap -e "clear mod4"
xmodmap -e "add mod4 = Super_L Super_R"

```

Bonus:  Do you hate caps lock?  Do you think it's useless, and even worse, gets in your way?  I do, that's why I disable it:

```
xmodmap -e "remove lock = Caps_Lock"
```

---

### Post by jpkotta on 2006-11-29
[https://help.ubuntu.com/community/MappingWindowsKey](https://help.ubuntu.com/community/MappingWindowsKey)

---

