---
title: "how to change nautilus windows size and colors in gnome-shell"
date: 2011-05-22
forum: Desktop Environments
---

### Post by Elie-M on 2011-05-22
No Matter what I do and change in gnome-tweak-tool, the window title bar won't change to anything else, won't go smaller, even the downloaded themes won't change the bar, and I cant seem to find the needed codes in xml to change them. anyone can help?

a photo is attached to illustrate the things  I need to change

[IMG]http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot.png[/IMG]

I need to change their size in the first place, and maybe change them to like ambiance or whatever. 

i've seen many guides on the net, and It still don't find the neeeded solution

---

### Post by Elie-M on 2011-06-01
nevermind (it's not like anyone minded though :P) to reduce the size do:


sudo sed -i "/title_vertical_pad/s/value=\"[0-9]\{1,2\}\"/value=\"7\"/g" /usr/share/themes/Adwaita/metacity-1/metacity-theme-3.xml

where u can change the "7" to a number between 0 (smallest) and 14 (biggest).

---

