---
title: "How did they get this vista-like transparency?"
date: 2010-06-16
forum: Desktop Environments
---

### Post by ginjaninja405 on 2010-06-16
As I asked, I really really would like to know how I could get this transparency for my Ubuntu install, here is the image for reference:

[IMG]http://public.bay.livefilestore.com/y1p4CFnHsRBapVWQUSJmWfwrB6l-QgJk5Ahfm_cYkZA6f6haIYW_EX5xyqcyRvMBNrdjOJLH93ypkj1UJJqWC8jBw/image%5B3%5D.png[/IMG]

Can anybody help?
Thanks!

Sam

---

### Post by Maheriano on 2010-06-16
It's part of Compiz if you enable it. I think you might also be able to set it in the theme.

---

### Post by nilarimogard on 2010-06-16
That would be [RGBA transparency]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html").

---

### Post by ginjaninja405 on 2010-06-21
> **nilarimogard said:**
> That would be [RGBA transparency]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html").

Thanks for the help, I've installed everything and followed the tutorial word for word, but now I get a plain white background and whenever I go to change it, it sort of hangs for about 20 seconds, and then doesn't do it. Any idea what's going wrong?

---

### Post by ronnielsen1 on 2010-06-21
You could try this way. You don't have to install the whole 7 look

[http://my.opera.com/ubuntunerd1/blog/how-to-make-ubuntu-look-like-windows7](http://my.opera.com/ubuntunerd1/blog/how-to-make-ubuntu-look-like-windows7)

> 
you also need another package call "libemeraldengine0" Mark it for  installation as well. click Mark then Apply again in the new window that  appears. Then, close Synaptic Package Manager. 

next download the windows7 "Emerald theme" from [here]("http://www.gnome-look.org/content/show.php/Who+Needs+Windows+7+%3F?content=105399") now go to >system > Preferences >  Emerald Theme Manager. 
click on Import and browse to the location where you downloaded the  Windows7 Theme highlight it and press open. 

once the theme is installed if you don't see any changes Hit  "Alt+f2" and restart Emerald by typing this command: 
emerald --replace 
you should now be able to see the transparency in your window  borders, now download the clean version of the windows7 wallpaper from [here]("http://www.4shared.com/file/110446452/d03e3272/img-wallpapers-windows-7-wallpaper-microsoft-15253jpg.html") install it by right clicking on an empty area  of your desktop and scroll to "Change Desktop Background" it should look  like this 

> You could try this way. You don't have to install the whole 7 look

But if you want to and you're running 10.04 
[http://ubuntu.sun.ac.za/index.php?title=W7_Theme](http://ubuntu.sun.ac.za/index.php?title=W7_Theme)

---

### Post by yossell on 2010-06-21
> **ginjaninja405 said:**
> Thanks for the help, I've installed everything and followed the tutorial word for word, but now I get a plain white background and whenever I go to change it, it sort of hangs for about 20 seconds, and then doesn't do it. Any idea what's going wrong?

Same here - it borked my system badly and I, with difficulty, followed the steps for removal. Grateful that things are back to normal now... As the tutorial warned, it doesn't look like this is yet ready for mainstream use.

---

### Post by jimbo99 on 2010-06-21
Actually you hit on a problem that demonstrates a problem with history.  In case you didn't know it, the Vista like transparency is a copy of compiz/beryl.  Those products were available to Linux users long before they were in Vista.  Microsoft essentially copied Linux in this regard.

I hope you'll take that forward with you.  Give credit where it is due.  Linux was the first to market with those features and remains king.

---

### Post by nilarimogard on 2010-06-23
> **ginjaninja405 said:**
> Thanks for the help, I've installed everything and followed the tutorial word for word, but now I get a plain white background and whenever I go to change it, it sort of hangs for about 20 seconds, and then doesn't do it. Any idea what's going wrong?

With a decent graphics card, it can't go wrong (unless you skipped a step or you're not using a theme with RGBA enabled). What can go wrong is that some apps might fail to start. At least that's the case for Lucid (I'm not sure about Karmic).

We'll probably get RGBA transparency included in the next Ubuntu 10.10 Maverick Meerkat.

---

