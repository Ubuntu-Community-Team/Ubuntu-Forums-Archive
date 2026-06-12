---
title: "Resize multiple images"
date: 2005-04-08
forum: Desktop Environments
---

### Post by mathjazz on 2005-04-08
Which tool do you use to resize multiple images at one? gThumb is great, but it can only convert and rotate multiple images.

I need this app very often and it should be gtk(2).

---

### Post by jordanau on 2005-04-08
you could use gimp and write a script with script fu. 

[http://www.lemur.com/dmm/culch/scriptsfu/](http://www.lemur.com/dmm/culch/scriptsfu/)

they have a script on resizing png files there.

Between that and a bash script you could automate things pretty well.

I don't know how to do it, I just am 99% sure that is possible.

---

### Post by alastair on 2005-04-08
ImageMagick includes a set of programs, one of which does image manipulation e.g. resizes.

---

### Post by StonePiano on 2005-04-09
I installed **Image::Magick** on my redhat machine at work, and in Perl I can resize images like:

#!/usr/bin/perl -w

use Image::Magick;

my $pic = Image::Magick->new();
my $x = $pic->Read("pic.jpg");
print $x if $x;
$y=$pic->Scale('150x150');
$pic->Write("new.jpg");

But when I do it on my Ubuntu Warty machine at home, I get the followingException error:
**420: no decode delegate for this image format `pic.jpg'**

Does anyone have any ideas as to how I can get a *decode delegate* for jpg on my ubuntu machine?

Many thanks,
StonePiano

---

