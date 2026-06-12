---
title: "Wine Font Problems"
date: 2009-01-11
forum: Desktop Environments
---

### Post by Dask8r on 2009-01-11
Once more Wine is giving me trouble with Fonts, I have all the correct Fonts installed at the right places and this is what happens now.  My effects are set to None like I was instructed to set before.
[IMG]http://img212.imageshack.us/img212/6468/screenshotwineconfigurayr2.png[/IMG]

---

### Post by Dask8r on 2009-01-11
Anyone?

---

### Post by Dask8r on 2009-01-12
Need help with this it's really buggin and I cant do anything :(.

---

### Post by undoIT on 2009-01-12
Imagine my surprise this morning at 6:30 AM when I opened my stock trading program Quotetracker in Wine and everything looked like it was in Arabic. Have I been hacked!!!?

Well, actually everything was in Tibetan, just the font is set too small to recognize it right away in Quotetracker. Over the weekend I had installed a Tibetan publishing tool called Pechamaker to attempt to send some Tibetan texts I had typed up years ago to somebody who had requested them. But I realized I wouldn't be able to print to PDF so I ended up using the Windows install in Virtualbox.

I had to delete the Tibetan fonts that had been installed to this folder:

/.wine/drive_c/windows/Fonts

I guess Tibetan gotten set as the system font. Not sure if this will help, but check that folder to see if there are any extra fonts there.

Is there any way in Wine to adjust the system font?

---

### Post by Dask8r on 2009-01-12
Nope no matter how I change or add Fonts this problem comes up.

---

### Post by undoIT on 2009-01-12
Perhaps it is your graphics card. Did  you see this thread:

[http://ubuntuforums.org/showthread.php?t=1009930&highlight=wine+font](http://ubuntuforums.org/showthread.php?t=1009930&highlight=wine+font)

---

