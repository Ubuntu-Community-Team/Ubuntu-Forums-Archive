---
title: "Getting boundaries for GMT maps"
date: 2007-04-30
forum: Education &amp; Science
---

### Post by timmie on 2007-04-30
Hello,
I'm just starting to learn GMT map plotting.

I've git a question about it:

Hhow you normally get the boundaries of your maps.

[list]
[*]  Do you use Google Maps / Earth?

[*] Do you use a conventional atlas?

[*] Or what else?
[/list]
Of course, I am referring to more general maps which do not plot your own measurement locations which you
know my heart.

---

### Post by seatopia on 2007-05-10
If by "boundaries" you mean things like land masses and coastlines, gmt has them built-in.  There are different resolutions available, ranging from crude to full resolution; the data files are installed when you install gmt.  If you make a map with pscoast, for example, just enter the boundaries of your region of interest (-R w/e/s/n) and it will add the land masses.  You can specify the resolution via the -D flag.

There are a ton of options available with GMT, and I'm still in the learning stage myself.  Try going through the tutorial examples and cookbook, I find them useful.

---

### Post by timmie on 2007-05-14
> **seatopia said:**
>  just enter the boundaries of your region of interest (-R w/e/s/n) and it will add the land masses.  You can specify the resolution via the -D flag..
That was acctually what I am aiming at. Let's say you wanna map the port of Marseille. Where to you take the coordintes from?

> **seatopia said:**
> 
There are a ton of options available with GMT, and I'm still in the learning stage myself.  Try going through the tutorial examples and cookbook, I find them useful.
Yes, there are tutorials. But the program as such a bunch of options. And sometimes they seem to contradict for not to combine in the eyes of a novice.

---

### Post by seatopia on 2007-05-14
[quote=timmie;2651732]That was acctually what I am aiming at. Let's say you wanna map the port of Marseille. Where to you take the coordintes from?

In that case I generally look at an atlas or website to figure out the coordinates I want.

---

