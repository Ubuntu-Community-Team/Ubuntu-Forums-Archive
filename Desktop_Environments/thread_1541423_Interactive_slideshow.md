---
title: "Interactive slideshow"
date: 2010-07-29
forum: Desktop Environments
---

### Post by malmjako on 2010-07-29
Is there a program that can show a slideshow of my photos and at the same time allow me to rate or tag photos, _during_ the slideshow?

The ideal would be if a screensaver had this functionality. I have many times happened to see a photo that I liked, or disliked, on my screensaver, but had no chance to do anything more with it. (My collection is quite big.)

---

### Post by nothingspecial on 2010-07-29
I don`t know of one exactly - but

feh will allow you save the photo currently displayed, I use it to create a directory of photos to get printed into real live photos.
```

sudo apt-get install feh
```To make a slide show

```
feh -rzF -D 5 /path/to/photos
```r makes it recursive (go through all subdirectories)
z makes it random
F makes it fullscreen
D 5 sets the time each photo is displayed to 5 seconds (you can change it to what you like)

When you see a photo you like press s and it will save it.

This is not much use if you launch feh from your photos directory as you will end up with 2 copies of the photos you like. Much better to launch it from where you want the new files to be saved and specify the path.

Type```
 man feh
``` to see all the options

Not exactly what you wanted but may be of some use.

---

### Post by malmjako on 2010-07-29
Sounds like something that can go part of the way, at least. Thanks!

---

