---
title: "text colors in Gnome Panels???"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Efwis on 2005-10-20
has anyone tried or succeeded at changing the text for the menus in the gnome-panels??

I want to use a dark background but if I do that with the transparent panels I end up not being able to see the text. any help would be appreciated if you know how.

---

### Post by Dr. Nick on 2005-10-20
Unfortunatley the text colors are hard to change, but not impossible :)
Look here [http://www.krakoa.dk/linux-software.html#COG](http://www.krakoa.dk/linux-software.html#COG) its a program called gnome configurator, you'll have to compile it from source or use alien on a rpm file, I compiled it and it works like it says it will, its just sort of a pain IMHO. The text color is all part of the theme so the options your most concerned with in GCongi..  is theme colors. 

The toughest part about it is finding out what all fonts are affected by each selection. Just play with it and you may figure something cool out, just don't change your theme to often or get real proficient in using it. hehe

For me it made a shortcut in applications-system tools

---

### Post by Efwis on 2005-10-20
[QUOTE=Dr. Nick]Unfortunatley the text colors are hard to change, but not impossible :)
Look here [http://www.krakoa.dk/linux-software.html#COG](http://www.krakoa.dk/linux-software.html#COG) its a program called gnome configurator, you'll have to compile it from source or use alien on a rpm file, I compiled it and it works like it says it will, its just sort of a pain IMHO. The text color is all part of the theme so the options your most concerned with in GCongi..  is theme colors. 

The toughest part about it is finding out what all fonts are affected by each selection. Just play with it and you may figure something cool out, just don't change your theme to often or get real proficient in using it. hehe

For me it made a shortcut in applications-system tools[/QUOTE]
thanks, got it installed, was actually quite easy to do with alien, now i just gotta figure out how to make it work since there is no manual that I can find

---

### Post by bvc on 2005-10-20
cog won't do it, if you want a diff color from everything else

what theme? I'll see if I can figure it out. To get an idea, or try, take a look at the panel.rc in the More Than Human theme;
[http://gnome-look.org/content/show.php?content=29684](http://gnome-look.org/content/show.php?content=29684)
It will require something similar if it is even possible.```
widget_class "*Panel*GtkToggleButton" style "panelbuttons"
widget_class "*Panel*GtkButton" style "panelbuttons"


widget_class "*.Panel*Button*GtkLabel" style "panel_button_label"
widget_class "*.Panel*GtkLabel" style "panel_button_label"
```


maybe?```
widget_class "*.Panel*Menu*GtkLabel" style "panel_button_label"
widget_class "*.Panel*Menu*GtkLabel" style "panel_button_label"
```I have been able to alter the text in app menus while maintaining another color in the other menus but it wasn't fast and easy, since I'm not a gtk developer.

---

### Post by Efwis on 2005-10-21
this is what I was going for. :)

---

### Post by bvc on 2005-10-21
so that color works for everything? or did you use a panel.rc? Wha? I don't see any open apps/windows in the shot.

---

### Post by matthew on 2005-10-21
I was using a dark theme for a while. Go to gnome-look.org and try to find a theme called "Smoked Glass." It may be what you need.

Better yet...here's the link. [http://gnome-look.org/content/show.php?content=27141]("http://gnome-look.org/content/show.php?content=27141")

Here's how it looked on my computer:
[http://www.ubuntuforums.org/gallery/showimage.php?i=612&catid=searchresults&searchid=4688](http://www.ubuntuforums.org/gallery/showimage.php?i=612&catid=searchresults&searchid=4688)
[http://www.ubuntuforums.org/gallery/showimage.php?i=814&catid=searchresults&searchid=4688](http://www.ubuntuforums.org/gallery/showimage.php?i=814&catid=searchresults&searchid=4688)

---

### Post by Efwis on 2005-10-21
[QUOTE=bvc]so that color works for everything? or did you use a panel.rc? Wha? I don't see any open apps/windows in the shot.[/QUOTE]
sorry in the other fourms where I hang out they don't care about the apps as much as they do the desktop pic itself lol, here is an updated one with apps. the only issue I am finding with it is that it over rides my font colors in everything including webpages opened in FF.

---

