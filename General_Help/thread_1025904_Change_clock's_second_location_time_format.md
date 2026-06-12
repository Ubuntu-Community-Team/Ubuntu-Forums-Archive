---
title: "Change clock's second location time format"
date: 2008-12-30
forum: General Help
---

### Post by Roanoke on 2008-12-30
I use a custom format for my main clock. Here it is:
```
<span color='#2243bf'>%a, %b %d, %Y</span> <span color='#172d80'><b>%I:%M:%S %p</b></span>
```
I have a second location (Berlin) which I also keep track of, under the 'locations' menu. However, I want it to have 12 hour format, not 24 hour. I succeeded temporarily with this:
```
<location name="Berlin" timezone="Europe/Berlin" latitude="52.383335" longitude="13.516666" code="EDDB" current="false" format="12-hour"/>
```
But if I open and close the clock's calendar, it reverts to 24 hour. Could someone help me get it to be 12 hour constantly?

---

