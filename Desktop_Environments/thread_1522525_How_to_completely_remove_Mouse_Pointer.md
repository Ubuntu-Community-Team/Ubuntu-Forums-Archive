---
title: "How to completely remove Mouse Pointer"
date: 2010-07-02
forum: Desktop Environments
---

### Post by brain!ac on 2010-07-02
Hi

I'm trying to make my mouse invisible permanently ,i tried to make a custom mouse cursor with lot of tutorials ,but it did not worked for me ,i tried to delete completely but i can not find how ,so if anybody can help me how to disable completely Mouse Cursor on X11 that would be great (not using unclutter) .

Best on advance

---

### Post by clrg on 2010-07-02
Why would you want to do that?

---

### Post by brain!ac on 2010-07-02
> **clrg said:**
> Why would you want to do that?

well believe me it's a very long story ,so do you know how ?

---

### Post by demosthenese on 2010-07-02
The only thing I can suggest is to install unclutter - which will remove the mouse pointer from the display when it is not moving, and unplug the mouse so it cannot move.

---

### Post by nothingspecial on 2010-07-02
Or remove xlib, modify the source code and recompile your own custom xlib.

But I wouldn`t want to do that.

---

### Post by brain!ac on 2010-07-05
> **nothingspecial said:**
> Or remove xlib, modify the source code and recompile your own custom xlib.

But I wouldn`t want to do that.

yes i agree with you (but only after i tried that :P) ,but it's not a big deal i can re-install instead of trying to fix it and i know to fix it would take much time ,but is there any other way like for ex. removing a Gnome Session component ? is the mouse Cursors a Gnome Component ?

Best on advance

---

### Post by brain!ac on 2010-07-05
Or i have another solution about that ,but still a newbie and don't know how to solve ,is there any way to make a theme package for mouse-cursors which looks like a black cube ,i mean all mouse cursor should look a simple black cube ,and so far this is not a mouse any more but only a black cube .

---

### Post by lkjoel on 2010-07-05
Or 1x1 images, or transparent GIFs or PNGs.

---

### Post by brain!ac on 2010-07-06
Well now i did ,that i could insert an transparent mouse pointer theme ,but i still have a problem ,another mouse theme is appearing at Startup which i need to make transparent also .

I`m stucket here but i hope you guy's there understand me ,because this is a project for University and i need to run a Multimedia Application at Startup where Mouse is hidden and not be seen .

---

### Post by lkjoel on 2010-07-06
You don't need to make a transparent mouse scheme to hide the mouse.
There should be a hide mouse function in the language you are using.

---

### Post by brain!ac on 2010-07-07
> **lkjoel said:**
> You don't need to make a transparent mouse scheme to hide the mouse.
There should be a hide mouse function in the language you are using.

Yes i know that ,but i can hide mouse only when my Application is active (running) but before that the mouse is controlled from GDM ,and my application is runnable at start-up but a higher runlevel than GDM !

---

### Post by CannibalZerg on 2010-07-07
**[B]Howto customize your GDM mouse cursor:**[/B]
[http://ubuntuforums.org/showthread.php?t=284915&](http://ubuntuforums.org/showthread.php?t=284915&)

---

### Post by brain!ac on 2010-07-07
> **CannibalZerg said:**
> **[B]Howto customize your GDM mouse cursor:**[/B]
[http://ubuntuforums.org/showthread.php?t=284915&](http://ubuntuforums.org/showthread.php?t=284915&)

This is what i was looking for ,thanks a lot cus u saved my life .

---

