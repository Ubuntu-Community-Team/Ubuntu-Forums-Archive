---
title: "Xgl + compiz problem (GLX_EXT_texture_from_pixmap missing)"
date: 2006-08-03
forum: Desktop Environments
---

### Post by borgert on 2006-08-03
Hi, i'm trying to get Xgl running on my laptop (915gm graphics card) but i'm having trouble with glx eg when i try to start compiz it returns this error:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

so the first thing i did was to check glx info..
$ glxinfo | grep texture_from_pixmap
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap

seems like compiz doesn't recognize the glx extension ?

---

### Post by M3phista on 2006-08-04
hm.. don't know, but I can really recommend you this tutorial:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

works great!

---

### Post by Rever75 on 2006-08-09
Not sure if you have solved this but you should do this....
**sudo apt-get install libgl1-mesa**
Let me know if that worked for you.

---

### Post by hizaguchi on 2006-09-11
I'm having the same problem in AMD64 Edgy with fglrx.  I tried to install the libgl1-mesa package and it said it was already the latest version.  Any other ideas?

---

