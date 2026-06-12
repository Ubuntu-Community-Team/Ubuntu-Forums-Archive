---
title: "ReEnabling A ToolBar, The X Button One?"
date: 2009-05-08
forum: Desktop Environments
---

### Post by djoe on 2009-05-08
**OpenSuse**

I think I may have messed around a particular setting.

Because I don't have the Windows Bar that shows the Close ([COLOR="Blue"]**X**[/COLOR]) button, Maximize ([COLOR="Blue"]**[]**[/COLOR]) Button and the Minimize ([COLOR="Blue"]**_**[/COLOR]) Button

I've been trying hard to find the setting, but, can't find it.

---

### Post by sarutv on 2009-05-08
djoe, I am not sure which desktop environment you are running. Do you still have this issue if you restart. If so this is most likely caused by your window manager failing to paint the Window Decorations including the title and the "X Button toolbar".

As an interim solution you could "Alt + Right Click" on a window that you are interested in and choose "Maximise", "Close", etc from Window popup menu.

---

### Post by sarutv on 2009-05-08
Actually, the solution from [this FAQ thread]("http://ubuntuforums.org/showthread.php?t=809695") might be the solution you are looking for:

[INDENT]**Where did my window borders go?**
    This is a common mistake caused by disabling some plugins in CompizConfig Settings Manager. To fix, open the manager (System > Preferences > CompizConfig Settings Manager) and find the "Window Decorations" plugin. Check the box and you're all set.[/INDENT]

---

### Post by djoe on 2009-05-09
As I said above its OpenSuse, and as for environment its a Gnome type.

Yes, when I restart the issue still shows up.

But, I'll try your suggestion.

---

### Post by djoe on 2009-05-13
Ok, I found out that the Animation Settings were Disabling The Window Border.

It claims that my Hardware doesn't support or can't handle Animation, including that cool Desktop Cude.

---

