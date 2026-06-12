---
title: "Text missing in browser and window titlebars"
date: 2008-12-22
forum: Desktop Environments
---

### Post by lombax on 2008-12-22
Had to switch to Windows to post this. 

Text is missing in Firefox and some applications. I can see the text of File, Edit, View, etc. and on the top of individual tabs but the website text does not show and all links appear as lines like this: ________. Also the text in the all application titlebars shows up as boxes like it doesn't recognize the font. I can see the text on Ubuntu menu, desktop icons, and gedit though. 

Not sure what's going on. Anyone know how to fix this?

---

### Post by gettinoriginal on 2008-12-22
Try this:  :P

System > Pref > Appearance > Fonts set rendering to "subpixel smoothing" then go to details set smoothing to "subpixel" and hinting to full

---

### Post by lombax on 2008-12-22
I already had subpixel smoothing set. I changed the settings in details but it had no effect. Thanks though.

---

### Post by gettinoriginal on 2008-12-22
What is the resolution of your monitor ??  Check the dpi ??  Some fonts won't display if that is not rendering correctly.

---

### Post by binbash on 2008-12-23
It is nvidia driver bug as far as i know.Search the forums

---

### Post by Gsundbrunn on 2008-12-23
Hi,

hat the same issue with Firefox. It was caused by a different theme than the default theme. By switching to the default theme everything worked well again.

Regards

Stefan

---

### Post by lombax on 2008-12-24
I decided to rebuild the font cache and that worked. Titlebar no longer shows boxes and I can read website text.

Thanks for all the responses.

---

### Post by sharathpaps on 2008-12-24
@lombax,
          your problem sounds nearly very similar to the problem i've been having. [Here]("http://ubuntuforums.org/showthread.php?t=1020727") is the thread I made on the matter..

I'll try rebuilding the font cache too (although I don't have the faintest idea on how to do that) & see if it helps me..

thanx

---

### Post by Cope57 on 2008-12-24
Sounds to me like the many issues people have running the experimental Compiz-Fusion.
I do not know, I have not used it for a few years. it was experimental back then...

Has Compiz become stable already?

---

