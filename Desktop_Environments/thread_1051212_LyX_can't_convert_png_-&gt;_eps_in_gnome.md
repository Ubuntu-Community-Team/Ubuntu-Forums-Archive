---
title: "LyX can't convert png -&gt; eps in gnome"
date: 2009-01-26
forum: Desktop Environments
---

### Post by vancouverite on 2009-01-26
Hi I just installed LyX as I'm always looking for a more intuitive LaTeX editor.  I was using the tutorial (Help -> Tutorial) and whenever I try to export the tutorial itself to a DVI, PS, or PDF I get the error 

"No information for converting png format files to eps. Define a converter in the preferences."

I don't know what converter to use.  Does anybody have any suggestions?  Dose a proper install of this application require that I install KDE (as some posts suggest).  I noticed that there are no image converters defined, so I assume this problem will not be limited to png.

Also, I tried the Tools -> Reconfigure and that didn't find the converter.

Thanks for your attention,
Van

---

### Post by Tamlynmac on 2009-01-26
You might check this out. Appears fairly simple.
I don't to much with eps's, but found this and the reviews looked good..

[http://www.terminally-incoherent.com/blog/2007/01/18/convert-png-to-eps/](http://www.terminally-incoherent.com/blog/2007/01/18/convert-png-to-eps/)

Good Luck

---

### Post by mionescu on 2009-01-26
As far as I know LyX uses imagemagick to convert images from one format to another. Did you install it? You can search in Synaptics for LyX and then install some of the programs from the "Recommended for Installation" or "Suggested for Installation" lists. In the former I installed everything with the exception of "viewpdf.app", "xpdf-utils", and "xpdf-reader".

Good luck,
Marius

---

### Post by vancouverite on 2009-01-26
Hi all,
Thanks for the ideas.  I ended up using imagemagick (sudo apt-get install imagemagick) and configuring it myself.  This was simple and involved the following:

1) Open LyX
2) Tools -> Preferences
3) File Handling -> Converters
4) Change "From format:" to PNG
5) Change "To format: to EPS
6) In the "Converter:" text field enter

convert $$i $$o

7) Select "Add" 
8) Select "Save" then "Close"

The program "convert" is very general so I think that the same technique should be able to convert any image format to EPS.

Thanks again for the help and I hope that this is useful to others in the future.

Cheers,
Van

---

