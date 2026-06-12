---
title: "[SOLVED] Installing &amp;quot;Tahoma&amp;quot; in Ubuntu"
date: 2007-10-05
forum: Desktop Environments
---

### Post by arjones85 on 2007-10-05
I have found that using the sans font in Ubuntu is giving me a headache. I would like the fonts used in everything in Ubuntu to be exactly what Windows XP uses down to the "T". 

How do I achieve this?

I have installed the msttcorefonts package (I believe that's what it is called. It was installed using easyubuntu's "Install microsoft fonts" option.

I looked in Windows's fonts list and it seems it is using "Tahoma". How can I get this? I've done a good amount of forum searching but nothing I've done has seemed to help.



Thanks for the help!

---

### Post by yabbadabbadont on 2007-10-05
Tahoma isn't one of the fonts that Microsoft released for distribution like the others in the msttcorefonts package.  The only (legal) way to get it is to copy it off of your Windows installation.  Then create a directory called ".fonts" (note the period) in your home directory and put it in there.  Just a heads up, in Linux, any files or directories whose names start with a period are hidden by default.  You'll need to toggle the option to view hidden files in order to see it once you create it.

---

