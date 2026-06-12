---
title: "Screenshots!"
date: 2007-05-10
forum: Desktop Environments
---

### Post by Sikarian on 2007-05-10
Right now, the default screenshot taking program (when I hit Print Screen) is the basic "Take Screenshot" that came with Ubuntu-Gnome.

This program sucks.  Any time I'm trying to capture from a 3d game, half the time it'll load black squares, half the time some models won't be displayed, sometimes the interface won't.  But sometimes it'll take a normal, decent screenshot.

I'm hoping to get something a little better and I was looking at KSnapshot...is there anyway I can set it so the Print Screen button captures with KSnapsnot and not with the default Gnome one?

---

### Post by taurus on 2007-05-10
Have you tried Applications -> Graphics -> GIMP -> Acquire -> Screenshot?

---

### Post by ComplexNumber on 2007-05-10
there is also desktop data manager [here]("http://data-manager.sourceforge.net/download.html"). this is one that i use.

---

### Post by bashologist on 2007-05-10
You can change it with these in your terminal:

```
[COLOR="Gray"]# To change it to ksnapshot[/COLOR]
gconftool-2 -s /apps/metacity/keybinding_commands/command_screenshot --type=string ksnapshot

[COLOR="Gray"]# To change it back[/COLOR]
gconftool-2 -s /apps/metacity/keybinding_commands/command_screenshot --type=string gnome-screenshot
```

---

