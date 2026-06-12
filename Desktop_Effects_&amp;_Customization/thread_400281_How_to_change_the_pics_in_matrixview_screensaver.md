---
title: "How to change the pics in matrixview screensaver?"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by LilaQ on 2007-04-03
Hey guys,

I saw the matrixview screensaver when i recently installed Ubuntu 7.04 and I really liked it. So my goal is to exchange the pics from Neo, Trinity etc with my own pictures. Since there were no simple .png's to replace I downloaded the source of the package and could locate a /matrixview_textures directory with a "cpics" (98.4kb) and a "cfonts" (128.0kb). I'm pretty sure the pictures are in that "cpics" but I have no idea how to open / replace it. Gimp won't open the file, arc won't too, ImageMagick won't convert it, I have no idea what to do with it now.

I hope someone of you can help me :)

LilaQ

---

### Post by gspawn69 on 2007-04-06
The images are changed by passing a command-line parameter, like so:

```
matrixview --image [directory]
```

However, I can't find a way to specify this parameter  in the screensaver manager so that it will load my picture directory for the actual screensaver, therefore I can only get it to work when I run it from the command-line.

---

### Post by Cullen on 2007-04-12
bump

---

### Post by Jons_Collasius on 2007-04-29
edit **/usr/share/applications/screensavers/matrixview.desktop**
> [Desktop Entry]
Encoding=UTF-8
Name=MatrixView
Comment=Assimilation of Matrix GL by Alex Zolotov <nightradio@knoppix.ru> ([http://knoppix.ru/matrixgl.shtml](http://knoppix.ru/matrixgl.shtml)) Ported to Linux by Tugrul Galatali - <http://rss-glx.sourceforge.net/>.
TryExec=matrixview
Exec=matrixview -r **--image /path/to/your/pictures**
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver


---

### Post by tommytomato on 2007-06-04
Thank you i was thinking about it, did a search and here it was, now my kids are spinning out, wondering how it was done.

thanks again

TT

---

### Post by hotdoog on 2007-06-11
This is not working for me. I am trying to do this in Dapper, perhaps the configuration is different for the older version? /usr/share/gnome-screensaver/themes/matrixview.desktop is what I am editing. Right now what is happening is I've edited the .desktop file but it just ignores it and continues to show the old pictures from the movie... Do I need to restart gnome perhaps?

Or, my other thought was that the pictures have to be in a certain format and I am not using the right one. What format/size do the images in the directory need be?

I also tried adding the -r --image home/image/ to the TryExec= field. But that just made the Matrixview entry not shop up at all in the Gnome Screensaver preview/chooser thing. 

Thanks in advance for any suggestions.

---

### Post by Kwunman on 2007-09-30
Hey, I found that it will only show pictures in that directory, not any subdirectories, you have to be really specific, otherwise it reverts back to default pictures.
Hope this helps,

Kwun-Man

---

### Post by Sturmeh on 2007-10-03
Also, just put a 1x1sized image of pure whiteness, in the specified directory, and nothing else, and you get pure Matrix scrolling. xD

( Is there by any chance a trigger for that? - No images? )

---

