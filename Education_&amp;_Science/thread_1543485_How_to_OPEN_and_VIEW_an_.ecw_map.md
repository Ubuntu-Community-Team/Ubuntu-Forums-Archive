---
title: "How to OPEN and VIEW an .ecw map ?"
date: 2010-08-01
forum: Education &amp; Science
---

### Post by asbesto on 2010-08-01
Look my last message for the howto ;)

Hi,

I have this big huge file in .ecw format, it's a 1:25000 map of a part of Sicily.

I can't find any program to open and show this map!

Can someone help me? 

What I need if exist, is only a simple program that show me the map on the screen to print some parts of it, not a complicated GIS library of programs :)

---

### Post by howefield on 2010-08-01
Have you tried the suggestions here ?

[http://www.tuxradar.com/answers/208](http://www.tuxradar.com/answers/208)

---

### Post by asbesto on 2010-08-03
Just found a way to do this. 

Assuming you have a very BIG HUGE .ecw file, 

Download  [http://fwtools.maptools.org/](http://fwtools.maptools.org/)

Unpack it into a directory, for example fwtools/

```

cd fwtools/; ./install.sh

```

Enter in fwtools/bin_safe/ and launch "openev" 
(you can use "openev -h" if you have graphic acceleration)

Use File->Open subarea; 

Select your file

Use "Geodetic" for coordinate selection

Specify the section you want to display and ENJOY YOUR MAP :)

P.S. don't open bug huge regions or your entire map, you can fill your RAM!

):P:lolflag::guitar:

---

