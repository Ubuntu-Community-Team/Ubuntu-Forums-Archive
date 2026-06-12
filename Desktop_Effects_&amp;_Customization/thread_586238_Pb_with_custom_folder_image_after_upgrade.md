---
title: "Pb with custom folder image after upgrade"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by SoPa on 2007-10-22
Hi All,

I have a problem with some customized folders since I've upgraded to Gusty.
I cannot explain it, I tried to assigned a different name to the image file, copy it, move it, move the folder, etc... but instead of the image, I see the gnome default white paper icon (the one you see if the original icon assigned to a file goes missing).

If I assigned another image to my folder, it works fine. It seems to be a problem with some files only, but they are not using any specific characters in their name (neither in the folders name), they are shown properly as thumbnails and are not corrupted.

I really don't get it. Is anyone else is having this problem? It looks so random, I cannot think about as reason why it would happen. On Feisty, they show properly before.

Any advice is appreciated,

SoPa

---

### Post by sonic1980 on 2007-10-22
I have the same problem with a fresh 7.10 installation

It seems that I cannot customize a folder image with a big image. With small JPGs or PNGs works great but if i try to assign a big JPG (more than 500 KBytes) the nautilus file explorer shows a blank paper as folder icon.

Is there any way to correct this? I had no problems with ubuntu 7.04.

A workaround is to resize the image with Gimp (1280x960 to 400x300, for example) and store it in the same folder (or where you want) with the name ".thumb.jpg" (this is optional). And then use this image to customize the folder.

---

### Post by SoPa on 2007-10-22
Sonic1980, you are right, the size does matter here.

I thught about this but actually one of the folder image is less than 300KB (272KB to be exact) and it still didn't show up. After reading your comment, I've reduced the quality of the picture and went down to less than 100KB and it show up properly (no need for a Nautilus restart or anything like that).

Well, I will just have to make smaller copies of the current pictures I'm using then.

Thanks...

BTW, the limitation seems to be 100KB max.

---

### Post by zeqk on 2007-11-15
i so have the same problem with fresh gusty  installation and gusty upgrade

some solution?

---

### Post by zeqk on 2007-12-16
> **sonic1980 said:**
> I have the same problem with a fresh 7.10 installation

It seems that I cannot customize a folder image with a big image. With small JPGs or PNGs works great but if i try to assign a big JPG (more than 500 KBytes) the nautilus file explorer shows a blank paper as folder icon.

Is there any way to correct this? I had no problems with ubuntu 7.04.

A workaround is to resize the image with Gimp (1280x960 to 400x300, for example) and store it in the same folder (or where you want) with the name ".thumb.jpg" (this is optional). And then use this image to customize the folder.

a litle scrpt for this

```
#!/bin/sh
cp $0 thumb.jpg
mogrify -resize 128x -compress jpeg -quality 70 thumb.jpg
```

and for nautilus scripts

[HTML]#!/bin/bash
cp $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS thumb.jpg
mogrify -resize 128x -compress jpeg -quality 70 thumb.jpg[/HTML]

---

