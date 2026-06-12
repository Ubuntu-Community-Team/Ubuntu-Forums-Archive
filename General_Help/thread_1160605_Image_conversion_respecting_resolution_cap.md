---
title: "Image conversion respecting resolution cap"
date: 2009-05-15
forum: General Help
---

### Post by macabro22 on 2009-05-15
Hello there mates,

I have high res 1600X1200 TIFF image files which I need to compact down to insert on my thesis. I should respect a threshold of 300 dpi (dots per inch) resolution though.

How can I attain that?

Further is there a solution that would work in batch mode?

Thanks.

---

### Post by cariboo on 2009-05-15
Have a look at the imagemagick package, from the description in synaptic,
> ImageMagick is a software suite to create, edit, and compose bitmap images.
It can read, convert and write images in a variety of formats (over 100)
including DPX, EXR, GIF, JPEG, JPEG-2000, PDF, PhotoCD, PNG, Postscript,
SVG, and TIFF. Use ImageMagick to translate, flip, mirror, rotate, scale,
shear and transform images, adjust image colors, apply various special
effects, or draw text, lines, polygons, ellipses and Bézier curves.
All manipulations can be achieved through shell commands as well as through
an X11 graphical interface (display).

the included utilities are all command line. For more info on imagemagick have a look [here]("http://www.imagemagick.org/script/index.php").

---

### Post by macabro22 on 2009-05-16
I was not successful in finding how to use imagemagick to do what I want. Possibly, the problem is my interpretation of dpi resolution. How can I translate my current image resolution to dots per inch, just so I have an idea?

---

### Post by mbeach on 2009-05-16
What size are you trying to size the pictures down to to?

As I understand it roughly - I could be completely wrong: Let's assume you are using a letter size piece of paper for final print, which is 8.5 inches wide, with say 1/2 inch borders.  You'd like your image which is currently 1600 pixels wide to fit into 7.5 inches.  At 300 dpi (dots per inch) 7.5 x 300 = 2250, so your images should be fitting in fine at their current resolution. I would think you should size your images at a width of 5 1/3 inches in your document to achieve a 300 dpi.

Which application are you using to embed the images?  Are you planning on printing on high quality glossy paper or normal 20lb white 8.5x11 normal photocopy paper?  Are the pictures in color or black and white?

some reference:
[http://designer-info.com/Writing/image_resolution.htm](http://designer-info.com/Writing/image_resolution.htm)

---

### Post by FluffyElmo on 2009-05-16
I'm not sure if you can do what you want, dpi would basically change the size of the image automatically as I understand it. But you should try the Gimp, it lets you change those settings. 
[http://www.freesoftwaremagazine.com/articles/digital_image_resizing_gimp](http://www.freesoftwaremagazine.com/articles/digital_image_resizing_gimp)

You can also try this program which seems aimed at what you want, though I haven't used it myself. [http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by macabro22 on 2009-05-17
Thanks guys

---

### Post by kaibob on 2009-05-17
You appear to have resolved this issue, but I thought I would add one more suggestion. Nautilus Image converter is a Nautilus extension that allows you to resize one, many or all images in a directory. It has few options but is simple to use, easily installed with the Synaptic Package Manager, and may be all that you need.

[http://www.bitron.ch/software/nautilus-image-converter.php](http://www.bitron.ch/software/nautilus-image-converter.php)

If you will be resizing or otherwise manipulating large numbers of images on a regular basis, then Imagemagick is the way to go.

---

