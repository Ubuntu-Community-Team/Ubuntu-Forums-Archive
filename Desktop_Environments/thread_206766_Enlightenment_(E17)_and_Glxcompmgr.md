---
title: "Enlightenment (E17) and Glxcompmgr"
date: 2006-06-30
forum: Desktop Environments
---

### Post by cocoapunk on 2006-06-30
Hi, I'm having a problem with Glxcompmgr in E17. I have compiz running in gnome perfectly fine, but gnome looks like trash, and the cube in e17 would be amazing. I compiled glxcompmgr fine and tried running in the LD_Library terminal, but this is what I consistently get:
]$ /opt/fdo/bin/glxcompmgr
/opt/fdo/bin/glxcompmgr: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/opt/fdo/bin/glxcompmgr: pixmap 0x1200041 can't be bound to texture
/opt/fdo/bin/glxcompmgr: Couldn't bind redirected window 0x6003f3 to texture
/opt/fdo/bin/glxcompmgr: pixmap 0x1200043 can't be bound to texture
/opt/fdo/bin/glxcompmgr: Couldn't bind redirected window 0x60013c to texture
/opt/fdo/bin/glxcompmgr: pixmap 0x1200045 can't be bound to texture
/opt/fdo/bin/glxcompmgr: Couldn't bind redirected window 0x600003 to texture

I'm guessing its not my xorg.conf...seems more like a e17 problem, but I'm not really sure.

Any help is appreciated :)

---

