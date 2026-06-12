---
title: "Gdesklet &quot;show desktop&quot; Issue"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by k3ano on 2007-11-02
Hi, I've just installed Gdesklet and added the desklets I want.  When I click "show desktop" to minimize my windows it also minimizes my desklets, is there a way to stop this behavior?

---

### Post by eldersoares on 2008-02-03
i have the same problem!!!!! anyone?¡?¡¡?¡?

---

### Post by ted.hallberg on 2008-02-05
I had the same problem with my screenlets. I configured them as "widgets" and the problem went away..

---

### Post by Julianz on 2008-02-05
Same problem. I see the question on a lot of forums but with no answer (that works for me)
Ted, can you tell how you did configure your screelets as widgets?

---

### Post by ted.hallberg on 2008-02-06
Right click your screenlet go to "options" tab. Enable "Treat as widget".

Now, open up the CompizConfig Settings Manager and ensure that "Widget Layer" is enabled.

Now if you press F9 your screenlet will be visible on the desktop. And minimizing all windows will not affect the screenlet.

Further i have a script that simulates a press on the  F9 that i have set to be run each time i log in to my session. This way i have the screenlet autostarted.

Hope this helps !

/Ted

---

### Post by MiniMe on 2008-06-27
Better yet, if you are using gconf then start gconf-editor and uncheck this value:

/apps/compiz/general/allscreens/options/hide_skip_taskbar_windows

No need to set "Treat as widget" in the screenlet and no need to enable" Widget Layer" in compiz. Screenlets will no longer be minimized along with other windows. Worked like a charm for me anyway. 

Got it from this post: [http://forum.compiz-fusion.org/showthread.php?t=323&page=83](http://forum.compiz-fusion.org/showthread.php?t=323&page=83)

---

