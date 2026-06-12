---
title: "Beryl + Emerald: Can't make panels opaque"
date: 2007-09-14
forum: Desktop Environments
---

### Post by Jiawen on 2007-09-14
I'm experimenting again with Beryl + Emerald. They installed quite nicely, but I have one major problem right off: the default install of Beryl is making my panels semi-transparent when my mouse isn't directly over them. I have things running on my panels all the time, though, and I want them to be permanently 100% opaque regardless of where my mouse is. How do I make Beryl keep them opaque all the time?

I tried the "Set Window Attribs by Various Criteria" menu, and added "c:Xfce4-panel:100" to both the "Window Opacity" and "Absoloute [sic] Window Opacity" lists. Doing that made the panels opaque -- until I moused over them, at which point they went back to the same behavior as above (translucent when not focused, opaque when focused). 

Thanks in advance for any help!

---

### Post by the yawner on 2007-09-14
Right click the panel and click customize. Uncheck the option Make active panel opaque and adjust the transparency as you see fit. :D

---

### Post by Jiawen on 2007-09-14
No such option. (In case it wasn't clear, I'm using Xfce, not Gnome.)

---

### Post by the yawner on 2007-09-14
That's odd. As far as I know when you enable compositing on Xfce, those options (transparency slide and checkbox for make active panel opaque) will appear when you customize the panel.

(And yes, I know it's Xfce. I also experienced the same thing when I enabled xfwm4's compositing feature)

---

### Post by Jiawen on 2007-09-15
My mistake -- I had separators on my panel and was clicking the properties for them. It's been so long since I right-clicked on the actual panel itself that I didn't know what the properties dialog for it looked like. 

Thanks for the help!

---

