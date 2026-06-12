---
title: "img to iso - what am I doing wrong?"
date: 2009-03-09
forum: General Help
---

### Post by pikaia on 2009-03-09
I've read through the threads.  Read about ccd2iso and acetoneiso... and I've tried them both and get errors on both.  

In ccd2iso I save an img file ibex.img (the mid img) to my desktop in the terminal, I cd to desktop and then enter ccd2iso ibex.img ibex.iso and get this error 
Unrecognized sector mode (0) at sector 0!

I load acetoneiso and it will not mount an img (but mounts an iso fine) I get an error saying Cannot mount.  And when I go to Conversion img to iso and select my .img file and then where to save the iso file and try to convert I get this error.

"This is error is mostly because the image you are trying to convert is already ISO-9660.
To check, open a terminal and type: file nameimage.xxx
If it is already ISO-9660, there is no need to convert it. Simply Extract it or Mount with AcetoneISO2."

I've tried just renaming the file to ibex.iso, but acetoneiso won't mount that either.  

Please, any help would save some frustration.  I'm trying to test out the img image on a machine that won't boot from usb, so I need the iso to burn it to a cd.

Thanks.

---

### Post by Ocxic on 2009-03-09
ccd2iso is for .ccd files not .img

---

### Post by pikaia on 2009-03-09
Actually according to [this](https://help.ubuntu.com/community/ManageDiscImages), it is.  But that doesn't mean I'm using the wrong utility... can someone suggest a way to do this properly?

Thanks.

---

### Post by bulletxt on 2009-03-11
I may be wrong but I think you can directly burn the *.img file with K3B burning software.

---

