---
title: "Change color of notification area icons"
date: 2009-12-21
forum: Desktop Environments
---

### Post by werdna5225 on 2009-12-21
The default notification area icons are grey, but I would like to change their color.  I used gnome color chooser to change the color of all the other colors on my panel, but I cannot seem to get the notification area to change colors.  I tried following this thread's advice:

[http://ubuntuforums.org/showthread.php?t=1289784]("http://ubuntuforums.org/showthread.php?t=1289784")

but it didn't change anything.  I think it may have something to do with the fact that the code:```
include ".gtkrc-2.0-gnome-color-chooser"
``` is showing up first in the file?  Does anyone know how to change the icons color with or without gnome color chooser?

---

### Post by werdna5225 on 2009-12-22
I have found that ```
include ".gtkrc-2.0-gnome-color-chooser"
``` points to a file with that name and this is where gnome-color-chooser stores theme information.  I tried adding the ```
style "panel"
{
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
``` to the file but I still couldn't get the icons to change colors.  Does anyone have any ideas how to change the icons in the notification area to a different color?

---

### Post by VCoolio on 2009-12-22
Maybe post a screenshot of what you have and what you want it to be. The solutions you tried apply to your gtk theme, that's only the background color of the notification area itself and text colors. For that also check [here]("http://ubuntuforums.org/showthread.php?t=1333739"). From your problem description I deduce you're trying to modify icon colors; in that case you probably need to modify your icon theme.

---

### Post by werdna5225 on 2009-12-22
Here is what my panel currently looks like:

[[IMG]http://www.mediafire.com/imgbnc.php/06134966ffbb41f5ac731c328ef126dc2g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=mm3tnh2ctwn&thumb=5)

and this is basically what I want the notification icons to look like:

[[IMG]http://www.mediafire.com/imgbnc.php/4ffe025206f0afa164b0b0c16bdf767e2g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=ytymt2mho23&thumb=5)

I don't necessarily have to change the color of the blue icon, but  I would like to somehow make all the others show up white.

---

### Post by VCoolio on 2009-12-22
I see; that's about icon theme then I think; try to change to another icon theme first to be sure. Search your icon theme (/usr/share/icons or ~/.icons) for those icons and replace them; you can skip the actions, apps and mimetypes folders (which are by far the biggest), they shouldn't be in there.

---

### Post by werdna5225 on 2009-12-23
Thank you! It was the icon theme that needed changed.  I found a them called Magog White 9.1 that is close to what I wanted.

---

