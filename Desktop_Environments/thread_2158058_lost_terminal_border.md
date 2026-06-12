---
title: "lost terminal border"
date: 2013-06-27
forum: Desktop Environments
---

### Post by jimw on 2013-06-27
I followed the instructions  involving metacity --replace, and the result was that the Unity sidebar disappeared.  After a moment of panic:confused: I shut down the computer and hit the restart option.

When Ubuntu came back up, I called up the Terminal and the border was back.

I just wanted to throw this in as my experience.  Yes, metacity worked, but it wasn't simple, it required a restart of the computer.  Or was that something a more computer-knowledgeable person would have known?

---

### Post by ajgreeny on 2013-06-27
When you ran the metacity --replace command it stopped compiz running and replaced it with metacity as the window manager.  As unity is totally dependent on compiz you lost unity, then when you rebooted compiz was again the window manager and unity ran as you had it previously.

What version of ubuntu are you using and do you want a different DE to unity, or were you simply playing around to see what happened?

---

### Post by stinkeye on 2013-06-27
...as ajgreeny said you replaced compiz with metacity.
To reload just your window decorations, using alt+F2....
```
gtk-window-decorator --replace
```
or 
to reload the window manager in Ubuntu/Unity...
```
compiz --replace
```

When running the commands in terminal add an "& disown" so the process isn't killed when
you close the terminal window.
```
gtk-window-decorator --replace [COLOR="#808080"]& disown[/COLOR]
compiz --replace [COLOR="#808080"]& disown[/COLOR]
```

---

