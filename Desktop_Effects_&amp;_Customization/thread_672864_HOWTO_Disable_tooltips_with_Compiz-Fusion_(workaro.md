---
title: "HOWTO: Disable tooltips with Compiz-Fusion (workaround)"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by Martje_001 on 2008-01-20
Hello,
This howto describes how to disable tooltips with Compiz-Fusion. The tooltips are annoying when enabeling Window Preview.

**1.** Open up *CopmizConfig Setting Manager*.[B]
2.[/B] Go to *General Options*[B]
3.[/B] Go to *Opacity Settings*
**4. **Add this value: *(name=gnome-panel & type=tooltip)* and for Opacity Value: *0*
**5.** Enjoy! The tooltips are gone (well, not really gone, they're just invisible).

---

### Post by K.Mandla on 2008-01-20
Moved to Desktop Effects and Customization.

---

### Post by ariel on 2008-05-26
> **Martje_001 said:**
> Hello,
This howto describes how to disable tooltips with Compiz-Fusion. The tooltips are annoying when enabeling Window Preview.

**1.** Open up *CopmizConfig Setting Manager*.[B]
2.[/B] Go to *General Options*[B]
3.[/B] Go to *Opacity Settings*
**4. **Add this value: *(name=gnome-panel & type=tooltip)* and for Opacity Value: *0*
**5.** Enjoy! The tooltips are gone (well, not really gone, they're just invisible).


Thanks, this basically worked for me. The panel tooltips were "erased" after a quick flash of a fraction of a second.

I fixed this flash issue by 

**1.** Open up *CopmizConfig Setting Manager*.[B]
2.[/B] Go to *Animations Plugin options*[B]
3.[/B] Select the entry with "(type=Tooltip) content
**4. **Click edit and change the value (originally 150) to 170

That was it.

---

### Post by Martje_001 on 2008-05-27
Thank you for your message! What does this do?

---

### Post by ariel on 2008-05-27
> **Martje_001 said:**
> Thank you for your message! What does this do?

In my system, following your initial instructions, tooltips in the panel still show up briefly (a fraction of a second, but still long enough to annoy). 

With the additional steps tooltips disappear for good.

---

### Post by ERICwithanH on 2008-05-31
My Compiz settings:

_General Settings : Opacity Settings_

(type=Tooltip)     0

_Animations_

...
Fade     150     (type=Notification | Utility)
Fade     278+    (type=Tooltip)

The second part in the Animations fixed the quick flash...

I guess you can press Alt+F2 and type gconf-editor and navigate to apps > panel > global and uncheck the tooltips_enabled checkbox, too, but that didn't work for me.  It did for a friend of mine, though, so maybe it'll work for you, too?

Thanks to everyone that helped me with this!

---

