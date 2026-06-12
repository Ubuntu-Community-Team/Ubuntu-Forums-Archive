---
title: "Installation of an IMS Viewer"
date: 2008-09-05
forum: Education &amp; Science
---

### Post by R.Bucky on 2008-09-05
I am hosting my domain using a LAMP server (7.10) and would like to install the equivalent of an ArcIMS viewer to 'stream' spatial data. Has anyone in the community installed such a system and what open-source software is available? 

Mark
[http://buckyspalace.net](http://buckyspalace.net)
[email]mark@buckyspalace.net[/email]

---

### Post by timmie on 2008-09-11
You may check here:
[http://www.freegis.org/database/?cat=9](http://www.freegis.org/database/?cat=9)

Most common solution these days seems to be Mapserver+Openlayers.

Or [http://featureserver.org/](http://featureserver.org/)

---

### Post by Nick Lake on 2008-10-01
Yep MapServer.... any OGC WMS / WFS compliant service should do though.

Interestingly someone tried to build a WMS service on the QGIS libraries:
[http://www.foss4g2006.org/contributionDisplay.py?contribId=123&sessionId=41&confId=1](http://www.foss4g2006.org/contributionDisplay.py?contribId=123&sessionId=41&confId=1)
Don't know what happened to it though.

It would also be possible to build something on GRASS (although it would probably be a pain in ****).

Never installed MapServer - all ESRI shop at work unfortunately.

Good luck - I'll visit your website to check up!

- Nick

---

### Post by Nick Lake on 2008-10-01
Check this out... [http://www.gisvm.com/](http://www.gisvm.com/)

---

### Post by R.Bucky on 2008-10-03
Yes, ESRI at my shop too. I keep threatening to install a dual boot on my work computer, but the IT guys just scowl. Thanks all for the suggestions.

---

