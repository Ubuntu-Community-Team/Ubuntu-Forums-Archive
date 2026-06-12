---
title: "When mounting a drive or folder how do you not show them on the desktop?"
date: 2009-04-25
forum: General Help
---

### Post by Gizim on 2009-04-25
I have a server running FreeNAS and i have about 4 shared folders how do i not get Ubuntu to put the links on the desktop when they are mounted?

---

### Post by joeyknuccione on 2009-04-25
> **Gizim said:**
> I have a server running FreeNAS and i have about 4 shared folders how do i not get Ubuntu to put the links on the desktop when they are mounted?
I prefer to use Ubuntu Tweak to turn desktop icons off. There's also a command line way, but I can't remember it.
Use Ubuntu Tweak, it's great!

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by fictivetoast on 2009-04-25
Press ALT+F2 to bring up the launch window, then type in gconf-editor.  
Desktop icons are located under apps -> nautilus -> desktop.  Just uncheck the "volumes_visible" box and they'll disappear.

---

