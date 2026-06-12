---
title: "How to remove gnome panel"
date: 2009-02-28
forum: Desktop Environments
---

### Post by HotelUnderSeige on 2009-02-28
Ok some people relize that the gnome panel in ubuntu is very annoying and if your like me you dont wnat it there anymore, so you wnat to get rid of it ( only suggested if you have something like AWN ), ok first push alt+f2, then in that type gconf-editor inside of it. Now in that a box should apear. Click on apps, then Gnome, then session, then required sessions. Then there should be a file called gnome-panel right click it then choose edit, then make it empty. then save it press ctrl+alt+delete, then it should not be there but if it is run killall gnome-panel, and to run it again type in gnome-panel. Hope this helped :D

[IMG]http://i229.photobucket.com/albums/ee61/HotelUnderSeige/Screenshot-98.png

---

### Post by commonplace on 2009-03-06
Thanks! This worked for me. Mine wasn't under apps/gnome/session, though, but under /desktop/gnome/session/required_components

But these instructions were close enough that I found it. This is under Intrepid (8.10).
/Kevin

---

