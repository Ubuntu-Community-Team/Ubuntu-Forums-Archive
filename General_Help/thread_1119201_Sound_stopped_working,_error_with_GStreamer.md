---
title: "Sound stopped working, error with GStreamer"
date: 2009-04-07
forum: General Help
---

### Post by Danger Fox on 2009-04-07
I installed today's update and after I restarted there was an icon over the master sound icon indicating that it wasn't working. Whenever I double click it I get the error message:
"No volume control GStreamer plugins and/or devices found."
This is confusing because the sound was working up until I installed those updates and restarted. Also Ubuntu is detecting my sound card. Everything I've looked up to try to fix this has not worked. Any help is very much appreciated.

---

### Post by neu2buntu on 2009-04-07
(1)check settings in volume-control (right click speaker icon) especially device drop down window
(2) > system > preferences > sound
(3) type in terminal ```
gstreamer-properties
``` 

im no expert here but most sound settings can be fixed in the above....hope this is of some help

---

### Post by neu2buntu on 2009-04-07
also if none of the above works try logging in as guest user or if not on>= 8.10 then add another user to see if the error still exists ,if it doesnt then you will know that it is some configuration error that can prob be easily fixed

---

### Post by namur on 2009-04-07
> **Danger Fox said:**
> I installed today's update and after I restarted there was an icon over the master sound icon indicating that it wasn't working. Whenever I double click it I get the error message:
"No volume control GStreamer plugins and/or devices found."
This is confusing because the sound was working up until I installed those updates and restarted. Also Ubuntu is detecting my sound card. Everything I've looked up to try to fix this has not worked. Any help is very much appreciated.

I have exactly the same problem.
I guess there is a bug in today&#347; update

Regards

---

### Post by Danger Fox on 2009-04-07
Yeah, everything I've tried hasn't worked. Is there anyway to undo this last update? Especially since it seems like a lot of people are having this issue.

---

### Post by AJExtreme on 2009-04-07
Mine is doing the same thing, but when I log onto my wifes account the sound works fine.

Any ideas on what is going on, or how to fix it?

---

### Post by neu2buntu on 2009-04-08
i havnt installed my updates yet and i think the offending packages are phonon and phonon-backend-gstreamer. 
what i would try is goto >system > administration >synaptic package manager >file >history...and click on the date of update and look for the above named packages, if they were installed.... search them by typing "phonon" in synaptic search icon.... click on phonon-backend-gstreamer to highlight it , then click > package > force version .... and choose the last version from drop-down list and install ,restart...... may also have to do it for "phonon" and "libphonon4" if they are not automatically downgraded with "phonon-backend-gstreamer"

---

### Post by Danger Fox on 2009-04-08
> **neu2buntu said:**
> i havnt installed my updates yet and i think the offending packages are phonon and phonon-backend-gstreamer. 
what i would try is goto >system > administration >synaptic package manager >file >history...and click on the date of update and look for the above named packages, if they were installed.... search them by typing "phonon" in synaptic search icon.... click on phonon-backend-gstreamer to highlight it , then click > package > force version .... and choose the last version from drop-down list and install ,restart...... may also have to do it for "phonon" and "libphonon4" if they are not automatically downgraded with "phonon-backend-gstreamer"

I tried to do this, but those packages were not installed in the update. I then actually downloaded those packages but I still get the error that there are no gstreamer plugins installed even after I resarted.

---

### Post by Danger Fox on 2009-04-08
I hate to bump this again, but I am seriously about to pull my hair out. Everything I try to look up doesn't work!

---

### Post by rage9 on 2009-04-09
Same freaking thing happened to me.  I just had to reinstall my ALSA drivers and all that jazz.

Thread:[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Download and unpack the AlsaUpgrade-1.0.x-rev-1.16.tar file, run the script, reboot, should be good to go.

Hope that helps.

---

### Post by Reini68 on 2009-04-13
Same happened here. But it's related to the kernel update of last night. As already mentioned by rage9 running the ALSA update script again should repair the problem. Issues with Kernel-upgrades is even mentioned by Soundcheck in his thread.

---

