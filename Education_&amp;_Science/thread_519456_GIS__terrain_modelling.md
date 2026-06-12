---
title: "GIS / terrain modelling"
date: 2007-08-07
forum: Education &amp; Science
---

### Post by aquavitae on 2007-08-07
Hi

I have a very specific problem I need help with.  I need to generate the xyz coordinates for a series of cross-sections along a river.  I have a dtm file (x,y,z format) representing the ground surface and the coords of a series of points along the river.  Can anyone suggest some software which could do this?  Even python or c++ libraries would be fine, as long as they are relatively simple - this is quite urgent so I don't have time to learn a complicated api!

---

### Post by timmie on 2007-08-13
What about Qgis?

Or advanced: Grass.

To you simply want to plot or do some analysis, too?

Greetings,
Timmie

---

### Post by tgalati4 on 2007-08-13
Do you have access to the river?  If so, you can install gpsdrive on a laptop with a USB GPS device and capture a walking track along the river.  This will give you the GPS coordinates including altitude.

You can then import a satellite map of the region with gpsdrive and overlay the track that you walked.  If they match up sufficiently, you can Control-Click on the map to get other coordinates.  If the river doesn't show up on any maps, then you will have to take several points along the river to map it adequately.

---

### Post by aquavitae on 2007-08-14
Thanks for your replies.

I've had a look at qgis (which I though included grass - does it?), but it doesn't seem to do quite what I want - maybe I just don't know how to use it though.  Let me expain the whole problem and maybe you can advise.  I'm doing a floodline analysis of a river (with a few tributaries).  Basically all the information I have is a survey of the area from which I can generate a contour map.  The software I'm using to do the floodline is hec-ras (runs under windows - I can't find any linux software that will do it).  The input into hec-ras is the river layout (which I estimate by looking at the contours), and a series of sections across the river.  The trouble is in order to get any sort of accuracy I need about 1000 cross-sections, too many to do by hand.  I also need to be able to tweak the position of each section to make sure they don't cross each other.

So ideally I want something that can do it all in one go (including the floodline), but otherwise just a way of extracting the cross sections (as a list of xyz coords)  so that I can import them into hec-ras.

I don't have access to the river so I can't walk it.

Any advise?

---

