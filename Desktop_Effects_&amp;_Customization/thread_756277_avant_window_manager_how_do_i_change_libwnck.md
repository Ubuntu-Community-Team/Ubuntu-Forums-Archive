---
title: "avant window manager how do i change libwnck?"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by Antonio44 on 2008-04-15
here is what the site says:

"Update SVN version no longer requires a patched libwnck! (It does however, need testers)

You will almost definatley need to build libwnck again due to one silly change you need to make in the source:

in libwnck/private.h change

#define DEFAULT_ICON_WIDTH          XX - this could be any number, most likely 32
#define DEFAULT_ICON_HEIGHT         XX

to

#define DEFAULT_ICON_WIDTH          48
#define DEFAULT_ICON_HEIGHT         48

you need to update & install libwnck with these changes before you install Awn."

How do I get to changing that number?

---

