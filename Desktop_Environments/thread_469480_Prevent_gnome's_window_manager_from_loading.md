---
title: "Prevent gnome's window manager from loading"
date: 2007-06-09
forum: Desktop Environments
---

### Post by dominator22 on 2007-06-09
When I run Nautilus in AfterStep it kills AS's window manager and replaces it with gnome's.  How do I reverse--and prevent from occurring again--this behaviour?  Thanks.

---

### Post by 5-HT on 2007-06-09
> **dominator22 said:**
> When I run Nautilus in AfterStep it kills AS's window manager and replaces it with gnome's.  How do I reverse--and prevent from occurring again--this behaviour?  Thanks.

Kill off nautilus and any gnome related stuff you dont want, and start start nautilus with ```
nautilus --no-desktop
```cheers,

---

### Post by dominator22 on 2007-06-10
Thanks.  This should be a default setting.

---

### Post by mcduck on 2007-06-10
> **dominator22 said:**
> Thanks.  This should be a default setting.

No, it should not. Nautilus is Gnome's file- and desktop manager, and it sure is supposed to manage your desktop by default ;)

If you wish to run it in some environment other than Gnome just use the --no-desktop option.

---

### Post by dominator22 on 2007-06-11
> **mcduck said:**
> No, it should not. Nautilus is Gnome's file- and desktop manager, and it sure is supposed to manage your desktop by default ;)

If you wish to run it in some environment other than Gnome just use the --no-desktop option.

Is there a way to make Nautilus to run with the --no-desktop option by default?

---

