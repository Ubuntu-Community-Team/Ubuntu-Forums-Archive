---
title: "Panel Transparency Help"
date: 2008-12-10
forum: General Help
---

### Post by sickpsycho on 2008-12-10
I am currently trying to make a theme more visually appealing by changing the panels and making them translucent. They use an image so I made another one with less opacity, but I have a problem: it covers most of the panel how I want it, but with certain applets (like the clock, notification area, applications-places-system menu, and some others) they still have the opaque background.

I tried making it flow by putting the opaque panel back on and lowering the opacity through compiz, but that affected the buttons also and it looks bad.

So how would I just make the image smoothly translucent? Thank you.


Also, I tried searching on the forums but couldn't find anyone with the same problem as me that was solved.

Running 8.10 w/ gnome.

---

### Post by Wartender on 2008-12-10
right-click the panel, select properties, navigate to background, use solid image and adjust the opacity

---

### Post by sickpsycho on 2008-12-10
> **Wartender said:**
> right-click the panel, select properties, navigate to background, use solid image and adjust the opacity

I can't adjust the opacity for the image, only a solid color. I'm using an image because it's a gradient and it flows really nicely.

EDIT:

That wouldn't work even if I was using a color, as the gradients behind the menu, notification area, clock, and window selector still exists. I just want to be able to change that image.

---

### Post by the yawner on 2008-12-11
That's probably due to the panel settings of the theme you're using. What theme are you using btw?

---

### Post by Andreas1 on 2008-12-12
if you want a transparent image as panel background (and not the compiz kind of transparency that affects icons and text too), you have to leave the panel background unthemed, and then set the image file in the panel properties (alternatively just drag it onto the panel. also, you can't make it stretch, so make sure it has the right size because it will be tiled)

there is no way to do what you want via the gtk theme, because this kind of pseudo-transparency is a feature of the panel, not a gtk feature.


**edit**: i think i got you wrong, you are not the themer, but using the theme, right?
for your custom panel backgrounds to work, the theme must leave the panel and (more importantly) its applets alone. go to the theme folder (that is /usr/share/themes or hidden /home/username/.themes if you dropped it into the theme manager) and open the gtkrc file of your theme. you will find a section that looks something like this:

```
# Theme panel elements
widget "*PanelWidget*" 					style "murrine-panel"
widget "*PanelApplet*" 					style "murrine-panel"
widget "*fast-user-switch*"				style "murrine-panel" # workaround for Fast User Switch applet
class "PanelApp*" 					style "murrine-panel"
class "PanelToplevel*" 					style "murrine-panel"
widget_class "*Mail*" 					style "murrine-panel"
widget_class "*notif*" 					style "murrine-panel"
widget_class "*Notif*" 					style "murrine-panel"
```

delete that section. now the panel should be plain and if you drag a transparent image file onto it everything should be transparent.

---

### Post by steveneddy on 2008-12-13
I assume that you are using Compiz, so I will post the proper way to get a transparent panel.

From my archives:

```
## Also make panel and menus transparent

Open CCSM

Go to General Settings

Go to Tab - Opacity Settings

Settings as follows:

dock 67
Menu 90
DropdownMenu 92
popupmenu 93

Link: http://wiki.compiz-fusion.org/WindowMatching
```

This should get you the desired result.

---

### Post by Andreas1 on 2008-12-14
> **sickpsycho said:**
> I tried making it flow by putting the opaque panel back on and lowering the opacity through compiz, but that affected the buttons also and it looks bad.

> **steveneddy said:**
> I assume that you are using Compiz, so I will post the proper way to get a transparent panel.

;-)

---

### Post by powerplayground on 2009-02-05
Solrry to bump this thread, but i do not see any opacity settings in the general settings in compizconfig settings manager.

---

### Post by Andreas1 on 2009-02-06
> **powerplayground said:**
> Solrry to bump this thread, but i do not see any opacity settings in the general settings in compizconfig settings manager.

is now an extra item in the accessibility section called "opacity, brightness & saturation". anyway, type "opacity" into the seach box and you should have it.

---

