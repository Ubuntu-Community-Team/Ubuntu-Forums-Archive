---
title: "QGIS 0.8 in Feisty?"
date: 2007-04-23
forum: Education &amp; Science
---

### Post by earlycj5 on 2007-04-23
Reading Launchpad it states:

> The package versions that were published when the distribution release was made. For releases that are still under development, packages are published here only.


So where's QGIS 0.8 in Fiesty?  It's been out since December of last year.

I'm going crazy trying to install it myself.  There's packages for Edgy available but not Feisty and I apparently incorrectly assumed it would be in this release of Kubuntu.  :(

---

### Post by nss0000 on 2007-04-23
BigE:

I've just installed, and am running  QGIS_0.74 & GRASS_6.0.x in DAPPERx64 ... because of the installation problems you mention. Have *NOT* tried to install newer versions -- or looked at PostGresql.

My impression is that x64 "stuff" finds spotty UBUNTU support. Anyrate it'll be a couple weeks at-least before I try updating to newer versions of QGIS & GRASS.   

nss
******

---

### Post by earlycj5 on 2007-04-25
> **nss0000 said:**
> BigE:

I've just installed, and am running  QGIS_0.74 & GRASS_6.0.x in DAPPERx64 ... because of the installation problems you mention. Have *NOT* tried to install newer versions -- or looked at PostGresql.

My impression is that x64 "stuff" finds spotty UBUNTU support. Anyrate it'll be a couple weeks at-least before I try updating to newer versions of QGIS & GRASS.   

nss
******

This is/was on my laptop, a i686 machine, not my x64 desktop.  The x64 is a whole nuther comfuction untu itself with QGIS.  :)

---

### Post by nss0000 on 2007-04-26
BigE:

Have you considered FEISTY_Fawn is as-per-name an immature product. I read lots of problems folks are having in general. While DAPPERx64 even with the x64_holes in HW/SW behaves more robustly. 

Anyrate I'm really impressed with GRASS_6 displays since I looked at GRASS_4 years ago.  I'm wondering what advantage QGIS brings to the table? Working my way thru the SWORDFISH60 sample data and GRASS processing functions. Lots of time since I recently retired ... and figure to start something new.  

Sure wish I'd treated myself to a new 30" monitor ...%^]

BTW: GRASS_6.0 does NOT seem to employ both CPUs in my AMD5400+. While processing I get ~70% / 2% usage on the pair.

nss
*******

---

### Post by earlycj5 on 2007-04-26
BigE?  I kinda like that.  :guitar: 

I'm using GRASS within QGIS or QGIS as a frontend for GRASS and other GIS tools.

I find that the power of QGIS isn't what IT can do but rather what it allows me to do.  I can integrate PostGIS and GRASS in a relatively intuitive interface.  Really I'm just beginning to scratch the surface of what I can do with GRASS/PostGIS/QGIS.  Problem is, when you take classes all they teach you is ESRI.

I wish I'd treated myself to a better laptop now that I'm using it for GIS work.  Ah well, once my funding comes through for the new project I should be getting a new work computer.  :)

---

### Post by nss0000 on 2007-04-27
BigE:

Got to "pushing" my GRASS install this morning -- using the SWORDFISH60 datasets. NVIZ enabled. Several maps displays simultaneous open, with various combos of proceedures requested. What I found was:

1) Both CPUs are being used 60%-90% during stat&matrix ops ... that's good!
2) freq_scaling quickly changes 1Ghz--> 2.8Ghz ... that's good!
3) Once/twice/hr the GRASS_GIS_manager gets trashed (overwritten) as various dropdown boxes come-and-go. Then, with both CPUs=100% the proggie hangs and I have to kill it from the shell or by closing the CLI_terminal ... that's terrible !!!  %^[ 

Do you think I'm "over-reaching" system hardware:  AMD5400+ / 2G ram / NV7600gs vid ,
or am I looking at GRASS_6.0.1 software bugs ? 
BTW: UBUNTU_repos LM-Sensors (2.9) does NOT function for my ASUS-M2N mobo, so I don't know sys_temps sec-by-sec. Whenever I check BIOS I see ~30-40C for mobo/cpu.

nss
******

---

### Post by earlycj5 on 2007-04-30
It's got me, I somehow suspect it's the program myself.

I've not pushed x64 at all.  I'm just learning Grass, most of my work is using PostGIS stuff right now and Grass for the occasional vector manipulation.

---

