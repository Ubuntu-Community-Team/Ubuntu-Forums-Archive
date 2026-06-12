---
title: "Generic app icon appearing on favorites bar"
date: 2019-05-08
forum: Desktop Environments
---

### Post by Petro Dawg on 2019-05-08
The last time I used Ubuntu regularly was back when Unity was new. I've recently come back to give Ubuntu 18.04 a try and overall I do like the streamlined feel of GNOME. But a minor unexpected thing is occurring which I don't recall happening on any other DE I've used before. When I launch Conky, a generic application icon appears on the favorites bar while it is running (circled on the attached screen shot). Is there any way to launch an application without some extraneous icon populating the bar? 

I created a custom .desktop launcher for Conky (seen above the circled generic icon) and would prefer a dot to appear next to it when Conky is running instead of an extra icon appearing, much like a dot appears near Chrome when it is running. Is that a difficult task to achieve?

[ATTACH=CONFIG]283226[/ATTACH]

---

### Post by CatKiller on 2019-05-08
> **Petro Dawg said:**
> Is there any way to launch an application without some extraneous icon populating the bar? 

Conky has *skip_taskbar* and *skip_pager* as potential values for *own_window_hints*, which will hide the Conky window from the taskbar and Alt-Tab, respectively.

> I created a custom .desktop launcher for Conky (seen above the circled generic icon) and would prefer a dot to appear next to it when Conky is running instead of an extra icon appearing, much like a dot appears near Chrome when it is running. Is that a difficult task to achieve?

You need the name of the .desktop file to be the same as the WM_CLASS of the created window.

---

### Post by Petro Dawg on 2019-05-09
Thank you very much. I had those exact values in my .conkyrc script from years ago but they were commented out (#). Its been so long that I forgot about needing those different options from time to time. However, I ended up leaving them inactive and renaming the .desktop from "Conky.desktop" to "conky.desktop" and that seemed to do the trick of putting the orange dot next to the launcher just like I wanted. I also didn't realize the WM_CLASS was case sensitive, but now I know.

---

