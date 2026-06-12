---
title: "No title bar : IBM T30 Radeon 7500 : Intrepid"
date: 2008-12-21
forum: General Help
---

### Post by louieb on 2008-12-21
When I open **System>Preferences>Appearance>Visual Effects** and select the normal or extra option, it messages "looking for drivers" then the screen refreshes, the title bar of whatever window(s) are open disappear. Then it asks if I want to keep these setting. 

:rolleyes:Need the title bar so I click no. Any ideas? 

```

/home/lou/bin%>./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]



```

---

### Post by Agroth on 2008-12-21
Hi.
Have you got Emerald installed? I had something like that problem before and when that happened, I pressed alt+f2 and ran "emerald --replace" and it reloaded the title bar.

edit: There's also an option in CompizConfig that's called "Window Decoration", make sure it's ticked, otherwise there won't be any title bars anywhere.

---

### Post by louieb on 2008-12-21
Installed compiz setting manager. Window decorations was checked. Now I get the title bar after the refresh. But don't seem to get any visual effects.

---

