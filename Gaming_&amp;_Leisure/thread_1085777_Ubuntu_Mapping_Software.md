---
title: "Ubuntu Mapping Software"
date: 2009-03-03
forum: Gaming &amp; Leisure
---

### Post by ScruffyReid on 2009-03-03
A friend of mine has a small Nokia device that has a program called Maemo Mapper on it.  He has downloaded map repositories to it and can use it with a Bluetooth GPS dongle.

I have a Dell Mini and hoped to download a similar mapping program for it.  Does anyone know of a good mapping program that I could use to download map repositories into for Ubuntu?

---

### Post by omegamormegil on 2009-04-27
I'm in the same boat.  I want to find mapping software for my Dell Mini 9 too.  I'll let you know if I come up with something.

---

### Post by omegamormegil on 2009-04-27
So far the best and easiest option seems to be tangoGPS, available in the Ubuntu repository.  It works just like Maemo Mapper, but I'm not sure if it will give you directions like Maemo Mapper will.  tangoGPS downloads maps while you view them over an Internet connection.  You can later view the maps offline.  You don't need a GPS, but the software is designed to make use of one.

Another option is gosmore, also in the repository.  The interface seems to be of somewhat lower quality than tangoGPS, and at first glance there are no preferences available - I wanted to get rid of some extra place names the data gave me, but I couldn't find an option to do so.  Also, you can't just install the software from the repository and have it work.  First you need to download a map of your state or country from this site:  [http://downloads.cloudmade.com/](http://downloads.cloudmade.com/) (the map to get is <your state>.osm.bz2) and then on the command line, type > bzcat <state or country>.osm.bz2 | gosmore rebuild .  This will generate a map in gosmore from the data file you downloaded.  I also noticed that installing gosmore doesn't create an entry in the Ubuntu menu, so you can make one manually, or execute it from the Terminal or the Alt+F2 Run Application box.

Hope this helps.

---

