---
title: "Cannot Change Mouse Cursor"
date: 2010-07-27
forum: Desktop Environments
---

### Post by cpicon92 on 2010-07-27
I installed LXDE a while back just to try it out, and the first time I logged into it, it gave me a different (kind of clumsy looking IMO) mouse cursor. In the end I chose not to use LXDE, but for some strange reason, even in Gnome, I'm stuck with their cursor. I've tried changing it back in multiple appearance setting dialogs. 

Is there a way I can force the cursor to go back?

Also, I've noticed that in some apps I get the old cursor and in some I get the new one.

---

### Post by malspa on 2010-07-27
I have LXDE installed in Lucid.  The system-wide cursor theme is set in the /usr/share/icons/default/index.theme file.  For example, here's what I currently have in that file:

[Icon Theme]
Inherits=DMZ-Black

The default was:

[Icon Theme]
Inherits=DMZ-White

---

### Post by Reffner on 2010-07-27
I just use this work around:

[http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html]("http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html")

Pretty much what malspa is talking about.
EDIT - That is if you have compiz enabled.  I haven't tried it without compiz yet.

---

### Post by cpicon92 on 2010-07-27
Thank you very much for your help. I did have compiz enabled, and that did fix it.

---

