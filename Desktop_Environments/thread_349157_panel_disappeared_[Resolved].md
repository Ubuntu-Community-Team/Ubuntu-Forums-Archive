---
title: "panel disappeared [Resolved]"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Amysunoon on 2007-01-29
After log in desktop background shows as usual, but the kicker panel isn't there.
I've tried to open a console with "alt+f2" with no results. ctrl+alt+backspace allows me to reboot into a console . A search came up with "dcop kicker kicker restart "  that failed. I can launch firefox but that doesn't have the title bar so I can not close,minimize,move or resize the window.
I don't know what to try next. Much gratitude for any help.

---

### Post by ComplexNumber on 2007-01-29
go into kde control centre (type 'kcontrol' on the command line), then navigate to where you change the hiding properties (i think its in appearance -> panel -> hiding). then make it so that it DOES NOT autohide, then set it back to autohide again.

otherwise, just type in 'killall kicker'(i think its called kicker, but not too sure) in the command line.

---

### Post by aysiu on 2007-01-29
Alt-F2 ```
kicker
``` doesn't work?

---

### Post by ComplexNumber on 2007-01-30
> **aysiu said:**
> Alt-F2 ```
kicker
``` doesn't work?
i know the panel is called kicker, but i'm not sure what the actually executable  binary is called. i don't have kde on my system and i never had to call kicker from the commandline.

---

### Post by aysiu on 2007-01-30
Wait... you don't have KDE on your system? Then, it's not *kicker* you're looking for.

Try Alt-F2 ```
gnome-panel
``` then. You're using Gnome, right?

---

### Post by ComplexNumber on 2007-01-30
but he's > **aysiu said:**
> Wait... you don't have KDE on your system? Then, it's not *kicker* you're looking for.

Try Alt-F2 ```
gnome-panel
``` then. You're using Gnome, right?
but the OP is using kde. notice that eh says this:
[quote=Amysunoon].....but the kicker panel isn't there...........A search came up with "dcop kicker kicker restart "  that failed. [/quote]





aysiu,  i'm going by memory.

---

### Post by aysiu on 2007-01-30
> **ComplexNumber said:**
> but he's 
but the OP is using kde. notice that eh says this:






aysiu,  i'm going by memory.
Oh, sorry. I saw the "I don't have KDE on my system" and thought the OP wrote it. You did. Whoops.

---

### Post by Amysunoon on 2007-02-02
Thank You for all the replies! 
The command "kicker" worked, also your quick response gave me a good feeling about how this forum works
and why it's called a community.
Dan

---

