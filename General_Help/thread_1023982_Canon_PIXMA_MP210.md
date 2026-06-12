---
title: "Canon PIXMA MP210"
date: 2008-12-28
forum: General Help
---

### Post by drricci on 2008-12-28
Hello, I hope this is the right section for this post.
I can't make my Canon Pixma MP210 printer work under Ubuntu 8.04.
I followed the instructions I found in a post in the "Absolute beginner talk" entitled "Canon PIXMA MP210. How to make it work?" (unfortunately that is now a read-only thread).
I succeeded in downloading and installing the drivers but when I try printing a test page using the gnome-cups-manager the following message appears: "Printing to 'MP210_series' failed with error code: 1034
is the printer paused ?". 
In the printer properties box it says that the driver for the printer is "text-only". Plus when I try to print with OpenOffice I get the message: "Error while printing".
Instead I can make the scanner work with The Gimp.
Is there anything else I can try?
Thank you for your help.

---

### Post by cguy on 2009-02-03
So as not to open new topic:
Is there any way possible to increase the contrast of your prints?

I have some poorly scanned documents (they appear gray instead of black) which I try to print and all I get is a lot of dots?
Must I install Windows to print them? ](*,) :mad:

---

### Post by cguy on 2009-02-03
BUUUUUUUUUUUUUUUUUUUUUUUUMP!

Save my mental sanity, please!

---

### Post by impact on 2009-02-03
> **cguy said:**
> BUUUUUUUUUUUUUUUUUUUUUUUUMP!

Save my mental sanity, please!

[http://ubuntuforums.org/showthread.php?t=943626](http://ubuntuforums.org/showthread.php?t=943626)

I have followed this thread to install my MP220 and it works (on a 32-bit system).

First remove the text-only printer driver and disconnect the printer.

Then dowload 4 .deb packages mentioned in that thread:

-1. cnijfilter-common_2.80-1_i386.deb
--2. cnijfilter-mp210series_2.80-1_i386.deb
--3. scangearmp-common_1.10-1_i386.deb
--4. scangearmp-mp210series_1.10-1_i386.deb

Install them, reboot, connect your printer, it should be correctly detected as MP210.

Printing should now work.

Edit: Scanning is even easier, don't bother with the points 7) to 14), just switch the printer into scanner mode, start X-sane and it should automagically detect it.
Edit 2: Oh, you already got the scanner working. :)

---

### Post by cguy on 2009-02-03
Printing already works. What does not work is using more ink to print the same stuff. I want an alternative to Windows's printing intensity / high quality printing.

---

### Post by impact on 2009-02-04
OIC. MP220 has those options in the printer menu itself (I'm assuming we're talking about the print quality settings). I don't have other OSs' installed so I have no means to compare actual prints from Windows and Linux. But GIMP should be able to fix those pics, which should have been scanned in grayscale instead of bw.

---

### Post by cguy on 2009-02-04
You can see 2 pages in the archive:
- the one where you can read the text is printed from Windows (High Color Intensity)
- the other one is a double print from Ubuntu

Unfortunately, Gimp is not the answer when I'm dealing with 40 pages pdf-s.

Oh well, I fell at peace with having to start the laptop to print some pages.

----

MP210 doesn't have those options in the its menu :(

---

### Post by impact on 2009-02-04
Wow, that's quite a difference! And you're right that printing 40 pages from GIMP would probably be tedious - it can import pdf and modify the images easily, but exporting and printing would be more time-consuming.

---

### Post by yoman82 on 2009-02-04
Try using Xsane. It´s really nice, you can do almost anything, including increasing scan quality.

---

### Post by cguy on 2009-02-05
@yoman82: I'm not the one who scanned those documents.

If anyone will ever come up with an answer, no matter how much time it will pass, please post it here.

---

