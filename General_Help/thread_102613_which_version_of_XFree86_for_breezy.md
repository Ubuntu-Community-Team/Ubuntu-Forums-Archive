---
title: "which version of XFree86 for breezy?"
date: 2005-12-12
forum: General Help
---

### Post by bazcor on 2005-12-12
hello .. well the heading says it all really, I'm looking to download tha ati radeon driver from the ati website, but they have versions for XFree86 4.1,4.2,4.3 and X.Org 6.8. Which one do I download for mr breezy?

many thanks in anticipation .. Barry (a newby)

---

### Post by Ocxic on 2005-12-12
just download the ati driver installer. it'll do the rest for you, don't forget to run fglrxconfig after you run the installer. to run it type this in a terminal:

sudo chmod +x "/path to installer file you downlaoded" OR right click on the file, click proerties, permissions tab, select all the execute boxes.

sudo ./ati_installer.run

then sudo fglrxconfig

and your drivers will be installed, you must restart your computer to have the changes take affect OR crtl-alt-backspace.

---

### Post by bazcor on 2005-12-13
OK thanks for that Ocxic, I now have it installed and have enabled large screen for my two monitors. There are a couple of problems with this caused presumably by having two different sized monitors (one 15" 1024x768 and a 17" 1280x1024). 

The problem is that the 15" monitor seems to have an invisible area off the screen at the bottom, where the mouse pointer will dissapear into and throw up a thin vertical area of corruption on screen. This vanishes as the mouse is brought back to the screen. 

Would this be fixed by allowing it to have a virtual screen size? Or is there a better solution?

Thanks again .. Barry

---

