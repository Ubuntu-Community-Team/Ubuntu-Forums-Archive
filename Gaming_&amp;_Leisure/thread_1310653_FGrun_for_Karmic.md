---
title: "FGrun for Karmic"
date: 2009-11-02
forum: Gaming &amp; Leisure
---

### Post by kainalu on 2009-11-02
Anyone figured out how to get FGrun for Flightgear for karmic? why isnt it just in the repos or included with install????? I have tried debs from 3 sites and compiling from source. 6 hours later, im giving up. I get some error no matter how I do it.

---

### Post by scotty64 on 2009-11-15
> **kainalu said:**
> Anyone figured out how to get FGrun for Flightgear for karmic? why isnt it just in the repos or included with install????? I have tried debs from 3 sites and compiling from source. 6 hours later, im giving up. I get some error no matter how I do it.

Same problem here. I wonder too why FGrun is not part of the Ubuntu package. Even the FlightGear website says that it is part of the package in some distros - so why not Ubuntu ?

---

### Post by kainalu on 2009-11-15
I dont know, Ive given up on FGRUN and wrote a basic BASH script to cover some of the functionality. FGRUN wont even compile from source for karmic.

---

### Post by carlleigh@gmail.com on 2009-12-02
Use FGO instead.
[http://www.flightgear.org/forums/viewtopic.php?f=6&p=54166](http://www.flightgear.org/forums/viewtopic.php?f=6&p=54166)

I downloaded fgo_091.tar.gz and extracted it to the home directory.
cd /home/xxxxxxxx                       (replace xxxxxxxx with your home directory).
tar -xvzf fgo_091.tar.gz

Changed to fgo and then data.
cd fgo/data 
or 
cd /home/xxxxxxxx/fgo/data                      (xxxxxxxx your home directory).

Using this config file. It works with Ubuntu 9.10, Gnome and Flightgear installed using Synaptic.
Supports multiplayer mode:
 
Edit /home/xxxxxxxx/fgo/data/config
-----------------------------------------------------
--aircraft=c172p
--airport=WSSS
--fg-root=/usr/share/games/FlightGear
--fg-scenery=/usr/share/games/FlightGear/Scenery
--runway=02C
AI_SCENARIOS=
FG_BIN=/usr/games/fgfs
HOME_DIR=/home/xxxxxxxx               (my home directory is /home/administrator)
LANG=en
TERRASYNC=0
TERRASYNC_PORT=5500
TERRASYNC_SCENERY=/usr/share/games/FlightGear/Scenery
xxxxxxxxxxxxxxxxxxx INTERNAL OPTIONS ABOVE. EDIT CAREFULLY! xxxxxxxxxxxxxxxxxxxx
#--runway=36
#--airport=YPXM
#--visibility=32000
--disable-fuel-freeze
--enable-real-weather-fetch
--units-feet
--timeofday=afternoon
--geometry=1024x768
--enable-panel
--multiplay=out,10,mpserver02.flightgear.org,5000
--callsign=xxxxxxx
--httpd=6500
#--altitude=4000
#--heading=45
#--in-air
#--lat=-20.56
#--lon=115.20
#--vc=115
# --enable-fullscreen
# --prop:/sim/frame-rate-throttle-hz=35
#--bpp=32
-----------
Replace HOME_DIR=/home/xxxxxxxx
With your home directory.

Replace --callsign=xxxxxxx with your own 7 digit callsign.
Which you can get by signing up at:
[http://fgfs.i-net.hu/modules/fgtracker/](http://fgfs.i-net.hu/modules/fgtracker/)

Replace --multiplay=out,10,mpserver02.flightgear.org,5000
With a server near you. 
I live in Singapore nearer the Hong Kong server than most of you.
====================================================
Run and test from CLI set up for GUI.

Edit /home/xxxxxxxx/fgo/fgo

fgo
------
!#/bin/sh
python /home/administrator/fgo/fgo.py

To test if from CLI.
cd /home/xxxxxxxx/fgo
gnome-terminal -e /home/administrator/fgo/fgo

Doesn't work check Issue: near the bottom of this note:
=====================================================

To start from GUI.
Add launcher to GNOME Panel.
Right click on Gnome Panel and choose 'Add to Panel'
Choose 'Custom Application Launcher' then the [   Add   ] button.

Create Launcher Dialog:
 -------------------------------------------------------------------------------------
|  Create Launcher
 -------------------------------------------------------------------------------------
|  Type: Application
|  Name: FGO
|  Command: gnome-terminal -e /home/xxxxxxxx/fgo/fgo   [ Browse...] 
|  Comment:
|  [ Help ]                                                             [ Cancel ] [   OK  ] 
 ------------------------------------------------------------------------------------- like that 
If it looks OK like that above. probably not 'xxxxxxxxx'. than choose OK  
(Your home directory instead of '/home/xxxxxxxx') 

Should now start from GUI.

-----------------------------------------
Issue:
If you have a problem try copying /home/xxxxxxxx/fgo/data to the home directory.
EG
cd /home/xxxxxxxx/fgo
cp -a data ../../

(Your home directory instead of '/home/xxxxxxxx') 
==================================================

I've never seen fgrun run (after many attempted compiles) and haven't seen a full description of what it does either. 
Now my question. Does fgo lack some functionality?

==================================================
After you've gotten your callsign to use the maps.
[http://http://mpmap02.flightgear.org/](http://http://mpmap02.flightgear.org/)

---

### Post by carlleigh@gmail.com on 2009-12-02
Sorry:  ../../ is wrong
---------------------------------------------------------------
Issue:
If you have a problem try copying /home/xxxxxxxx/fgo/data to the home directory.
EG
cd /home/xxxxxxxx/fgo
cp -a data ../

Correct

---

