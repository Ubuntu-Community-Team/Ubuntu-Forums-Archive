---
title: "capture 'on the sceen' program"
date: 2009-01-08
forum: General Help
---

### Post by monkey186 on 2009-01-08
There is a wonderful program written for Windows called Kelptomania ([homepage]("http://www.structurise.com/kleptomania/index.shtml"), there is an english version trial, iirc the russian version is free) which allows one to capture any portion of anything on the screen, and to output it either as text (ocr) or grpahic on the fly.

Was wondering if anything similar exists for linux. The important part is that the program should allow user to choose the area to be copyed with the mouse in a manner similar to cropping.

Thanks!

---

### Post by fooman on 2009-01-08
have you tried "gtk-recordmydesktop"?

it should be in synaptic,  or from a terminal:

```
sudo apt-get install gtk-recordmydesktop
```

there are others i'm sure.  not sure if thats even what you need...but thats the first thing that comes to mind.

hope it helps.

---

### Post by monkey186 on 2009-01-08
Thanks fooman that's an interesting program, but it seems it only outputs as video file. 

I was wondering if there is a similar program but that can also output as graphic (and possibly as text)

---

### Post by binbash on 2009-01-08
did you try wink?

---

### Post by ju2wheels on 2009-01-08
I think what you are looking for is a combination of screen capture (already built into Ubuntu if you are using Gnome) and image to ascii art converter (aalib).

For the first part, you can capture your entire desktop by pressing Print Screen buttons or only the window which currently has focus by pressing ALT+Print Screen.

For the second you can use some program based on aalib or use mplayer/mencoder to output an image frame to aalib. You can google for more info on this, dont know how to do it off the top of my head.

---

### Post by monkey186 on 2009-01-14
thanks ju2wheels, for the first part i also realised i can use Gimp as it allows to determine the area to be captured (as opposite to only options entire desktop/focus window)

will have a look for an aalib!

---

### Post by KeyserSoze93 on 2009-01-14
Just pressing "prnt scrn" will launch the gnome screenshot tool. If you want more precise control, you can open a terminal and run:
```
xwd > screenshot.xwd
```

This will allow you to click on the window you want capture.

The file can be open by another app, such as gimp, which will allow you to then save as a more standard format such as png.

If you install imagemagick and gocr, you can use the terminal to set up a pipe like this:

```
xwd|convert xwd:- pgm:-|gocr -i - -o output.txt
```

This will allow you to click on a window, and have its contents converted into a text file called output.txt

---

