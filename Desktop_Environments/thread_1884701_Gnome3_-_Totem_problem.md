---
title: "Gnome3 - Totem problem"
date: 2011-11-21
forum: Desktop Environments
---

### Post by Bobhuber on 2011-11-21
I'm using gnome3 in 11.10 with no major problems except one I can't figure out. I've changed the default theme without any problems and all of the windows reflect the new theme except Totem. It persists on maintaining the dark brown window borders etc. that comes as default (I guess) with the Adwaita theme. Changing themes makes no difference and that's the only app I've found so far that's affected.
Any help appreciated.

---

### Post by Frogs Hair on 2011-11-21
Does it make a difference if you logout and back in after making the theme selection ? 

I found one theme out of the many I have tried that wouldn't draw a skin on one application . I have noticed a need to logout and in when changing themes every now and then .

---

### Post by Bobhuber on 2011-11-21
> **Frogs Hair said:**
> Does it make a difference if you logout and back in after making the theme selection ? 

I found one theme out of the many I have tried that wouldn't draw a skin on one application . I have noticed a need to logout and in when changing themes every now and then .
Yea I've about worn the drive out rebooting LOL. The Raliegh theme will actually change the Totem skin so I figured I'd take a look at it. WRONG - Its the default theme and hard coded which I didn't know was done. Here are the statements found .
Raliegh > * This theme is the default theme if no other theme is selected.
Default > * Default keybinding set. Empty because it is implemented inline in the code.

---

### Post by Frogs Hair on 2011-11-21
I don't know whats happening . You can avoid restarts by using this in the command prompt . ```
r
```

The Alt + F2 command prompt is disabled by default in the shell , so open keyboard settings and enable it in shortcuts > system .

It's possible to check for errors in Looking Glass by entering the following in the command prompt . Use Esc to close it .```
lg
```

---

