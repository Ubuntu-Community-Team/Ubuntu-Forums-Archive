---
title: "Second Life 1.23.5 Linux Viewer Crashes And Sound"
date: 2009-10-25
forum: Gaming &amp; Leisure
---

### Post by Dantae Garnet on 2009-10-25
I just got Ubuntu 9.04 yesterday (former Windows Vista user) and it's my first Linux experience so I have no idea how to fix this issue with Second Life always crashing my entire computer. Also, sound is choppy and I get a message saying my computer dose not  meet the minimum system requirments to play Second Life despite the fact I have never had this message when running Second Life on Windows Vista.  I think I have to compile the viewer... whatever that means. What do I do?

---

### Post by Glucklich on 2009-10-26
Did you got it from Get Deb or Gamers Arena, for example? Usually the games from there are working correctly after installation.

.deb it's just an easier package to install for a newcomer.

---

### Post by shnurui on 2009-10-26
Hippo is more stable, only crashes when the SS activates.

---

### Post by Tony Flury on 2009-10-26
I am running SL 1.23.5 fine on 2.6.24-25-generic kernel - downloaded from [www.secondlife.com](www.secondlife.com).

Sometimes SL does not do a good job recognising the video drivers on Linux - and I doubt the rebuilding the viewer would help.

---

### Post by oldHat on 2009-10-31
I have better luck with omvviewer.  Until today, i've had chronic crash problems with all the others.

After i saw this thread, i tried grabbing the Hippo source from [http://mjm-labs.com/viewer/build.php?platform=Linux](http://mjm-labs.com/viewer/build.php?platform=Linux) .  It took two tries to build it, and it took me a while to discover the launch script in the "packaged" directory, but it runs.  

I haven't pinned down the fix, but this approach stopped Secondlife, Hippo, and Snowglobe all from crashing on startup.  In the preferences menu:

-- reduce graphics resolution to LOW 
-- set network bandwidth to <= 500 kbps, 
-- disable voice chat, streaming audio, and streaming media

If it gets better, gradually re-enable each feature, tune the graphics options, and tune network bandwidth until you're happy with it

---

