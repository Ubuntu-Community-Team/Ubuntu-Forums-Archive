---
title: "Installing Flight Gear in UBUNTU 6.06 - Best Method?"
date: 2008-04-04
forum: Gaming &amp; Leisure
---

### Post by Gehan on 2008-04-04
Hi

 I have tried to install Flight Gear 0.9.10   in Ubuntu 6.06

I have dowloaded some required  packages but it seems to be missing libcv6, although I installed it. 

Tried running in WINE but program ends when I select a plane

Anyone installed flight gear Windows version in WINE?

What is the best way install FG? I have a broadband connection to the 
Internet


Thanks

G

---

### Post by Gehan on 2008-04-04
OK so I used the Help in SYnaptic Package Manager and got it installed

But it does not run, now what?

g@g-desktop:~$ fgfs -v
freeglut (fgfs): Unable to create direct context rendering for window 'FlightGear'
This may hurt performance.
opening file: /usr/share/games/FlightGear/Navaids/carrier_nav.dat
/usr/share/games/FlightGear/Navaids/TACAN_freq.dat
fgfs: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
Aborted
g@g-desktop:~$

---

### Post by Gehan on 2008-04-19
Update 

The next step was to get a proper 3d accelerator card. The ATI card I had did not work with the Compaq Deskpro EN, so I ended up buying a  PIII with a 16 MB S3 AGP VGA card. That did the trick.

Using Synaptic to install FGFS was not successful, there was no icons no binaries anywhere, so I installed FGFS V 1.0 Windows version and it seems to run OK.

I have also installed X-Plane 5 and that  runs OK as well, frame rate is acceptable

All on the incredible WINE 

More testing to follow. I appears that it was the VGA card

---

### Post by Robin T Cox on 2008-04-19
> Using Synaptic to install FGFS was not successful, there was no icons no binaries anywhere, so I installed FGFS V 1.0 Windows version and it seems to run OK.

You can also download Flightgear from GetDeb and run it in Ubuntu direct:

[http://www.getdeb.net/search.php?keywords=flightgear]("http://www.getdeb.net/search.php?keywords=flightgear")

---

### Post by Perfect Storm on 2008-04-19
I hardly think that 6.06 can run it, as the .deb package are build with Gutsy dependencies/libs.

OP: I suggest that you move to a newer version of Ubuntu as 6.06 have very very soon seen its days (if possible).

---

### Post by Gehan on 2008-04-19
Thanks for you answers

I have with me Ubuntu 7.10 unfortunately it did not complete installing - could not read one little file and suggested I clean my CD. THe other time I installed it it would not let me login as root. Can't remember if I tried 

sudo passwd root 

FGFS runs OK in WINE, however I cannot see the listing in the installer, and need to get a better VGA card two weeks from now

BTW Joystick can be calibrated but I can just make shallow  right turns in FGFS, XPLANE and YS2000 Flight sim. Works OK with WIn 98 Baffling. But a separate topic

Next Step UBUNTU 7.10 and a 32 or 64 VGA card. I wihs FGFS would put an error message saying "Insufficient video RAM " or the  like

---

