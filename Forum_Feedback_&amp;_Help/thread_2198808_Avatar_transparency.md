---
title: "Avatar transparency"
date: 2014-01-10
forum: Forum Feedback &amp; Help
---

### Post by Erik1984 on 2014-01-10
If I recall correctly when uploading an avatar as a transparent png file it would also be transparent on the forums. When I tried to set my avatar to one that I previously have used (and appeared transparent back then) it just will not display as a transparent image. Currently my avatar looks transparent if you use the default forums theme because I filled the transparent surfaces in the image file with rgb(239,239,239).

---

### Post by bapoumba on 2014-01-10
Testing.

---

### Post by bapoumba on 2014-01-10
Yup..

---

### Post by Erik1984 on 2014-01-10
Thanks for testing. I don't know how the avatar is handled on the back-end but the avatar image file on the forums is a GIF image, my uploaded image was PNG. So it seems to be transformed, could be that this conversion breaks the transparency of the uploaded file.

---

### Post by coffeecat on 2014-01-10
I'm not sure. I downloaded your avatar (right-click -> save image as...) and it reveals itself as avatar1332877_12.gif.png which the forum software often does, no doubt in an attempt to confuse us. However, running "file" on that image gives me:

```
avatar1332877_12.gif.png: PNG image data, 68 x 90, 8-bit/color RGB, non-interlaced
```

So it is a .png. However, it doesn't have true transparency. Have a look at my current one - it will probably download as avatar129087_69.gif.png. Again, file reveals it to be a .png, but it does have transparency which survived the upload. My original was a png file.

---

### Post by Iowan on 2014-01-10
Forum seems finicky sometimes. What size was the original? The last few avatars I've built did not show the transparent background - if the forum had to shrink them. If I reduced the size via GIMP, it looked transparent. (Even the preview in my graphics directory looked different.)

---

### Post by Erik1984 on 2014-01-10
The original file is 76x100 pixels, so it seems to be shrunken to 68x90. I'll try to resize it to that dimensions locally before uploading.

---

### Post by Erik1984 on 2014-01-10
Looks like it works, thanks Iowan and Coffecat. Now my avatar behaves the same as yours: downloading shows a transparent image.

---

