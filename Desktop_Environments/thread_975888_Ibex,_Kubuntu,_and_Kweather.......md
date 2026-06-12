---
title: "Ibex, Kubuntu, and Kweather......"
date: 2008-11-08
forum: Desktop Environments
---

### Post by Skripka on 2008-11-08
I have a seemingly simple problem that I'm at a loss for:


How can I get a plasmoid on my KDE4 desktop to show a forecast?  This wouldn't on the surface seem that difficult.....




Kweather-I have installed via synaptic, and is not listed in the "Add Widgets Menu"...I can look and point at it under /usr/bin/ even.  I'm at a dead end here.

THIS widget: [http://www.kde-look.org/content/show.php/weatherforecast?content=92149](http://www.kde-look.org/content/show.php/weatherforecast?content=92149) , I follow the directions from the author and it spits out an error from CMake-and I cannot make or make install

From the above KDE-Look page, someone has kindly put that widget onto a Debian repo for easy download--so I followed his apt-get instructions, and installed it---but it is NOT listed under "Add Widgets".

I've tried a few Mac Dashboard widgets in plasma, and not only do they run terribly-and I cannot specify my location in them, rendering them useless.


Any ideas, I'm completely open-I like Ibex and KDE4 otherwise-all I ask is current weather conditions, and a few day forecast to be displayed-in a plasma widget.

---

### Post by krazyd on 2008-11-08
This is being worked on for inclusion in KDE 4.2 which is to be released in January. 

If you are *really* desperate for a forecast plasmoid, ask in the comments for the widget you linked on KDE-look.org, OR upgrade to [Project Neon]("https://launchpad.net/project-neon"), for nightly builds of KDE trunk (only do this if you don't mind regular breakage). I'm pretty sure the forecast widget is included.

---

### Post by aged hippy on 2008-11-09
I found this confusing, as well :) you need to <search> for *plasmoids* in Adept (or -- much simpler -- Synaptic) and add the ones you want, then they will appear in <Add Widgets>. 

Have Fun.:)

---

### Post by Skripka on 2008-11-09
> **aged hippy said:**
> I found this confusing, as well :) you need to <search> for *plasmoids* in Adept (or -- much simpler -- Synaptic) and add the ones you want, then they will appear in <Add Widgets>. 

Have Fun.:)

Already did this. they (plasmoids) are installed by and according to Adept Pacakage Manager, and I can point at them in in Dolphin in /etc/bin/ but they don't show up in Add Widgets....for kicks I tried installing the entire KDE toys module-and every single plasmoid listed in Adept....Kweather and the weather-forecast widget I linked to aren't list in Add Widgets.  That is the bizzao thing, the other official widgets appear in Add Widgets, but not these, even the OSX Dashboad widgets I briefly futzed with show up in the menu, but not Kweather or weather-forecast. :confused:

---

### Post by aged hippy on 2008-11-09
You probably need to log out (and in again :)) for them to be seen.

---

### Post by aged hippy on 2008-11-09
Rather than an edit:

If you add this to your sources.list:
deb [http://ppa.launchpad.net/samrog131/ubuntu/](http://ppa.launchpad.net/samrog131/ubuntu/) intrepid main
deb-src [http://ppa.launchpad.net/samrog131/ubuntu/](http://ppa.launchpad.net/samrog131/ubuntu/) intrepid main

There is also a widget to kill the slug - sorry, cashew.

---

### Post by Skripka on 2008-11-09
> **aged hippy said:**
> You probably need to log out (and in again :)) for them to be seen.

Grasshopper, I've rebooted and logged in and out 15 times in the last few days, and nada there--what the hay, I'll try your repos though....BRB

---

### Post by Skripka on 2008-11-09
> **aged hippy said:**
> Rather than an edit:

If you add this to your sources.list:
deb [http://ppa.launchpad.net/samrog131/ubuntu/](http://ppa.launchpad.net/samrog131/ubuntu/) intrepid main
deb-src [http://ppa.launchpad.net/samrog131/ubuntu/](http://ppa.launchpad.net/samrog131/ubuntu/) intrepid main

There is also a widget to kill the slug - sorry, cashew.

EXCELLENT! :popcorn:


Thx!!

---

