---
title: "librmagick-ruby problem"
date: 2005-11-22
forum: Desktop Environments
---

### Post by bmgz on 2005-11-22
I need to include some basic image processing with my Rails app, so I install librmagick-ruby (ruby ImageMagick lib). I seems to be pretty broken.

Condsider the following:

irb> img = Magick::Image.read("mytestfile.jpg")
Magick::ImageMagickError: unable to open image `le.jpg': No such file or directory:

so I added 8 characters before the filename:

irb> img = Magick::Image.read("xxxxxxxxmytestfile.jpg")
=> [`\uffff[38]  0x1163 DirectClass 1535-bit 372004b]

...and it works? I have absolutely no intention of working with this if I have to use this crude workaround all the time, does any one have any idea what the problem is? I have seen various bug reports etc about incompatible ImageMagick version or something, but that seems ludicrous as the bug reports go back to over a year ago...

---

