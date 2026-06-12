---
title: "Remove the &quot;squares effect&quot;, when minimizing a window without desktop-effects"
date: 2010-08-22
forum: Desktop Environments
---

### Post by peefonic on 2010-08-22
Hi,

is there a possibility to remove the ugly "squares"-effect, when minimizing a window by using no desktop-effects?

---

### Post by mcduck on 2010-08-22
Sure.

Press Alt-F2 and run "gconf-editor". Use it to browse to apps/metacity/general, and enable the "reduced_resources"-key. The ugly animation is now gone. :)

..and so are your window contents when moving a window.. Luckily there's a way to get them back while keeping the reduced_resources mode enabled: still in gconf-editor, browse to desktop/gnome/interface and enable the "accessibility"-option.

---

### Post by peefonic on 2010-08-22
> **mcduck said:**
> 
Press Alt-F2 and run "gconf-editor". Use it to browse to  apps/metacity/general, and enable the "reduced_resources"-key. The ugly  animation is now gone. :)


Thanks! That worked.

> **mcduck said:**
> ..and so are your window contents when moving a window.. Luckily there's a way to get them back while keeping the reduced_resources mode enabled: still in gconf-editor, browse to desktop/gnome/interface and enable the "accessibility"-option.

I don't understand what effect this option has. Could you describe me that?

---

### Post by mcduck on 2010-08-23
> **peefonic said:**
> Thanks! That worked.



I don't understand what effect this option has. Could you describe me that?

I've never noticed any other effect than that it allows window contents to be seen when moving a window instead of just a wireframe when you have the "reduced_resources" setting enabled.

You can safely toggle it on and off to see the effect and decide if you prefer enabling it or keeping it off.

---

