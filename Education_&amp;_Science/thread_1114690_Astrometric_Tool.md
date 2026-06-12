---
title: "Astrometric Tool"
date: 2009-04-03
forum: Education &amp; Science
---

### Post by I eat coffee! on 2009-04-03
I was in search of a tool that could exact RA and Dec coordinates of any given starfield. This is all for a photometry project I am working on. The photometry project aims to observe large portions of sky at a very low cost as much as weather permits. Then the system would record the data for analysis. The other giant aim is to do all this automatically. I am currently the only one involved but, if anyone else wants to contribute they only need to message me. 

The website [http://www.astrometry.net/]("http://www.astrometry.net/") hosts an interesting program. This program can take an starfield image and transform it into coordinates. You must receive permission for access to the indexes these are the "maps" that the software uses to solve the stars in the field. I think your images need to be in the .fits format but, I am not 100% sure. Anyways, any astrophysicists should definitely check this website out. I hope this provokes some conversation! 

I ran a test of the program and it performed its task well

joseph@joseph-laptop:~$ /usr/local/astrometry/bin/solve-field '/home/joseph/Desktop/FITS TEST/zenith-006.fit'
Reading input file 1 of 1: "/home/joseph/Desktop/FITS TEST/zenith-006.fit"...
Extracting sources...
simplexy: found 374 sources.
Solving...
Field 1 did not solve (index index-219.fits, field objects 1-10).
Tweaking!
Field 1: solved with index index-218.fits.
Field 1 solved: writing to file /home/joseph/Desktop/FITS TEST/zenith-006.solved to indicate this.
Field 1: solvedfile /home/joseph/Desktop/FITS TEST/zenith-006.solved: field has been solved.
Creating new FITS file "/home/joseph/Desktop/FITS TEST/zenith-006.new"...
Field center: (RA,Dec) = (152.4, 52) deg.
Field center: (RA H:M:S, Dec D:M:S) = (10:09:37.7, +52:00:17.4).
Field size: 42.3116 x 28.901 degrees
Creating plots...
Your field contains:
  Part of the constellation Ursa Major (UMa)
  Part of the constellation Lynx (Lyn)

[IMG]http://i30.photobucket.com/albums/c307/joerules22/zenith-006-ngc.png[/IMG]

):P

---

