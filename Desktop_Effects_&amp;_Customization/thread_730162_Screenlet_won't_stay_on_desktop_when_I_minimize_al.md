---
title: "Screenlet won't stay on desktop when I minimize all windows"
date: 2008-03-20
forum: Desktop Effects &amp; Customization
---

### Post by Lantesh on 2008-03-20
Someone else asked this about a week ago or so, and it was never resolved.  I've got the same question as well.  When I hit the "Show Desktop" button on the left side of my task bar it will also minimize my screenlets.  Does anyone know how to keep the screenlets locked to the desktop?  I've tried all the different check boxes in the screenlets properties that seem applicable, but none of them work.  Any ideas?

---

### Post by MiniMe on 2008-06-27
If you are using gconf then start gconf-editor and uncheck this value:

/apps/compiz/general/allscreens/options/hide_skip_taskbar_windows

No need to set "Treat as widget" in the screenlet and no need to enable "Widget Layer" in compizConfig. Screenlets will no longer be minimized along with other windows. Worked like a charm for me anyway. 

Got it from this post: [http://forum.compiz-fusion.org/showthread.php?t=323&page=83](http://forum.compiz-fusion.org/showthread.php?t=323&page=83)

---

