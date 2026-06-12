---
title: "Iraf and ds9 on ubuntu 9.04 64-bit"
date: 2009-08-17
forum: Education &amp; Science
---

### Post by astropunkin on 2009-08-17
I recently installed IRAF on my 64 bit ubuntu system.  I followed the directions here [http://geco.phys.columbia.edu/~rubab/iraf/]("http://geco.phys.columbia.edu/%7Erubab/iraf/") for the 64-bit install.  But when I try to use the packages in IRAF such as imexamine that interface with ds9 they do not work.  I get a warning message  Warning: Graphics overlay not available for display device.  Also if I try to call display on an image it won't display the entire image just a very small piece of the center of the image.  Any one else run into this and know how to fix it?  Would be much appreciated :)

---

### Post by favilac on 2009-08-18
I don't know about those instructions, but I have my own installer for IRAF here:

  
 [http://cosmos.astro.uson.mx/~favilac/linastro.html](http://cosmos.astro.uson.mx/~favilac/linastro.html)

  The installer is an .iso file ready to burn on a CD, or to mount it via the loopback device.

  It is tested with Ubuntu LTS. It works with 9.04, with the only exception of pyraf.

---

### Post by astropunkin on 2009-08-18
Thank you!  I will give this install a shot.  I wasn't sure about the other install since it used the --force-architecture command.  I will let you know how it goes!

---

### Post by astropunkin on 2009-08-18
Thank you so much!!  Now imexamine works :)  I still cannot get display to open the entire image but I can use File-->Open to open my image and set the scaling.  I was more worried about using imexamine and such anyways.  Is it ok for me to refer my colleagues to your webpage??  Thanks again!!

---

### Post by favilac on 2009-08-19
Of course you can share the link. 

   Bug reports are welcomed and requests for new features will be considered (as time permits!) :)

---

### Post by IraGainesUK on 2009-09-03
Thankyou so much for this favilac - it installs IRAF and STSDAS much quicker than a newcomer to Ubuntu like me could ever hope to!

Cheers(!!!)

---

