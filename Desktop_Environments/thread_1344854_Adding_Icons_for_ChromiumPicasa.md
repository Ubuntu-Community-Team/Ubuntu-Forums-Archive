---
title: "Adding Icons for Chromium/Picasa"
date: 2009-12-03
forum: Desktop Environments
---

### Post by RiazM on 2009-12-03
I have high resolution images for these applications, does anyone know how I would go about adding them to my current icon pack so that they show up when I run the programs from gnome-do?

---

### Post by ayampanggang on 2009-12-05
my questions exactly. Is there any general way of replacing all the icons of all applications with the high res ones?

As for google chrome, i think you simply go to /opt/google/chrome then replace all the product_logo_xx.png with your high res one where xx is the size of the icons, e.g. in my case there's 32, 48, and 256.

But when you upgrade your chrome it will get overriden by the default so you might have to do that everytime theres upgrade to chrome

---

### Post by RiazM on 2009-12-06
To replace all icons with hi res ones, go to Preference>Appearance, select customise and then the icons tab. Many of the icon sets there have SVG scalable graphics and look better in general. I recommend gnome-colours which you can install with

sudo apt-get install gnome-colors

I've replaced my picasa icon by replacing the .xpm file located in /opt/google/picasa/3.0/desktop/ with a higher resolution one. However I am still stuck on Chromium, and Spotify, which is running in WINE.

---

### Post by RiazM on 2009-12-06
Ah, I solved my problem by following these instructions:

[http://life-the-universe-and-stuff.blogspot.com/2009/07/i-really-like-gnome-do-but-thing-that.html](http://life-the-universe-and-stuff.blogspot.com/2009/07/i-really-like-gnome-do-but-thing-that.html)

---

### Post by RiazM on 2009-12-06
Ah, I solved my problem by following these instructions:

[http://life-the-universe-and-stuff.blogspot.com/2009/07/i-really-like-gnome-do-but-thing-that.html](http://life-the-universe-and-stuff.blogspot.com/2009/07/i-really-like-gnome-do-but-thing-that.html)

---

