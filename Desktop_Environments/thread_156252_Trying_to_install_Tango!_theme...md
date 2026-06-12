---
title: "Trying to install Tango! theme.."
date: 2006-04-06
forum: Desktop Environments
---

### Post by anodizer on 2006-04-06
From the official tango project site:
You will need the following packages for a successful installation:

    * GNU Automake 1.9.x and friends
    * ImageMagick version 5.5.7 or greater
    * pkgconfig version 0.19 or greater
    * XML::Simple Perl Module 

I already have ImageMagick installed, version 6:6.2.3.4-1ubuntu1.1. However, when I try to compile the tango icon theme, I'm getting this error: ```
configure: error: ImageMagick is required to build tango-icon-theme
```
Should I install the current Imagemagick version from source?

---

### Post by aCiD2 on 2006-04-06
Looks like you need lib-magick-dev :) Try:

```
sudo apt-get install libmagick6-dev imagemagick
```

---

### Post by anodizer on 2006-04-06
Yay it worked! Thnx

---

### Post by K.Mandla on 2006-04-06
Just as a note, I know there are quite a few Tango fans out there, myself included. For speed and ease of installation, I've been using packages posted at gnome-look.org.

[http://www.gnome-look.org/content/show.php?content=33959](http://www.gnome-look.org/content/show.php?content=33959)

That's the suite page that collects a bunch of other Tango posts into one place. Most of those will install through the Theme menu under System > Preferences. 

Anyway, it's just an idea.

---

### Post by anodizer on 2006-04-06
[QUOTE=K.Mandla]Just as a note, I know there are quite a few Tango fans out there, myself included. For speed and ease of installation, I've been using packages posted at gnome-look.org.

[http://www.gnome-look.org/content/show.php?content=33959](http://www.gnome-look.org/content/show.php?content=33959)

That's the suite page that collects a bunch of other Tango posts into one place. Most of those will install through the Theme menu under System > Preferences. 

Anyway, it's just an idea.[/QUOTE]

Yes I knew that, it is an option, but in my opinion it's better to compile it, cause some other icon themes like OSX version 3, requires Tango to be "properly" installed in order to work.

---

