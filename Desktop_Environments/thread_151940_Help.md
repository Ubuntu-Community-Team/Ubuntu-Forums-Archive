---
title: "Help"
date: 2006-03-28
forum: Desktop Environments
---

### Post by xlib on 2006-03-28
I just installed Kubuntu to my other computer. And I just compared the two in the ubuntu webpage. I went and looked at the screenshot page. 
[http://www.ubuntu.com/screenshots](http://www.ubuntu.com/screenshots)
Mine does not look like this and I was wondering if my version is out of date or something of the sort..

---

### Post by Jucato on 2006-03-28
Um... you installed Kubuntu, which uses KDE.
The screenshots you are looking at is Ubuntu, which is using GNOME.
That's why they are different
Here are screenshots for Kubuntu: [http://shots.osdir.com/slideshows/slideshow.php?release=470&slide=4&title=kubuntu+5.10+screenshots]("http://shots.osdir.com/slideshows/slideshow.php?release=470&slide=4&title=kubuntu+5.10+screenshots")

---

### Post by Bukunut on 2006-03-29
Ignore post, I got it back to front.! aysiu got it the right way round... 
too much coffee me thinks..
Bukunut

---

### Post by aysiu on 2006-03-29
[QUOTE=xlib]I just installed Kubuntu to my other computer. And I just compared the two in the ubuntu webpage. I went and looked at the screenshot page. 
[http://www.ubuntu.com/screenshots](http://www.ubuntu.com/screenshots)
Mine does not look like this and I was wondering if my version is out of date or something of the sort..[/QUOTE] If you want screenshots of **K**ubuntu, go [here](http://shots.osdir.com/slideshows/slideshow.php?release=594&slide=3&title=kubuntu+6.04+flight+5+screenshots). Otherwise, what you need is the *ubuntu-desktop* package, which will install Gnome on top of your current KDE one: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` Log out, click on "session," and select "Gnome." Log back in. Voila! You have something to match the Ubuntu screenshots.

---

