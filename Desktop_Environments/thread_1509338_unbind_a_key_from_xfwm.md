---
title: "unbind a key from xfwm"
date: 2010-06-14
forum: Desktop Environments
---

### Post by mad_ady on 2010-06-14
Hello,

I need to send a java application the CTRL+F11 key sequence. Unfortunately, I don't seem to be able to do it from xfce, because it seems to be some default key binding.
Is there any way of sending that key combination to the application (either by removing it from XFCE, or by sending it via a command line directly to the application)?

I've looked in the Keyboard panel in Xfce settings, and there is no binding for CTRL+F11. However, if I try to add a new key binding, it says it is used by xfwm.

Thanks

---

### Post by mad_ady on 2010-06-15
I'm an idiot, I was looking in the wrong place.
Turns out CTRL+F11 was switch to workspace 11. I disabled it from Window Manager -> Keyboard: [http://www.xfce.org/documentation/4.2/manuals/xfwm4#keyboard_shortcuts](http://www.xfce.org/documentation/4.2/manuals/xfwm4#keyboard_shortcuts)

---

