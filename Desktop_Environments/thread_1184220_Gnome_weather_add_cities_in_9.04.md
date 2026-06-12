---
title: "Gnome weather: add cities in 9.04?"
date: 2009-06-10
forum: Desktop Environments
---

### Post by Clancy_s on 2009-06-10
Summary - in 9.04 I can't find the config file that gnome is using for the weather applet, I wonder if someone knows which and where it is?

I live in a regional town in Australia (Newcastle), with an airport with an online weather station (YWLM).  I like to use that station for my weather applet instead of Sydney, which is 150k away.

Newcastle has never been big enough to be included in the default pick list.  I can cope with that, so long as I can get access to the config file and add it.  For ubuntu 7.10 that was Locations.xml under /usr/share/gnome-applets/gweather.  In 8.10 it was in /usr/share/libgweather.

With 9.04 I can't find the file that gnome is using, and having indavertently selected a new station I've lost my local weather monitor - I can't get it either in the standalone gnome weather applet or in the one built into the clock.

I've have my custom Locations.xml in

/usr/share/gnome-applets/gweather 
/usr/share/libweather
and also
usr/share/evolution(something I've forgotten)

which are the only places I can find a native copy, to no effect.  I'm presuming the new version of gnome is getting it's info from a new file, does anyone know where?  I've tried google and some general gnome sites, no joy.

I know I could use conky but since all I want is the weather I'm hoping for a simple answer.

---

### Post by Sarai the Geek on 2009-06-10
On my machine, there is a Locations.xml located at:

/usr/share/libgweather
/usr/share/evolution-data-server-2.26/weather

Hope that helps!

---

### Post by Clancy_s on 2009-06-12
Alas, allowing for my faulty memory, those are the ones I've replaced.

Thanks for trying though

---

### Post by sawjew on 2009-07-15
Did you find out where the locations.xml file is?  The one in /usr/share/evolution-data-server-2.26/weather only has US cities in it.  I want to add information for Renmark Airport, SA as my closest weather station.

---

### Post by Stainesy on 2009-07-15
My Coolangatta Airport location is in /usr/share/libgweather/Locations.xml

---

### Post by Clancy_s on 2009-07-17
> **Stainesy said:**
> My Coolangatta Airport location is in /usr/share/libgweather/Locations.xml

Thanks for the push - that turns out to be the place to add new cities.  The reason I was having a problem turns out to be that the format of Locations.xml has changed and I was trying to use the old one I made for 7.10 (worked through to 8.10).

I had to edit the new one and add in my city.  As an example this is my addition


```
<city><name>Williamtown</name><coordinates>-32.793200 151.8359</coordinates><location><name>Williamtown Airport</name><code>YWLM</code><coordinates>-32.793200 151.8359</coordinates></location></city>
```

I added it alphabetical order in the state section (NSW, which already existed.  I logged out and in and Williamtown is now on the list and seems to work correctly - the data matches what I get from a direct lookup. :)

eta: gedit got indigestion, I used open office word on a copy I'd made then a root version of nautilus to add it back to /usr/share/libgweather/, having first renamed the original Locations.xml to Locations.bkp in case I borked something.

---

