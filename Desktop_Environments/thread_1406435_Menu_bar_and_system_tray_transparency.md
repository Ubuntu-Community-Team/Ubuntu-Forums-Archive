---
title: "Menu bar and system tray transparency"
date: 2010-02-14
forum: Desktop Environments
---

### Post by Richard1979 on 2010-02-14
See pic:
[http://www.digit4l.net/content/images/forum/Menus.jpg](http://www.digit4l.net/content/images/forum/Menus.jpg)
(parts censored for obvious reasons)

I've managed to get my main menus to have transparency and it looks great, same deal with the shortcut bar - but the main menu (Applications Places System) and the system tray area are a solid color and I can't see how to edit them.

Any ideas?

---

### Post by moongia on 2010-02-14
In my ccsm under ''opacity,brightness and saturation adjustments''under ''windows specific settings'' I hit new and added ''name=gnome-panel'' w/o quotes. It worked for me I hope it helps

---

### Post by Richard1979 on 2010-02-14
> **moongia said:**
> In my ccsm under ''opacity,brightness and saturation adjustments''under ''windows specific settings'' I hit new and added ''name=gnome-panel'' w/o quotes. It worked for me I hope it helps

Amazing, it worked.
Thank you.

I now have a desktop that will make my Windows 7 mates go "WTF how?"

---

### Post by moongia on 2010-02-14
No prob.

---

### Post by Richard1979 on 2010-02-14
Looking really good now, woohoo:
[http://www.digit4l.net/wp-content/uploads/2010/02/DesktopTransparency.jpg](http://www.digit4l.net/wp-content/uploads/2010/02/DesktopTransparency.jpg)
Take that Windows!

---

### Post by moongia on 2010-02-14
LoL I dig the wallpaper..Glad  to help.

---

### Post by kelvin spratt on 2010-02-14
you extend it like this
name=gnome-panel | type=Menu | tooltip |  PopupMenu | DropdownMenu,  set you opicaty to what ever, or you can separate, them for individual settings.

---

### Post by moongia on 2010-02-14
Thanks,I'm good to go.

---

### Post by vgrisham on 2010-05-17
How do you do this in Lucid? I've added the window setting in ccsm, but the text and icons all disappear as well.

---

### Post by rude_lee on 2010-06-09
yeah me too does not seem to work any help please people

oh i get it

name=gnome-panel | type=Menu | tooltip | PopupMenu | DropdownMenu

and the value raise it above 70 and u should see everything working... so easy 
thanks this is hot

---

### Post by Timmer1240 on 2010-06-09
Thanks alot!Was wondering how to do this awhile back and stumbled on to this thread it really pays to visit the forums Often!Thanks for the info and Keep Ubuntuing!

---

### Post by XsilverX on 2010-06-25
[IMG]http://i741.photobucket.com/albums/xx51/XsilverX90/Screenshot.png[/IMG]
loged as root navigat to file system/usr/share/themes 
is you are using ambiance go to ambiance folder or if you are using radiance go to radiance folder once in there open the folder named "gtk-2.0" and open the file called "gtkrc" with gedit (as root)
find the line: 
bg_pixmap[NORMAL] = "panel_bg.png"  

and put a # before it leaving it like this: 

# bg_pixmap[NORMAL] = "panel_bg.png" 
(with a space between the # and the text)

save it, restart your computer and then right click your panel go to background and select solid color 

thats all ;D hope it works for you  
(this only works with the ambiance and radiance theme)

---

