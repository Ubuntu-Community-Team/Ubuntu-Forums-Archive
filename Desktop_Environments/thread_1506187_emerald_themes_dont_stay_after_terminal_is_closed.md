---
title: "emerald themes dont stay after terminal is closed"
date: 2010-06-10
forum: Desktop Environments
---

### Post by netwidget on 2010-06-10
I am new to linux and unbuntu 10.04.  I have instaled compiz fusion and emerald.  I understand through research that there is a bug in Emerald that requires the use of terminal to activate a new theme specifically typing the following text at the command line: emerald --replace.

When I do this the theme changes.  However when I close the terminal it reverts back to the gnome default theme. What do I need to do to keep the Emerald theme changes.  Previously I added the following to the start preferences: fusion-icon --no-start

Please help,  Thanks in advance

---

### Post by Peter09 on 2010-06-10
This is because when you  close the terminal you also kill emerald.
 
You need to go into Compiz-settings-manager and change the default windows decorator to emerald. I'm not at my machine at the moment so I cannot tell you exactly where this is, I think there is a section that deals with windows - its most probaly there.

---

### Post by stinkeye on 2010-06-10
You should be able to change window decorators using fusion-icon and it should persist even after a restart.

I don't think there is a bug.
Choose your emerald theme in Emerald Theme Manager and then 
activate emerald as the window decorator using fusion-icon.

---

