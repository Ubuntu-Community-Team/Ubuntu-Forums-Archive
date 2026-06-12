---
title: "Menu Bar Transparency"
date: 2010-04-24
forum: Desktop Environments
---

### Post by grammarian on 2010-04-24
[SIZE=3]Hello Everyone,

I'm fairly new to the Ubuntu world but have been simply amazed by what it can do. Someone told me to install Mac4Lin after I was done and I've done that. The desktop looks a lot more like a Mac especially after installing AWN. I do have a bit of a problem and would be very grateful for any assistance here. My taskbar is set to a background pattern which gives it the OSX look. However, towards the left side where the menu's reside, there is a bit which does not show the background pattern and instead has a dull grey color. I've been searching around for where I can tweak that bit to also have the the same pattern as the taskbar but have had no luck. Attached is a screenshot.

If anyone would be able to help me resolve this issue I would be extremely grateful. Many thanks in advance!!!
[/SIZE]

---

### Post by naja on 2010-04-24
i am not sure but it could have to do with the theme being used.try another one.

---

### Post by SoFl W on 2010-04-24
I know in regular Gnome you right click-> Properties-> Background-> Solid color-> and use the slider for transparent and opaque .

---

### Post by 3rdalbum on 2010-04-25
That's caused by the theme that you have chosen. Some themes can have the transparent Gnome menubar - take a look around.

---

### Post by stinkeye on 2010-04-25
If you go into the theme folder your using, and change the name of
panel-bg.png (usually in ~/.themes/*name of theme*/gtk-2.0/Panel)
this should solve your problem.
I usually copy and paste **panel-bg.png** into that folder and then delete the original,
so your left with **panel-bg (copy).png**

Then in properties for your panel, choose **panel-bg (copy).png** as the background image.

---

### Post by pinturic on 2010-11-04
I am having the same problem. Did you solve it

---

