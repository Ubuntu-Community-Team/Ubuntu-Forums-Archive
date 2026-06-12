---
title: "Changing my avatar"
date: 2015-05-11
forum: Forum Feedback &amp; Help
---

### Post by TriforceOfKirby on 2015-05-11
I can't seem to be able to change my avatar, I'm using this URL for the image: [http://triforceofkirby.github.io/favicon.svg](http://triforceofkirby.github.io/favicon.svg). After clicking save it just says "Invalid File".

---

### Post by sudodus on 2015-05-11
Please try with a png or jpg file.

---

### Post by TriforceOfKirby on 2015-05-11
I don't have a png or jpeg of that image, I created it in a text editor(Adobe Brackets). Is there a terminal command I can use to create a rasterization of the image?

---

### Post by sudodus on 2015-05-11
If it is an svg file, it can be read (and edited) by ***inkscape***, and it can be exported as a png file from inkscape. I think also ***gimp*** can import svg files and write them as png or jpg files, at least with fairly simple svg files.

---

### Post by TriforceOfKirby on 2015-05-11
Alright, I'll install inkscape. What image size is ideal for the forums?

---

### Post by sudodus on 2015-05-11
Square avatars 90x90 pixels are good, maybe even slightly bigger.

---

### Post by slickymaster on 2015-05-11
> **TriforceOfKirby said:**
> I don't have a png or jpeg of that image, I created it in a text editor(Adobe Brackets). Is there a terminal command I can use to create a rasterization of the image?
There are many online converters that do what you want, but if you really want to do it through the terminal you can use the rsvg command line tool. To install it in Ubuntu, run this command:```
sudo apt-get install librsvg2-bin
```To convert an SVG image, you can now use this command```
rsvg file_name.svg file_name.jpg
```
All files will be generated in the current terminal location.

---

### Post by slickymaster on 2015-05-11
*Moved to the ***Forum Feedback & Help*** sub-forum*

---

### Post by TriforceOfKirby on 2015-05-11
Ok I exported the image as 100x100 px; however, the image seems rather poor quality; the arcs aren't being rendered perfectly round, they're almost elliptical, there is some space in between as a result. Are there some settings in inkscape to fix this?

---

### Post by Elfy on 2015-05-11
> **TriforceOfKirby said:**
> Alright, I'll install inkscape. What image size is ideal for the forums?

Note: The maximum size of your custom image is 90 by 90 pixels or 19.5 KB (whichever is smaller).

---

### Post by sudodus on 2015-05-11
> **TriforceOfKirby said:**
> Ok I exported the image as 100x100 px; however, the image seems rather poor quality; the arcs aren't being rendered perfectly round, they're almost elliptical, there is some space in between as a result. Are there some settings in inkscape to fix this?

I think your avatar looks good :-)

I have used inkscape to make some icons, but I'm far from an expert. Maybe it would work better if you use a bigger size (higher resolution) when you create the image, and shrink it afterwards (when you are exporting it, or even in gimp when it is already a png file).

---

### Post by ajgreeny on 2015-05-11
There is surely no need to install something as large as inkscape, unless you will use it for other purposes, just to do that simple job.

You can use **convert file.svg file.jpg** which uses imagemagick, which I think is installed by default.  If not, install it; it is not a large install like inkscape.
  You can also change the size at the same time.
See **man convert** for all details.

---

### Post by TriforceOfKirby on 2015-05-11
Ok I tried rsvg and it worked very well; I was able to create a 90x90px avatar and 100x100px profile picture. The arcs look much more circular now. I don't think I'll be using inkscape as I prefer to create SVGs with a text editor, so I'll uninstall that. Thanks for the help.

It would be nice however if the forums allowed SVG avatars in the first place; is there a possibility of that in the future?

---

