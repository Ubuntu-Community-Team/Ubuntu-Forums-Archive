---
title: "upgrade to 14.04, click to raise window fails in unity"
date: 2014-12-25
forum: Desktop Environments
---

### Post by syrag on 2014-12-25
Yes, the title is nearly an exact copy of previous thread, because I have the exact same problem and there was no solution: In Unity left click on the title bar does not raise the window. On 12.04 it did, and if I use the gnome desktop it works as well.
Is there a setting somewhere where I can set this behavior? Or is there a package that was improperly upgraded? I want the window to come to top when I click on the title bar (left, middle or right; I really don't care) without any modifiers. (Why should I have to use the keyboard and the mouse, when just the mouse alone used to work fine, and in gnome, still does?)

Thanks for your help.

---

### Post by CantankRus on 2014-12-25
Install compizconfig-settings-manager and open...
ccsm > general options > focus and raise behaviour

You can also rest unity/compiz with...
```
dconf reset -f /org/compiz/
```
Log out and back in.

---

### Post by syrag on 2014-12-25
You mean 'raise on click'. I've tried it in the past, and wasn't quite satisfied with the way it worked. For example, I can't resize or move windows without bringing them to the front. I would prefer the window to raise *only* if the title bar is clicked, as in gnome. I'll try it again and see  interferes with my work flow.
In the meantime, I'd appreciate any other answers.

Thanks again.

Edited to add: After enabling and then disabling 'raise on click' I can now middle-click on the title bar and it raises the window. This persists after logging out and back in *as long as there are only two windows open*. If there are three or more the behavior seems to be that the clicked window will be moved under one of the windows, but never brought to the top. I think there is a bug here somewhere.

---

### Post by CantankRus on 2014-12-25
The compiz Unity plugin now draws window decorations instead of **gtk-window-decorator**
so probably wont get back to previous behaviour.

---

### Post by CantankRus on 2014-12-25
> **syrag said:**
> 
Edited to add: After enabling and then disabling 'raise on click' I can now middle-click on the title bar and it raises the window. This persists after logging out and back in *as long as there are only two windows open*. If there are three or more the behavior seems to be that the clicked window will be moved under one of the windows, but never brought to the top. I think there is a bug here somewhere.
It actually lowers on middle click.
You can set up something like Super+mouse1 to raise a window in ccsm as shown.

---

### Post by syrag on 2014-12-26
I remember seeing somewhere that the default behavior was to lower the window, that's why I thought there was a bug somewhere. After a reboot it still raises the window on a middle click, as long as there are only two open. More than two, it lowers it.

I have raise on click + super enabled, but I was hoping to do it with just a mouse click, as in 12.04. I know it's little thing, but it is just annoying enough that I'll probably be switching to gnome. I wasn't aware of how often I use this until I didn't have it.

Thanks again for your time.

---

