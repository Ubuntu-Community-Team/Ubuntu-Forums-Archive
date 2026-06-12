---
title: "1680x1050 not recognized on xubuntu 7.10 tribe4 !?"
date: 2007-08-21
forum: Development CD/DVD Image Testing
---

### Post by roots on 2007-08-21
hi there, i just gave the xubuntu tribe 4 live cd (32bit) a shot on my desktop pc. however, i'm facing the well-and-long known problem that the screen resolution is not recognized properly.

i was hoping that with xorg 1.3 and xrandr 1.2 a new aera of X was about to begin, but again i do end up with ugly 1280x1024 instead.

according to xorg.0.log, xorg is using the vesa driver for my ati card which is fine in first place, as i'm going to use the system only as productive environment, that is, no 3D.

my lg tft display is recognized fine, including the "additional mode" 1680x1050, but, as can be read some lines further, xorg can't use the resolution because there is "no mode of this name".
 
i can't tell you how much i'm fed up with this line as i've spent weeks to get the very same display working on my notebook in the past, which was solved due to xrandr 1.2. 

not so on my desktop pc, i've spent a day trying to get the desired wide screen resolution to work, but no success.

any suggestions!?

should i file this as a bug? i know that there are issues with ati drivers etc., especcially with newer cards like mine is, but as i'm only using the vesa driver, basic things like proper screen resolution should at least work?!


cheers,
roots.


my specs: 

athlon 64x2 4000+
asus m2n-e
ati x1950xt @ pcie
2gb patriot ddr2
sound blaster audigy
hdd, cdr, bla.

display: lg l226wtq-sf

---

### Post by jerrylamos on 2007-08-24
Might be worth your while to try Gutsy Tribe 5 build as of Thursday 8/23.  Tribe 4 had Xwindow support problems for me, big time, Tribe 5 working much better.

Cheers, Jerry

---

