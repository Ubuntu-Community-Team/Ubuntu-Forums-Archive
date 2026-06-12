---
title: "Astronomical gear train/gear ratio calculation...take two"
date: 2014-08-25
forum: Education &amp; Science
---

### Post by David_Malphrus on 2014-08-25
I would like to add to an old closed thread:

Thread: [[COLOR=#dd4814]Astronomical gear train/gear ratio calculation tool for linux?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1480507")

Gear train to convert a solar day to a sidereal day (or vice versa)

Reference:

Title: The new definition of universal time
Authors: Aoki, S., Kinoshita, H., Guinot, B., Kaplan, G. H., McCarthy, D. D., & Seidelmann, P. K.
Journal: Astronomy and Astrophysics, vol. 105, no. 2

It lists the conversion factor as: 1.002737909350795 for January 1, 2000. This value needs a "smidgen" of correction over time.

The algorithm is 1.002737909350795 + 5.9006 10^-11 T - 5.9 10^-15 T^2

Where T is the number of Julian centuries (consisting of 36,525 days of 86,400 seconds of dynamical time each) elapsed since JD 2451545 TDB.

The elapsed time to current is 14 9/12 years or .1475 centuries for T meaning the present conversion is:

1.002737909359498256638125 (for September 1, 2014).

But, if this is used, you will have an error of X in your gear train in 100 years, so instead use a conversion factor that is correct 50 years into the future. Then, you would start with an error of .5X, end with an error of .5X and have (practically) no error at 50 years.

September 1, 2064 = .6475 centuries for T.

Conversion factor: 1.002737909388998911388125 (September 1, 2064).

 Now convert 1.002737909388998911388125 to proper fractions for the gears while constraining the conversion to four fractions:

 (233/359) * (346/317) * (358/304) * (363/302) = 1.0027379093889957827883714847908

 Gear-train error = 0.0000000000000031286

...hope this helps the OP of 'Astronomical gear train/gear ratio calculation tool for Linux?'

 Any thoughts, comments and/or corrections?


David Malphrus

---

