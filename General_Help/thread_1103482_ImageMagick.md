---
title: "ImageMagick"
date: 2009-03-22
forum: General Help
---

### Post by measekite on 2009-03-22
I used Synaptic to install ImageMagick.  I received a dialog that it was successfully installed.

I do not see any items in the menu that allows me to launch the program.  I also do not see any executables when doing a search of the filesystem.

How do I get to use this program?

---

### Post by apmcd47 on 2009-03-22
**_display xxx_** will run imageMagick's display program. **_mogrify_** is another program. Also **_convert_**.
```
convert jane.gif jane.jpg
```will convert a picture of your girlfriend from gif to jpeg.
```
mogrify -format jpg *.gif
```will batch-convert all gifs in the current directory.

Look in /usr/share/doc/ImageMagick for a full set of documentation, or [go to their website]("http://www.imagemagick.org/script/command-line-tools.php").

Andrew

---

### Post by measekite on 2009-03-22
> **apmcd47 said:**
> **_display xxx_** will run imageMagick's display program. **_mogrify_** is another program. Also **_convert_**.
```
convert jane.gif jane.jpg
```will convert a picture of your girlfriend from gif to jpeg.
```
mogrify -format jpg *.gif
```will batch-convert all gifs in the current directory.

Look in /usr/share/doc/ImageMagick for a full set of documentation, or [go to their website]("http://www.imagemagick.org/script/command-line-tools.php").

Andrew

Are you saying that it is a command line program with no GUI frontend?

---

### Post by apmcd47 on 2009-03-23
> **measekite said:**
> Are you saying that it is a command line program with no GUI frontend?

That's about the size of it. I think there is a GUI for Windows, but ImageMagick is really a graphics library for command-line users or programmers. If you want to do batch processing of images, eg resize, rotate, insert text, then this is your toolkit of choice (the alternative being something with "pbm" in the name :p ). 

It is not a rival to GIMP, I'm afraid.

Andrew

---

### Post by Liviu-Theodor on 2009-03-23
> **apmcd47 said:**
> **_display xxx_** will run imageMagick's display program. **_mogrify_** is another program. Also **_convert_**.
```
convert jane.gif jane.jpg
```will convert a picture of your girlfriend from gif to jpeg.
```
mogrify -format jpg *.gif
```will batch-convert all gifs in the current directory.

Look in /usr/share/doc/ImageMagick for a full set of documentation, or [go to their website]("http://www.imagemagick.org/script/command-line-tools.php").

Andrew

Thanks

---

