---
title: "How do I make gnome-terminal translucent under Beryl?"
date: 2006-10-27
forum: Desktop Environments
---

### Post by Kethinov on 2006-10-27
I've got Beryl installed in Edgy running with the NVIDIA 1.0-9625 beta driver's AIGLX implementation, but gnome-terminal still uses fake transparency and is unable to recognize that the Beryl window manager supports compositing. From what I've read, GNOME Terminal 2.16.1 should be able to see Beryl's compositor and use real translucency, but it doesn't. Why? How do I make it work?

---

### Post by koolatron on 2006-10-27
If I recall correctly, alt+mousewheel ought to alter the transparency for the currently focused window.  I realize what you're asking about is transparency for (only) the background; I'm not sure whether there's any option for this besides fakeparency.

---

### Post by Kethinov on 2006-10-27
According to the GNOME 2.16 release notes, gnome-terminal supports this. [http://www.gnome.org/start/2.16/notes/C/rnfrontpage.html](http://www.gnome.org/start/2.16/notes/C/rnfrontpage.html)

> 
Advanced 3D effects

Metacity, GNOME's default window manager, makes its first steps into the world of 3D accelerated desktop computing. Many extensions to its compositor engine let your windows wobble, shrink, explode, fade in and out, bounce on window focus, and show other interesting, unusual or funny effects such as having different transparency for different window types like menus, dialogs, and main windows.

Not yet enabled by default, new compositing affects are only available when Metacity is compiled with the special --enable-compositor option. The new compositing features also depend on support for the GLX_texture_from_pixmap extension, which is only available to owners of Intel i830 to i945, and ATI Radeon 7000 to 9250 chips at the present time.

&#8220;It's important to note,&#8221; says Vincent Untz, member of the GNOME release team, &#8220;that it's an ongoing work, and that more will come in 2.18&#8221;.

Once Metacity is compiled with the correct option, the effects can be turned on and off without a restart or new login, and applications can take advantage of this. For example, the GNOME terminal can now offer real transparency.


---

### Post by CatKiller on 2006-10-27
From what you just wrote: > ...The new compositing features also depend on support for the GLX_texture_from_pixmap extension, which is **only available to owners of Intel i830 to i945, and ATI Radeon 7000 to 9250 chips** at the present time...

---

