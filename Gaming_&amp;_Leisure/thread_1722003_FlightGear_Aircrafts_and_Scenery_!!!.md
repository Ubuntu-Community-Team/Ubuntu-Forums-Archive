---
title: "FlightGear Aircrafts and Scenery !?!?!"
date: 2011-04-05
forum: Gaming &amp; Leisure
---

### Post by moehabibi on 2011-04-05
Hello guys ... 

iv been playing FlightGear for the past 3 days ... and im sick of the default plane. I wanna download more but i dont know how ! 

there is no /usr/shared/...../aircraft
Or  usr/shared/......./world scenery !

all i have is /usr/.fgfs/aircraft-data.


im extracting the plane data to that folder but i dont know how to open it up ... there no menu to select the aircraft ?

and what about the scenery i dont know where to extract it too 

btw im using UBUNTU 10.10 

iv been searching for SOOO long and NOTHING seems to work and most posts are for 9.10 and below (ubuntu)

---

### Post by GWBouge on 2011-04-05
The ~/.fgfs/aircraft-data directory is for saving your preferences for specific planes, such as your Nav's, Com's, switches, etc.  When you download aircraft or scenery, you can either put it in the default locations (/usr/share/games/FlightGear/Aircraft and /usr/share/games/FlightGear/Scenery ... note:  you will need root privileges to extract to these locations.  'gksu nautilus' to open up nautilus with privileges, navigate to the archive, and extract it to the right folder), or you can create a folder in your /home/user directory to get around the privileges, but you will have to let FlightGear know about these directories.

Have you gotten a GUI launcher for it yet?  [FGrun]("http://sourceforge.net/projects/fgrun/") seems to be the tried and true, however it's a little 'heavy' and requires compilation ... alternatively, there's [FG Flier]("http://sourceforge.net/projects/fgflier/") and [FGo]("http://sites.google.com/site/erobosprojects/flightgear/add-ons/fgo")

---

### Post by Rytron on 2012-02-24
How do I select a new plane?

Edit:
Example:
```
fgfs --aircraft=CitationX
```

---

