---
title: "[SOLVED] Cartograms?"
date: 2008-02-05
forum: Education &amp; Science
---

### Post by nemilar on 2008-02-05
I'm looking for a program that will allow me to create a cartogram.  I know that there is something you can do with the GNU R language (or something... not really clear on this) but it seems too complex.  

Is there any simple way to do this?  A GUI would be preferred, but something with a not-too-complex CLI is okay.

---

### Post by timmie on 2008-02-13
Hello,
would you please give us a meaingful example?

Kind regards!

---

### Post by nemilar on 2008-02-13
Of a cartogram?  It's just a map in which area is based upon a variable, rather than the actual area of the state/country/etc.  

[http://en.wikipedia.org/wiki/Cartogram](http://en.wikipedia.org/wiki/Cartogram)

[http://www.odt.org/Pictures/poplcart.jpg](http://www.odt.org/Pictures/poplcart.jpg)  is a really good example.  The size of the country on the map is determined by the size of its population.  Note that india and china are huge in relation to the rest of the countries in the world.  Canada is tiny.

---

### Post by timmie on 2008-02-14
Hello,
I never did prepare such a graph. Well, would be nice to know actually.

I imageine that there will be no easy GUI application.

Try generic mapping tools (GMT).

---

### Post by earlycj5 on 2008-02-14
Quantum GIS with PostGIS I imagine could work.

Quantum GIS and Grass might be an option as well.

---

### Post by nemilar on 2008-02-14
Ah, thank you for that recommendation!  I took a brief look at the website, it seems to be what I need.  Unfortunately, trying to install it creates package dependency problems.  I'll work through them tomorrow and report back.

---

### Post by earlycj5 on 2008-02-15
This *might* help but I don't know.

[https://wiki.ubuntu.com/UbuntuGIS](https://wiki.ubuntu.com/UbuntuGIS)

Sadly it looks out of date.  I flop between Kubuntu and openSUSE and right now openSUSE has much better support for GIS in the repositories from the way this looks (but it may not be the case).

---

### Post by nemilar on 2008-02-15
Hey, so I got GIS installed via the qgis package, and I've got it running successfully.  Some googling reveals that the GIS package is capable of creating cartographs, which is good news.  

The interface is a bit complex; I was hoping for something nice-and-simple, but I'll do my homework and figure out how to work this thing :)

Thanks very much you guys, for helping me out!  Thanks-clicks are coming your way :)  I'm going to mark this thread as solved, since my question (what program can create cartographs) has been answered.

Many thanks!

---

### Post by earlycj5 on 2008-02-16
> **nemilar said:**
> Hey, so I got GIS installed via the qgis package, and I've got it running successfully.  Some googling reveals that the GIS package is capable of creating cartographs, which is good news.  

The interface is a bit complex; I was hoping for something nice-and-simple, but I'll do my homework and figure out how to work this thing :)

Thanks very much you guys, for helping me out!  Thanks-clicks are coming your way :)  I'm going to mark this thread as solved, since my question (what program can create cartographs) has been answered.

Many thanks!

Glad it will work for you.  :KS

---

