---
title: "How do I install custom firefox icons?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by randell6564 on 2006-08-01
OK.., Thanks to the folks here at ubuntu forums, I finally figured out how to install fonts from gnome-look.org.

NOW, I found some really Beautiful icons for mozilla firefox.

They are just .png images that I got here:[http://www.gnome-look.org/content/show.php?content=14560](http://www.gnome-look.org/content/show.php?content=14560)

I'm assuming that they are icons that will display on my panel and Applications>internet.

Where do I put them in my file system?

Thanks Folks!

---

### Post by neoeden on 2006-08-01
Checkout /usr/share/pixmaps/ . Since it is owned by root, your going to need to be root to move the icons there.

---

### Post by aarbear26 on 2006-08-01
actually you can put them anywhere you want, but rightclick on the icon that is now firefox and hit properties.  click on the icon picture and navigate to the directory of your new icon.  select it and viola, pretty icons

---

### Post by neoeden on 2006-08-01
Good to know. I didn't realize that. :)

---

### Post by randell6564 on 2006-08-01
> **aarbear26 said:**
> actually you can put them anywhere you want, but rightclick on the icon that is now firefox and hit properties.  click on the icon picture and navigate to the directory of your new icon.  select it and viola, pretty icons

Got It!  Well ALRIGHT!! Thanks a lot!  Looks great, but is there a way to make it the universal icon for firefox on my box?

Right now, I can only get it on my panel as a quick launch button.

---

### Post by aysiu on 2006-08-01
[This](http://ubuntuforums.org/showthread.php?t=199193) should help you.

---

### Post by randell6564 on 2006-08-01
> **aysiu said:**
> [This](http://ubuntuforums.org/showthread.php?t=199193) should help you.


Hey aysiu!  Hows it going?  

Thanks for the link, but I want the firefox icons that I downloaded from gnome-look.org

Here:[http://www.gnome-look.org/content/show.php?content=14560](http://www.gnome-look.org/content/show.php?content=14560)

One of these is the one that I want to make the universal firefox icon on my box.

---

### Post by aysiu on 2006-08-01
The script gives you an idea of where these icons are located:

/usr/share/pixmaps/firefox.png
/usr/share/pixmaps/mozilla-firefox.xpm
/usr/lib/firefox/icons/default.xpm
/usr/lib/firefox/chrome/icons/default/default.xpm
/usr/lib/firefox/icons/document.png

---

### Post by randell6564 on 2006-08-01
> **aysiu said:**
> The script gives you an idea of where these icons are located:

/usr/share/pixmaps/firefox.png
/usr/share/pixmaps/mozilla-firefox.xpm
/usr/lib/firefox/icons/default.xpm
/usr/lib/firefox/chrome/icons/default/default.xpm
/usr/lib/firefox/icons/document.png


OK.,

So, can I place these icons in anyone of those folders?

They are all .png so maybe /usr/share/pixmaps/firefox.png

---

### Post by srunni on 2006-08-01
I'm guessing you would have to go to Terminal/Konsole and type ```
sudo cp [location of new icon] /usr/share/pixmaps/firefox.png
```

and

```
sudo cp [location of new icon] /usr/lib/firefox/icons/document.png
```

---

