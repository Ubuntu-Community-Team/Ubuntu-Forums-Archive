---
title: "Date applet not showing the wheather on the panel in 8.10"
date: 2009-01-07
forum: General Help
---

### Post by Tasc0 on 2009-01-07
I searched on the forum and I've found a couple of threads about this problem, but the only solution that's offered is to add the weather applet. I don't want to use that application. Besides, it should work with the date and hour app. It worked in 8.04.

The city is specified. When I click to show the weathers, it only shows a blank space.

---

### Post by redguru on 2009-01-07
I just added my location into the 8.10 date/time applet and now it's showing my current temperature and conditions.

---

### Post by redguru on 2009-01-07
[IMG]http://i40.tinypic.com/2qktapc.jpg[/IMG]

---

### Post by Tasc0 on 2009-01-08
> **redguru said:**
> I just added my location into the 8.10 date/time applet and now it's showing my current temperature and conditions.
Must be my location that it's not supported. What city did you specify? I'll try with that one.

---

### Post by Tasc0 on 2009-01-08
....

---

### Post by dcantin on 2009-01-08
I do have the same problem, even when I try with other locations in the preferences panel of the clock applet.

So far, I have tried :

- New York (New York City, Central Park), New York, United States
- Montreal (Pierre Elliot Trudeau International Airport), Quebec, Canada
- Sherbrooke, Quebec, Canada

With 8.04, it was working lawlessly with "Sherbrooke, Quebec, Canada"

---

### Post by sockrebel on 2009-01-08
try unclicking "show weather" and "show temperature" under preferences.
add your location
and then reenable those two.

it worked for me.
g'luck.

---

### Post by Tasc0 on 2009-01-08
> **dcantin said:**
> I do have the same problem, even when I try with other locations in the preferences panel of the clock applet.

So far, I have tried :

- New York (New York City, Central Park), New York, United States
- Montreal (Pierre Elliot Trudeau International Airport), Quebec, Canada
- Sherbrooke, Quebec, Canada

With 8.04, it was working lawlessly with "Sherbrooke, Quebec, Canada"
Yes, somebody needs to come up with a solution. Maybe an update?

> **sockrebel said:**
> try unclicking "show weather" and "show temperature" under preferences.
add your location
and then reenable those two.

it worked for me.
g'luck.

Didn't work. Thanks anyways.

---

### Post by eddy2009 on 2009-01-29
Hi there, not sure why this works but it does for me.  I had the exact same problem and what you need to do is click on the date.  Once the calendar shows up, click on "Locations".  Finally, click on "Set" next to the city and time.  That should do it.

---

### Post by ions on 2009-01-31
Thanks eddy, that fixed mine.

---

### Post by hwttdz on 2009-02-05
Another possible solution:

sudo dpkg-reconfigure tzdata
killall gnome-panel

The gnome-panel auto restarts so that's all you need to do.  The first command reconfigures the timezone data, don't know how exactly that's linked to the weather.  Principally posting so that when I change my location and break it again, I can find the solution!

---

### Post by Turtleman on 2009-06-17
Thanks Eddy! You rock!

---

### Post by MarkieB on 2011-03-30
no longer participating in ubuntuforums.org

---

