---
title: "Change the size of the titlebar"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Skyxn3t on 2011-04-30
Does anyone know how to decrease the size of the title bar?

[http://i52.tinypic.com/10oe3k7.jpg](http://i52.tinypic.com/10oe3k7.jpg)

---

### Post by mc4man on 2011-04-30
r. click in the area you're showing as too big and uncheck tabs on top

---

### Post by Skyxn3t on 2011-04-30
> **mc4man said:**
> r. click in the area you're showing as too big and uncheck tabs on top

Thanks for the reply, but the tab section is not part of the titlebar, so that doesn't help... I'm talkinga bout the area above the tabs, which is called the titlebar.
I used firefox as an example, but all windows and apps use the same large titlebar.

Here's the titlebar I'm referring to:

[http://i53.tinypic.com/b650cg.png](http://i53.tinypic.com/b650cg.png)

[http://i51.tinypic.com/x2th1h.png](http://i51.tinypic.com/x2th1h.png)

---

### Post by Krytarik on 2011-04-30
If you find the titlebar indeed too high at any window, you can

[LIST]
[*]lower the size of "Appearance -> Fonts -> Window title font"
[*]modify the theme's Metacity settings to reduce the space around the titlebar text, for "Ambiance" you need to edit the file "/usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml"
[/LIST]
  Greetings.

---

### Post by naptastic on 2011-12-25
The specific setting you need is:

<distance name="title_vertical_pad" value="12"/>

I like to decrease the size of my titlebar font from 11 to 10, and change this value from 12 to 6. It takes 2 pixels off the height off, which makes it match my menu bars; I reduce the y-padding on those from 2 to 1.

---

