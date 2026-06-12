---
title: "Photo rotates when set as wallpaper"
date: 2008-12-09
forum: General Help
---

### Post by bellabiagio on 2008-12-09
I'm trying to set a photo I've taken on my camera phone as a wallpaper but when I try and set it as a wallpaper, the wallpaper displayed is rotated counterclockwise. Can this be fixed?

I've already tried to rotate the photo at an odd rotation before I set it but that doesn't help.

---

### Post by gettinoriginal on 2008-12-10
So the photo as a file is correct, but it is upside down as wallpaper ??

---

### Post by KeyserSoze93 on 2008-12-10
Jpeg often images contain EXIF meta data, including info such as the time taken, the type of camera used, and crucially, the orientation at which the image should be viewed. Therefor, the photos may all come off your camera as landscape, but if they were taken as a portrait then most software will display them rotated when it reads the meta data.

The only quick solution to this problem would be to open the photo is an app such as Gimp, rotate is if necessary, and copy the whole image into a new file, and save that, thereby disowning all meta data from the original image.

Gimp, in fact, will probably tell you that the image should be rotated and offer to do it for you.

---

