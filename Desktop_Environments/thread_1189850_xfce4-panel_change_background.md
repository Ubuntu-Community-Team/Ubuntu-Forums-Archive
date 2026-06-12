---
title: "xfce4-panel change background"
date: 2009-06-17
forum: Desktop Environments
---

### Post by mayacreator on 2009-06-17
Could you please tell me guys, is it possible somehow to change background in xfce4-panel v.4.6 just like it was in 4.4 version?

---

### Post by john.nicholls on 2009-06-18
How are you trying to change the background? Also are you using Compiz?

---

### Post by mayacreator on 2009-06-20
There is no possibility by default to change taskbar background(just like in Gnome) in xfce 4.6, I knew that there is so called "cairo-patch" but I do not understand how to use it?

---

### Post by Seaniesean on 2009-08-21
Change the taskbar background?  Does this work?

Create a 1 pixel by whatever width your taskbar is pixels bitmap in some sort of image editor.  Maybe you could save it in your /home/username folder with the name .BITMAP.bmp

Open /home/YOURNAME/.gtkrc-2.0 with your favourite text editor.

Mine looks like this...

gtk-icon-theme-name = "Tango"

style "panel"
{
bg_pixmap[NORMAL] = ".BITMAP.bmp"
fg[NORMAL] = "white"
}

widget_class "*Panel*" style "panel"
widget "*Panel*" style "panel"
class "*Panel*" style "panel"

Obviously replace .bitmap.bmp with whatever your background is called.

Is that what you meant?

---

