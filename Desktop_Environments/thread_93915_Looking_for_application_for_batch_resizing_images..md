---
title: "Looking for application for batch resizing images."
date: 2005-11-23
forum: Desktop Environments
---

### Post by fragmental on 2005-11-23
I'm looking for an application that can resize multiple photographs.   I would like to shrink the resolution and file size of the images.  I know I can do it with the gimp but doing it picture by picture can be slow when there are a lot to go through.

---

### Post by htoerrin on 2005-11-23
You can use ImageMagick

Type something like this in a shell:
for i *.jpg; do convert -geometry 1024x768 $i outputdir/$i; done

---

### Post by buldir on 2005-11-23
Yep. ImageMagick is the way to go. If you want all your images to be 600 pix in height, do:
```
mogrify -resize x600 *.jpg
```
This will adjust the width automatically to keep the proper ratio. To install ImageMagick, just type:
```
sudo apt-get install imagemagick
```

---

### Post by fragmental on 2005-11-26
[QUOTE=buldir]Yep. ImageMagick is the way to go. If you want all your images to be 600 pix in height, do:
```
mogrify -resize x600 *.jpg
```
This will adjust the width automatically to keep the proper ratio. To install ImageMagick, just type:
```
sudo apt-get install imagemagick
```[/QUOTE]

Worked great. I kind of wish there was a graphical way to do it though.  Not because this wasn't extremely easy, but just because I know I won't remember how to do it this way.  I am not good at remembering console commands.

---

### Post by stalefries on 2005-11-26
I know that the GIMP has command line tools, you might want to do a Google search for that.

---

### Post by IYY on 2005-11-27
I use [BBIPS]("http://www.bbips.org/"). It's a nice GUI to run inside a terminal, and does exactly what you want, nothing less and nothing more.

---

