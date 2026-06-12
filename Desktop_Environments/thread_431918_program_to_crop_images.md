---
title: "program to crop images"
date: 2007-05-03
forum: Desktop Environments
---

### Post by rkakkar on 2007-05-03
i want a simple and a small program to just crop images. any recommendations? krita and gimp are too large for the task. i'm using kubuntu. thanks! :)

---

### Post by Andruk Tatum on 2007-05-03
You would have to use wine, but you might be able to get Paint.net working.

---

### Post by bashologist on 2007-05-03
You could try imagemagick:
```
sudo apt-get install imagemagick
#More info about imagemagick here: http://www.imagemagick.org/script/command-line-tools.php

#Then you could try things like this
convert image.jpg -gravity Center -crop 50% re_image.jpg

#Maybe use a loop
for i in *; do if [ -f "$i" ]; then convert "$i" -gravity Center -crop 50% "re_$i"; fi; done
```

---

### Post by cage27 on 2007-05-03
This might help, you could try an online photo editor
[www.picnik.com:popcorn:](www.picnik.com:popcorn:)

---

### Post by Enki on 2007-05-03
Picnik looks nice, if you have the bandwith. Google's [Picasa]("http://picasa.google.com/linux/") works fine (tested on Dapper).

---

### Post by jetpeach on 2007-06-08
EDIT: i just found showfoto and it rocks for this. it's quite fast to load and is pretty much the digikam editor (as described below) but as a standalone viewer.
sudo aptitude install showfoto and you should be off...

i generally find gwenview (default opener for me) pretty useless - it does any image manipulation thru strange and cryptic kipi plugins in order to be "minimal", but it's very slow to load for me! especially when compared with windows programs like irfanview....  i am hoping this will be improved in 

but for now, i'm pretty happy with digikam - it takes a bit to load the first time but is great for storing/organizing all your photos. when i open an image in the digikam editor it opens nearly instantly and to crop you just left mouse click the area and hit control-x (or select transform->crop).  there is one default setting i changed on digikam to get the digikam "editor" to open when clicking a file, settings->conf digikam ->albums tab-> at the bottom i change click action to "start image editor".  if you don't to this, you can just hit F4 instead of clicking when on a pictures as well, that also brings up the editor (but my girlfriend isn't about to remember this so i changed my default settings...)

if you don't like the idea of using digicam for all your image stuff and just think storing photos in folders is easier, still try it - i think you may quickly see the benefits of having a program designed to store/edit/organize images...

---

