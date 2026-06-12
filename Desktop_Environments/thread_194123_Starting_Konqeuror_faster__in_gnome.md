---
title: "Starting Konqeuror faster  in gnome?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by aLT Wizard on 2006-06-11
Hey,
Is it possible to make Konqueror start faster in gnome. I dont like nautlius and wanted to use konqueror instead but didnt want to switch completely to kde ...
Is there something like a start up script that did load all that kde needs before hand on starting ubuntu so taht Konqueror loads faster???

---

### Post by chavo on 2006-06-11
You can try running konqueror -preload. This is what it does in KDE if you set it to load a konq process on login. I don't know if it'll work but you can try it. Also with xfce there's a possibility to load kde libs, you can see what that code is doing if the above doesn't work.

Edit...
Just tried this out and it seems to work well. I added konqueror -preload to the startup list and logged in. Then I fired up konqueror and it loaded very quickly.

---

### Post by aLT Wizard on 2006-06-11
Thanks You! Works GREAT! :D

---

