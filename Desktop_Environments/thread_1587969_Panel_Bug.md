---
title: "Panel Bug"
date: 2010-10-04
forum: Desktop Environments
---

### Post by AhmedSheshtawy on 2010-10-04
[SIZE="4"]Since 10.04 till 10.10 RC .. I found a bug but i don't know how to report it
Increasing the Ubuntu panel .. yup that's the bug
if you clicked on the upper or lower panel and changed the size of the panel you will find something strange ... the panel doesn't increase it's size but it adds another panel just like that[/SIZE]
[IMG]http://img413.imageshack.us/img413/181/screenshot20101004at225.png[/IMG]

[CENTER][SIZE="4"]Can anybody please verify the same bug or just report that bug to ubuntu coz really i tried to report that bug but I didn't succeeded and the new version of ubuntu is going to be released in just a few days !!![/SIZE][/CENTER]

---

### Post by Hoopz on 2010-10-04
the only way I can find to resize it is going to properties and increasing the pixel size

---

### Post by ankspo71 on 2010-10-04
Hi,
What you are seeing is a resized panel but the panel background image is duplicated. This is caused by the panel background image not being automatically resized vertically to fit the new panel size. I have always had this problem in Gnome with panels that use gradient images or other images that aren't solid colors (as far as I can remember).

If this is the Radiance theme, then the image at /usr/share/themes/Radiance/gtk-2.0/panel_bg.png needs to be edited. You can resize it and that will probably work. It is currently 1x26 pixels. If you want a 80 pixel panel, try resizing the panel_bg.png image to 1x80 pixels. Make a backup of the image first though. If you paint the image to a solid color, it wont matter on the size of the images, because any duplicated images in the panel will match.

Hope this helps.

---

### Post by AhmedSheshtawy on 2010-10-04
Great tip .. works fine
Hope Ubuntu make it auto :)

---

