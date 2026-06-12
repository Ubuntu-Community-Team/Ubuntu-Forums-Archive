---
title: "how do you load images in octave"
date: 2008-11-14
forum: Education &amp; Science
---

### Post by 7raTEYdCql on 2008-11-14
When i try the following command
a=loadimage("a.img")

The image doesnt load.
Am i supposed to install some extra packages to enable image processing in octave.

Thanking you,
Mehrzad

---

### Post by normandin on 2008-11-14
could you provide some additional details?  what type of image are you trying to load?  does the call to loadimage() generate an error message?

you might be interested in the "image" package from octave forge.  it is available in the intrepid universe repos under the package name octave-image (you may need to add it to your octave path after it's installed).  alternatively, you can download the image package from octave-forge ([http://octave.sourceforge.net](http://octave.sourceforge.net)) and follow the instructions there.

---

### Post by etfd on 2009-05-02
First, make sure you install the octave-image package (do a sudo apt-get install octave-image ) this installs the imread function which opens various image formats. 

-D.

---

### Post by macotto on 2009-05-02
you might be interested in the "image" package from octave forge. it is available in the intrepid universe repos under the package name octave-image (you may need to add it to your octave path after it's installed). alternatively, you can download the image package from octave-forge ([http://octave.sourceforge.net]("http://octave.sourceforge.net/")) and follow the instructions there.

---

