---
title: "FLUXBOX fbsetbg option to ZOOM instead of stretch"
date: 2009-04-03
forum: Desktop Environments
---

### Post by pw_f100_220 on 2009-04-03
Hi, I have dual monitors, and most of my favorite wallpapers are high res but for one screen.  I have a few 3360x1050 that are ok, but I like showing my ubuntu pride, and mostly I just find high-res one screen images with Tux or Ubuntu logo.

I can't get fbsetbg to "zoom to fit" like in gnome where the aspect is maintained but zoomed in until the entire screen is filled.  I ran fbsetbg -h and got
"Options:

    -f  Set fullscreen wallpaper (default).
    -c  Set centered wallpaper.
    -t  Set tiled wallpaper.
    -a  Set maximized wallpaper, preserving aspect.
        ( if your bgsetter doesn't support this
          we fall back to -f )

fbsetbg -a fills it vertically, but horizontally leaves half of each screen black.
fbsetbg -fa won't do anything (darn, I thought I was smart for trying)

Is there something I'm doing wrong or just missing?  What should I do other than settle with 3360x1050, or combining/cropping wallpapers?

Thanks!

---

### Post by Giblet5 on 2009-04-03
I know of no background setter that will do an aspect zoomed stretch.

You still have options:

A) You can filter your images, using ImageMagick, to create a new set of zoomed and cropped images, saving them someplace new.

B) You can add the functionality to fbsetbg.

C) You can hand tweak the images with the gimp (or any tool you prefer) and save copies for use as background images.


I take pix with a great camera, then I adjust them for a perfect fit on my monitor and save that as a background image. That way, I have control over the image quality, the framing, etc. That's option C and it works best for me.

---

### Post by pw_f100_220 on 2009-04-04
It can't be that presumptuous to think there is someway to do this in Fluxbox...I think it's the default setting in Gnome's gui background manager...whenever you choose a wallpaper it zooms until it fills the screen without distorting the image (of course with other options)...it seems like this would be default in fbsetbg/esetroot

as for adding the function...that sounds like development...maybe someday...

Thanks for the reply!

---

### Post by kerry_s on 2009-04-04
try nitrogen it has a automatic feature> sudo apt-get install nitrogen
[http://projects.l3ib.org/nitrogen/](http://projects.l3ib.org/nitrogen/)

---

### Post by pw_f100_220 on 2009-04-05
Thanks Kerry_S, but it didn't do the trick.  So far the only options have been stretch to fill screen, maximize the image vertically while preserving the aspect, tile, and center the wallpaper at it's original resolution.

This isn't a frustration significant enough to send me back to Gnome...but I sure does miss that feature

---

