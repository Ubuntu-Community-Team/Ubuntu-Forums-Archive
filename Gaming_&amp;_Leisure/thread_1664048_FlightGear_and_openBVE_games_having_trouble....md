---
title: "FlightGear and openBVE games having trouble..."
date: 2011-01-10
forum: Gaming &amp; Leisure
---

### Post by AdrenalinPlease on 2011-01-10
For some reason I cant figure this out, well probably because I just started using Linux.

Anyway heres the deal: I downloaded a bunch of scenery and aircraft from Flightgear website. I tried copying it into their respective folders (aircraft/scenery) but it wouldnt let me since it said I didnt have certain permisions. I googled and found out about nautilus gsk or something like that so that I can open folders with admin priveleges, I also installed 7zip. So I finally copied the folders where they need to be and extracted them. Ran Flightgear and couldnt find any aircraft other then the cessna and couldnt load any other locations than it came with. Boo. 

openBVE: downloaded a bunch of routes from different sites along with some trains, same thing. None of the trains show up, the routes however show the folders but no actual routes.

What gives? Is it me, probably, but can someone help me do this step by step so I can have more inside these games?

Ubuntu 10.10 newbie please help.

---

### Post by AdrenalinPlease on 2011-01-11
54 views and not a single reply?

---

### Post by Quadunit404 on 2011-01-11
Hit Ctrl+F2, then type in gksudo nautilus /path/to/flightgear/data

Obviously replace /path/to/flightgear/data with the actual directory. Since I have FlightGear installed locally I don't know the path to fgdata.

---

### Post by AdrenalinPlease on 2011-01-12
> **Quadunit404 said:**
> Hit Ctrl+F2, then type in gksudo nautilus /path/to/flightgear/data
 
Obviously replace /path/to/flightgear/data with the actual directory. Since I have FlightGear installed locally I don't know the path to fgdata.
 
That is to do what? For the scenery or aircraft?

---

### Post by Sebedee on 2011-01-18
Hi I am having the same problem I have found other planes but cannot add anything to the simulator such as planes and scenery I have currently downloaded two areas and really would like to know how to put them on i am really not very good with ubunto so I would like a simply step by step to help me out please thanks.

---

### Post by Quadunit404 on 2011-01-19
> **AdrenalinPlease said:**
> That is to do what? For the scenery or aircraft?

That is for both :wink:

Of course, it's much, MUCH easier to just [compile FlightGear like this]("http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu") since FlightGear would be installed in your home directory and therefore you can do whatever the hell you wish with it much easier than installing it through the USC whether it be adding scenery or aircraft.

---

