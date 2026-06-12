---
title: "Cairo-dock ugly VLC icon"
date: 2009-02-17
forum: General Help
---

### Post by yonexFactory on 2009-02-17
I can't seem to change VLC's icon in Cairo-dock. I've tried the instructions [here]("http://www.cairo-dock.org/ww_page.php?p=A%20complete%20tutorial%20on%20how%20to%20customize%20your%20dock%20&lang=en") which say > To change the icon for a running application, you first have to activate "Overwrite X icons with launchers" in the Taskbar configuration options. Doing this will tell Cairo-DOck to ignore the crappy icons provided by X, and to search for a better icon... and instruct me to use ```
xprop | grep WM_CLASS
``` to find the application class. However, when I do this with VLC, all I get is ```
WM_CLASS(STRING) = "", ""
``` Can anyone offer any advice?

---

