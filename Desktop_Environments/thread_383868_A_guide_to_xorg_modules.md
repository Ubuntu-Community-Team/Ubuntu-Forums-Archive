---
title: "A guide to xorg modules?"
date: 2007-03-13
forum: Desktop Environments
---

### Post by duns0014 on 2007-03-13
Hi, I'm trying to get info on the modules that xorg loads so that I can find out which I don't need.  X takes up quite a bit of memory, so this can help a lot.  I found this thread [http://ubuntuforums.org/showthread.php?t=62650](http://ubuntuforums.org/showthread.php?t=62650) but it doesn't give much explanation about what the modules do that you comment out.  Some of those modules weren't even in my xorg.conf.  Here's my section for modules:

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
#       Load    "glx"
        Load    "int10"
#       Load    "type1"
        Load    "vbe"
EndSection

I've already commented out the dri section (according to some error message, my machine doesn't even support it), the glx section (I don't use anything that uses opengl), and the type1 section (I guess this is some font type that's only used by pdfs, and then only sometimes.  I haven't had problems after doing this, even when reading pdfs).  Any other help on these cryptic names?  I've used google, the ubuntu forums, and even the gentoo forums, and wikipedia.  Also, any tips on disabling fonts?  As I understand, those can take up a lot of memory too.

---

### Post by clickwir on 2007-03-15
Don't have a list but in this config tool, there's a brief explanation of some of them. You can just hit Ctrl+C once you've gotten to that spot and read it so you don't actually overwrite your config file.

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by duns0014 on 2007-03-16
Thanks for that.  I've figured out that ddc, vbe, int10, and i2c seem to have to do with a graphics card controlling the monitor, like changing hue and whatnot.  Bitmap, freetype, and type1 are fonts.  Extmod seems to be a collection of random stuff.  So it looks like I'm good with what I commented out.  I also commented out cyrrilic fonts since I just get an error in my xorg log with it, and I can't really read them.

---

