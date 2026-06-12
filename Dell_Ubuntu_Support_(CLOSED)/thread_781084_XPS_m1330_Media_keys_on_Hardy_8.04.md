---
title: "XPS m1330 Media keys on Hardy 8.04"
date: 2008-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by akniss on 2008-05-04
In Gutsy, the media keys worked just as expected.  I recently did a fresh install of Hardy on my m1330 (but keeping my old /home partition).  After the Hardy install, my volume media keys do not work as they should (or as they did in Gutsy).  If I push the mute, volume up or volume down keys, I get the icon on the screen indicating that the volume should be changing accordingly.  However, nothing actually happens to the sound.  In order to do some trouble shooting, I clicked on the volume applet on the panel and opened the volume control.  Sure enough none of the sliders on the playback tab were changing in response to the media keys.  

It seems that in Hardy, these keys are now tied to the 'Digital' slider on the Recording tab.  If I raise or lower the volume with the media keys, the slider under 'Digital' in the recording tab moves accordingly.  Does anyone know how I can get these keys tied to the playback volume again?

Thanks,

---

### Post by adajet51 on 2008-05-04
> **akniss said:**
> In Gutsy, the media keys worked just as expected.  I recently did a fresh install of Hardy on my m1330 (but keeping my old /home partition).  After the Hardy install, my volume media keys do not work as they should (or as they did in Gutsy).  If I push the mute, volume up or volume down keys, I get the icon on the screen indicating that the volume should be changing accordingly.  However, nothing actually happens to the sound.  In order to do some trouble shooting, I clicked on the volume applet on the panel and opened the volume control.  Sure enough none of the sliders on the playback tab were changing in response to the media keys.  

It seems that in Hardy, these keys are now tied to the 'Digital' slider on the Recording tab.  If I raise or lower the volume with the media keys, the slider under 'Digital' in the recording tab moves accordingly.  Does anyone know how I can get these keys tied to the playback volume again?

Thanks,
ok .. ,this may work, on the top bar, right click the speaker icon, click settings (settings or something alike ... mine's spanish) and select the right "slider" u want to move... usually "Master" , do that.... if that doesn't work..., 

try to do it on the top bar System/Settings/Sound... in there at the bottom should say ... mixer default channel, select the right channel as well, and it should work...

---

### Post by akniss on 2008-05-04
> **adajet51 said:**
> ok .. ,this may work, on the top bar, right click the speaker icon, click settings (settings or something alike ... mine's spanish) and select the right "slider" u want to move... usually "Master" , do that.... if that doesn't work..., 

try to do it on the top bar System/Settings/Sound... in there at the bottom should say ... mixer default channel, select the right channel as well, and it should work...

Going into the settings from the panel applet wouldn't change anything.  By going into System>Preferences>Sound, and selecting Front and Master at the same time in the Default Mixer Tracks did the trick!  
Thanks!

---

### Post by MyR on 2008-07-16
just wanted to say **thank you** ;]

peace

---

### Post by Yeti can't ski on 2009-03-16
Thank you guys! Trick also worked for Ubuntu 8.10.

---

