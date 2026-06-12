---
title: "Getting Terminal to look like conky"
date: 2007-04-11
forum: Desktop Effects &amp; Customization
---

### Post by nefarious piece of wood on 2007-04-11
I have very little experience in actual coding or constructing scripts, but I am willing to learn.

Is there a way to write a script so that the [gnome] terminal window will show up in a set location (like conky) and have the same general features of conky (customizable fonts, borders, window transparency, etc)?  

Appreciate the responses

---

### Post by invalid on 2007-04-11
This depends on the terminal you use. For example, urxvt has all this capability - see the man page for all options.

Here is a sampling of possible terminal
```
urxvt -depth 32 -fg rgb:ff/ff/ff -bg rgba:0000/0000/0000/6666 -bd rgba:0000/0000/0000/6666 -bl +sb -fn "xft:Monospace:pixelsize=11"
```

This is a borderless, custom font size, semi-transparent, opaque text terminal.

---

### Post by ashrack on 2007-07-02
devils pie is what U want.

Search around forums and U'll find the guides.

---

