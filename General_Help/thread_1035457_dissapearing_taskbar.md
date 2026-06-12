---
title: "dissapearing taskbar"
date: 2009-01-09
forum: General Help
---

### Post by Jameshardy88 on 2009-01-09
hi iv'e got a problem with all of my "human" themes. Im running intrepid ubuntu with gnome. The problem seems to be localised to all of my human themes. Whenever i let my cursor drift over the taskbar (the 1 with the title of what you are on as well as the close, maximize and minimize buttons it will just grey out all of its contents. This seems to have been a problem since the install however i have not used a human theme until now.

Any and all help appreciated thanks

---

### Post by gettinoriginal on 2009-01-11
What are you using for a window decorator and window manager ??

---

### Post by Jameshardy88 on 2009-01-11
just te standard compiz, so i believe metacity (though i could be wrong) i do also have emerald installed though its not running when i experience the problem

---

### Post by gettinoriginal on 2009-01-11
Install Compiz Fusion Icon from Synaptic, from that you can pick your window manager and window decorator at will with a click of the mouse.  Compiz and Metacity are Window Managers, Emerald and Gtk are window decorators.  If you do not want to do that, you can copy/paste in terminal:
```
compiz --replace
```
or
```
metacity --replace
```
But I also recommend that if you are using compiz as your window manager that you use emerald as you decorator:
```
emerald --replace
```

---

