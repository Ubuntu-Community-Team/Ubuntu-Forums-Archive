---
title: "Unity dash icons appear cut"
date: 2011-10-24
forum: Desktop Environments
---

### Post by typhoon_tip on 2011-10-24
Hello guys,

I have recently upgraded to Ubuntu 11.10 and using Unity as desktop, which I think is very lightweight and works extremely fast on my Lenovo T400 laptop.

I have a stupid problem tough, the Dash is displaying somewhat cut icons on the main page (I have attached a screenshot), does anyone know how could this problem be fixed ?

I am liking Unity as a desktop software, I think is very fast and very performing !

:D

---

### Post by typhoon_tip on 2011-10-24
OK, found the problem: if you set the profile to "small" in Assistive Technology under System Settings (all settings), you will get that it will use a scaling factor of 0.8 to decrease all font settings, while keeping font dimensions and styles unaltered.

When you logoff and login again, the icons of the main page of the dash will appear cut (probably it mistakenly read this setting to scale them).

By using Sdvanced Settings tool, one is able to achieve the same result for font sizes without touching the scaling factor and... voila', job done, now icons are not cut anymore and I can show Unity around to difficult "clients"...

;)

---

