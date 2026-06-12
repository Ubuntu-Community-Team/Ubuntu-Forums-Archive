---
title: "Bright usplash for Fiesty"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by EKZ on 2007-06-01
Just created bright usplash for fiesty. I get all artwork from gdm Human & metacity Human themes.
Want to share with public (and test he-he).

Resolutions:
1280x1024
1024x768
800x600
640x480
1365x768 (don't fully understand this, may be buggy)

Installation:
UnBzip usplash-theme-ubuntu.so.bz2 somewhere.

sudo cp /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-theme-ubuntu.so.bak
sudo cp ./usplash-theme-ubuntu.so /usr/lib/usplash/usplash-theme-ubuntu.so

Test:
sudo usplash

Install into boot sequence:
sudo mkinitramfs -u

Uninstall:
sudo cp /usr/lib/usplash/usplash-theme-ubuntu.so.bak /usr/lib/usplash/usplash-theme-ubuntu.so
sudo mkinitramfs -u

2Admins:
If it is not right place to post such a things, just let me know where it is :).

---

### Post by orange2k on 2007-06-01
Just one question: how did you do it?
I mean is it easy to convert any image of choice for this purpose and is there anything else to take care of?
I`m interested to create a custom usplash myself - just with another custom image...:D

---

### Post by EKZ on 2007-06-01
The main problem in creating usplashes - make good 256 color images for BG and progress bars with same palette with all 256 colors matched to 16-bit colorspace (or you get rainbow instead of gradient). And this is somewhat magic...

As of compiling and installing - it's simple - make, make install... :)

---

### Post by EKZ on 2007-06-01
Did you test, by the way? See any problems?

---

### Post by orange2k on 2007-06-01
No, I didn`t have the chance to get to my machine yet, so I`ll do it later in the evening...

---

### Post by orange2k on 2007-06-01
Ive tested the usplash and it works, however I dont like the image that much, I wish you would have done it with some other image instead of this one...

---

### Post by EKZ on 2007-06-01
This splash it a "technology preview". I like it, but this is not the point. I try to find a clear way to implement image conversions. Now I'm stitching everything that I digged out and will (hopely) publish a little HOWTO (or maybe ever set of tools). So it's up to you... just wait a little.

---

### Post by orange2k on 2007-06-01
You`re doing a great job. Until now I didn`t think it was so difficult to set up a custom usplash.
Please do post a how-to - it would be very interesting to know...:D

---

### Post by blaresutton on 2007-06-03
EKZ,

Any luck with the usplash customisation guide? I have tried following the information provided in the general how to and those provided with libusplash-dev to no avail. I am remastering an iso remix based on feisty and would love to release it with a changed usplash rather than the default. Even a brief write up of what you had to do would be appreciated to get me started.

Cheers,

Blare

---

