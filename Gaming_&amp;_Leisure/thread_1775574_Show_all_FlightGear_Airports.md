---
title: "Show all FlightGear Airports"
date: 2011-06-04
forum: Gaming &amp; Leisure
---

### Post by lkjoel on 2011-06-04
Hi!
I want to know all currently available FlightGear Airports with their Runways.
Does anyone know how to do this?

---

### Post by mips on 2011-06-05
Do you have the complete scenery installed as the airports available are dependent on the scenery installed?

With FGo! installed I get a list of airports in the top left of the window.

Else maybe look here [http://wiki.flightgear.org/Category:Airports](http://wiki.flightgear.org/Category:Airports)

---

### Post by ubudog on 2011-06-05
> **mips said:**
> Do you have the complete scenery installed as the airports available are dependent on the scenery installed?

With FGo! installed I get a list of airports in the top left of the window.

Else maybe look here [http://wiki.flightgear.org/Category:Airports](http://wiki.flightgear.org/Category:Airports)

Is there a place to download all the scenery at once?

---

### Post by lkjoel on 2011-06-05
Sorry, I wasn't clear enough.
Does anyone know a terminal command to find all available FG Airports with their runways?

---

### Post by lkjoel on 2011-06-05
> **ubudog said:**
> Is there a place to download all the scenery at once?
Yes!
Type this into a Terminal window:
```
cd /usr/share/games/FlightGear/
sudo mv Scenery Scenery1
sudo svn checkout http://terrascenery.googlecode.com/svn/trunk/data .

```
And then wait around 24 hours for it to download :P.

To update the scenery:
```
cd /usr/share/games/FlightGear/Scenery
svn up

```

---

### Post by ubudog on 2011-06-05
Cool, thanks.

---

