---
title: "Odd xgl/compiz problem"
date: 2006-08-24
forum: Desktop Environments
---

### Post by kbastuba on 2006-08-24
I've installed Xgl/compiz, and it mostly works, but for some reason, holding the the Alt key moves the active window to the next desktop.  Obviously this causes some trouble with certain eye candy features (e.g. transparency, desktop switching....).  Any ideas as to why this is happening and/or how to fix it?  Thanks in advance, I'm a complete linux n00b, so this is all a little over my head.

---

### Post by hseoane on 2006-08-27
> **kbastuba said:**
> I've installed Xgl/compiz, and it mostly works, but for some reason, holding the the Alt key moves the active window to the next desktop.  Obviously this causes some trouble with certain eye candy features (e.g. transparency, desktop switching....).  Any ideas as to why this is happening and/or how to fix it?  Thanks in advance, I'm a complete linux n00b, so this is all a little over my head.

I solved that problem by opening gconf-editor and editing the following parameters under apps/compiz/plugins/put/allscreens/options:
- change value for put_viewport_right_key to "Disabled"
- change value for put_viewport_left_key to "Disabled"

Don't open gconf-editor as root, because you won't see any changes in that case.

Hope that helps,
Hernan

---

