---
title: "4x6 borderless photo printing"
date: 2007-04-01
forum: Desktop Environments
---

### Post by finite9 on 2007-04-01
please help!  I have a Canon PIXMA MP450 that, under Windows can print a photo on Canon PP101 paper (4x6") without borders.  Even if images taken with a consumer level digital camera (Canon IXUS 400) are not the right size, Windows does some auto-cropping of the image so that the scale is retained, and one side of the image gets cropped.  This is OK for me.

I run Feisty Beta amd64 and as there is really no easy way to get this printer working with free software (no, the DEBs that the Japanese guy created for i386 do not install correctly under amd64 even with force-architecture, and Gutenprint in CUPS does *not* work, contrary to all the posts I have read), I have installed Turboprint and it works flawlessly...test page, printing from OOo or Firefox all work fine.  The Turboprint driver even has support for 4x6 borderless page size.

However, when I try to print an image from Gnomes "Image Viewer" aka Eye Of Gnome, it does not seem to have support for 4x6 borderless.  It has the page size, but the image is not rotated for best fit, so a landscape image is printed in portrait mode.  I cannot see any option to rotate the image in Image Viewer.  I tried Gimp as well, but the print system in Gimp does not seem to use CUPS as default and it seems like I have to setup a new printer through the Gimp interface, which I didn't know how to do.

So, after much rambling, my question:  How do you print 4x6 borderless photos?

---

### Post by finite9 on 2007-04-01
I just looked at F-spot and it handles borderless printing better than Eye of Gnome, which cannot do borderless at all it seems, but F-spot still doesn't allow you to select some kind of autocrop function so that there really is no white space left on the 4x6 paper.  Windows does admittedly crop quite a lot of the image to make it fit the entire paper, and maybe this is unacceptable for some, but I would like the choice at least.

---

### Post by djeley on 2007-04-29
In CUPS ([http://localhost:631](http://localhost:631) or [http://127.0.0.1:631)](http://127.0.0.1:631)), if I set my printer options as follows:

Page Size: Photo or 4x6 inch index card
Printout Mode: Photo (on photo paper)

I find that F-Spot will print excellent borderless photos! The photos need to be edited first in F-Spot using the crop constraint feature. If you don't know how to use this:

[LIST=1]
[*]Got to the edit mode in F-Spot
[*]Select the constraint mode e.g. 4x6 postcard
[*]Left click on the photo and drag your mouse to select the area you want to print - adjust and drag as necessary. This area will be constrained to 4x6 (or whatever you chose in the previous step)
[*]Click the Crop button
[*]Go to the File menu. Select Create New Version... and enter your version name e.g. "4x6"
[/LIST]

Hope that helps!

Duncan

---

### Post by mannheim on 2007-04-29
I have never found a good solution to printing 4x6 borderless photos either, except to use vmware and run a Windows application unde emulation.

I have a Canon camera (which produces jpeg images that are not 4x6). To print out a bunch of photos, I run Canon's "Easy Photo Print" program, under vmware.

---

### Post by finite9 on 2007-04-30
actually, i got around this...

If you stick a copact flash card into the slot in my printer, then when you connect the printer, the CF card shows up in ubuntu, and using a script that accesses it as root, i can transfer images to the CF card, then remove/reinsert the card and use the printers LCD display to print the images.  This is quite painless for me, and all other printing works ok.

---

### Post by karhulitos on 2007-05-26
> **djeley said:**
> In CUPS ([http://localhost:631](http://localhost:631) or [http://127.0.0.1:631)](http://127.0.0.1:631)), if I set my printer options as follows:

Page Size: Photo or 4x6 inch index card
Printout Mode: Photo (on photo paper)

I find that F-Spot will print excellent borderless photos! The photos need to be edited first in F-Spot using the crop constraint feature. If you don't know how to use this:

[LIST=1]
[*]Got to the edit mode in F-Spot
[*]Select the constraint mode e.g. 4x6 postcard
[*]Left click on the photo and drag your mouse to select the area you want to print - adjust and drag as necessary. This area will be constrained to 4x6 (or whatever you chose in the previous step)
[*]Click the Crop button
[*]Go to the File menu. Select Create New Version... and enter your version name e.g. "4x6"
[/LIST]

Hope that helps!

Duncan

Wau man! That worked for me. Beautiful borderless from HP Photosmart 8150 with 10*15 paper (I set 'Photo Paper with tear off" wherever I saw paper size).
I already did the steps you described in F-Spot but still I had white. So the thing must have been setting things ok in CUPS.

I might want to say something about why the **** I need to go to some web page to do this if I've already set paper propeties in System -> Maintenance (?) -> Printers and in all applications I try to print from, but I won't. I'm happy now. Wife gets borderless photos and I can shutdown our old Windows 2000 box, finally!

---

