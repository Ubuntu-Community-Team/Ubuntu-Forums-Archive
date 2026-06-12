---
title: "compiz flickering"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by Cresho on 2007-12-02
Im running a am2 6400 black edition with the 8800gt (nvidia beta drivers).  I added in sessions "nvidia-settings --load-config-only" without parenthesis.  in the "nvidia x server settings", i am using texture sharpening, anisotrphic and antiliasing settings maxed out.  I activate compiz and it runs smooth, no jaggy edges, screen is silky smooth even after reboot.  I open up a game running this script
-------------------------------------------------------------------------------
#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
cd /home/ranxerox/Installed_Programs/Typhoon_2001
./typhoon

#Compiz on;
compiz --replace &


-------------------------------------------------------------------------------


after It closes, everything is peachy again...until i open a wine program.  when it launches, my screen flickers like crazy.  This problem is totally avoided when i disable everything in the antialiasing settings in the nvidia x server settings.


Does anybody have a work around this.  I want to see my desktop silk smooth with no jaggy edges.  I am already running a hp w2408 monitor with 1920x1200 resolution and still looks jaggy at the edges.

---

