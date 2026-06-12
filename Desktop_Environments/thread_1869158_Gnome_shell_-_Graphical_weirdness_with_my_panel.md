---
title: "Gnome shell - Graphical weirdness with my panel"
date: 2011-10-25
forum: Desktop Environments
---

### Post by swappa on 2011-10-25
Hi there
Decided to try out gnome shell, and, so far I am loving it. Primarily because it is a lot faster than Unity, and it fits my work-style a lot better. 

Anywho - If you look at the attachment you'll see that the left side of the upper panel looks weird. It seems to consist of several menu items. Any idea how this came to be and how it can  be fixed? 

My gnome shell version is 3.2.1 

Thanks

---

### Post by LarsKongo on 2011-10-25
Alternative 1: If you don't use icons on your desktop you can open gnome-tweak-tool and uncheck "Have file manager handle the desktop."

Alternative 2: If you don't use the global menubar in Unity you can remove the appmenu packages entirely.
*sudo apt-get remove appmenu-gtk appmenu-gtk3*

---

### Post by swappa on 2011-10-25
> **LarsKongo said:**
> Alternative 1: If you don't use icons on your desktop you can open gnome-tweak-tool and uncheck "Have file manager handle the desktop."

Alternative 2: If you don't use the global menubar in Unity you can remove the appmenu packages entirely.
*sudo apt-get remove appmenu-gtk appmenu-gtk3*

Ah. Perfect! 
Thank you so much. :D

---

