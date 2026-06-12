---
title: "simple context script hint request"
date: 2015-01-28
forum: Desktop Environments
---

### Post by Gingalone on 2015-01-28
I am trying to add a simple script to Nautilus in order to have the possibility, by a right click, to apply an image magick command to an image file... 
I wrote a simple script to reduce the image size and to rename the new file :
```

#!/bin/bash
for file in `ls *.JPG` `ls *.jpg`
do
convert -resize 20% $file small-$file
done
```
this script reduces all the images (jpg files) present in the working folder and (this is my help request) I was not able to make a script that works just on one file (the right-clicked file)...
And also I would like to put "small" at the end of the new filename (before the extension .jpg) and this looks to be a not easy task (at least for my very little bash knowledge!)...

---

### Post by CantankRus on 2015-01-28
Have a look at the 2 attached scripts.
They both work on multiple or single files and prepend the new size to the resized file.

**_[COLOR="#FF0000"]Edit[/COLOR]_**
You will also find some nautilus scripts [**_HERE_**]("https://github.com/yeKcim/my_nautilus_scripts/") that **append** the new size to the original file name.
Just adapt one of the resize scripts.

---

### Post by Gingalone on 2015-01-30
Thank you  CantankRus, I'll try your scripts!

---

