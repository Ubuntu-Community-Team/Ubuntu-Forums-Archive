---
title: "Compiz changes mouse bindings"
date: 2006-12-03
forum: Desktop Environments
---

### Post by mklein49 on 2006-12-03
I'm having trouble running compiz. I can compile everything fine and launch compiz. However, when I run my mouse bindings change. I can only get a "normal" left click by holding the control or shift button down when I left click. The same thing happens for the right mouse button. This happens when I launch compiz and if I switch back to kwin the mouse buttons are fine. I'm not sure what's going? Any Ideas?

I'm able to run beryl fine and my mouse settings stay the same.

---

### Post by mklein49 on 2006-12-04
Well,  I found a work around.  If I run gnome-keyboard-properties and set a new us keyboard it seems to work fine.  Any ideas why this may be happening and how I can avoid having to run gnome-keyboard-properties everytime i start compiz?

Also, I noticed in my /var/log/Xorg.0.log file, XKB complains about not being able to set the keyboard map.  I had have compiled xorg 7.1 from source.  Don't know if that's related?

---

### Post by nethersole on 2006-12-25
Running "setxkbmap gb" or us in your case seems to work.

But still would like to know why this happens.

---

