---
title: "program for cropping pictures?"
date: 2009-05-28
forum: General Help
---

### Post by devin0 on 2009-05-28
I have been scanning a bunch of pictures lately and am in search of a Linux program that I can crop large amounts of pictures easily. Can anyone recommend a program that can do this?

---

### Post by timcredible on 2009-05-28
digikam is very good, it's in the repos, supports freehand crop, aspect ratio crop, resize, rotation, etc. etc.  if you have just a few pictures, you could also use kolourpaint.  gimp will do it, but not nearly as easily as digikam.

---

### Post by philinux on 2009-05-28
I use gimp, as I tend to use the curves and levels at the same time. It's in the menu's under apps>graphics.

---

### Post by sahabcse on 2009-05-28
Use "gimp" is best for croping and improve the image pixels. For installing run in terminal

sudo apt-get install gimp.

Default it is avialable in ubuntu

---

### Post by tacantara on 2009-05-28
> **philinux said:**
> I use gimp, as I tend to use the curves and levels at the same time. It's in the menu's under apps>graphics.

I have done some basic photo editing with Gimp (cropping mainly), but I'd like to see if it can do some other tricks.  For instance, I took a picture of an information sheet next to a chair (of historical value/interest) that was on display.  The picture was taken from above the level of the information sheet, so the image appears to be canted.  Is there a way to make it look like the picture was taken straight on?  I can't seem to find anything in the Gimp help file.  Eventually I want to get into the animations, etc., but for now I'd like to clean up that one picture.  Any ideas?

---

### Post by olskar on 2009-05-28
Use gthumb, it should be default.

---

### Post by devin0 on 2009-05-28
Ok cool I tried gthumb and digikam, I like them both. I tried using gimp but im running a really old machine so it takes a while to load. Anyway thanks for the suggestions everyone :)

---

### Post by FakeOutdoorsman on 2009-05-28
I'm surprised nobody has mentioned convert from the **imagemagick** package.  It's command-line and can batch process your images.

[ImageMagick command-line options](http://www.imagemagick.org/www/command-line-options.html#crop)

[ImageMagick v6 Examples -- Cutting and Bordering](http://www.imagemagick.org/Usage/crop/#crop)

---

### Post by CatKiller on 2009-05-28
> **tacantara said:**
>  Is there a way to make it look like the picture was taken straight on?

Well, the Perspective tool seems like the obvious choice. I don't know how good the results are because I've never used it, but this kind of thing is exactly what the tool is for.

To the OP: I tend to crop when I'm scanning the image, in the Preview window before I scan the image. Then I do touch-up work in the GIMP. But then it's quite rare for me to do it, so I don't have to do hundreds in one go. If they all need the same area cropped, it might even be possible to do it in some scriptable command-line way, using ImageMagick or something.

---

### Post by Junkieman on 2009-05-28
For batch cropping try [Phatch]("http://photobatch.stani.be") (It's in the repos - select the 'All Open Source Applications' option in Add/Remove), for everything else theres GIMP :D

---

### Post by malangaman on 2009-05-28
Sometimes you need something quick and easy. I just downloaded Picasa3 to Ubuntu 8.04. It works great and uploads to web albums quickly.

---

### Post by timcredible on 2009-05-28
> **tacantara said:**
>   The picture was taken from above the level of the information sheet, so the image appears to be canted.  Is there a way to make it look like the picture was taken straight on?

digikam has a 'free rotation' and 'perspective adjustment' under the menu tab 'transform' that will probably do what you're looking for

---

### Post by Junkieman on 2009-05-28
> **malangaman said:**
> Sometimes you need something quick and easy. I just downloaded Picasa3 to Ubuntu 8.04. It works great and uploads to web albums quickly.

+1 on that! Even if not a native Linux binary, there's no reason why it shouldn't rock!

---

### Post by Zimmer on 2009-05-28
GIMP has Batch facilities, too  
Xtns>Batch Process

---

