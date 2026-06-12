---
title: "No sound in Armagetron"
date: 2006-04-01
forum: Gaming &amp; Leisure
---

### Post by bpont on 2006-04-01
I successfully installed from Universe repository and It plays perfectly, just no sound...I have the sound files in the correct location and can play them by browsing to them and playing on a different application: xmms, totem, etc.  Armagetron just won't play with sound effects for some reason and hearing the noises is half the fun!!  Anyone got any ideas to share?  I searched the forums, but couldn't find anything.  ](*,)

---

### Post by bpont on 2006-04-01
Solved: the problem lies with the standard libsdl Ubuntu installs, which is libsdl1.2debian-oss.  If I install libsdl1.2debian-esd which corresponds to my gstreamer-properities, aka "Multimedia Systems Selector" the audio default sink has as its Output: ESD - Enlightenment Sound Daemon  and the Pipeline is "esdsink".

Then I uninstalled libsdl1.2debian-esd and reinstalled Ubuntu's default libsdl1.2debian-oss and recreated the same problem of no sound while playing Armagetron.

Finally, I uninstalled libsdl1.2debian-oss and installed libsdl1.2debian-all, which includes all drivers (including esd) and all is well.

I should mention that you can only install libsdl1.2debian-esd or libsdl1.2debian-all through the 'Universe' repository and it's not officially supported by Ubuntu.

---

### Post by Derspankster on 2009-11-11
My issue is somewhat similar but I do have sound when I initially start Amagetron. After some time, sound begins to stutter, as does the game itself and finally, sound fails and the game stalls to the point of being unplayable.

I am unsure that the fix described above would help me as it might not be the same issue.  All other sound events seem to be OK.

---

### Post by decomp on 2009-12-04
Derspankster, I would say it's worth trying the fix listed above - I had a similar issue with the game hedgewars, and switching the sounds libsdl sound driver fixed it. If not you can always switch it back.

Also, the above listed fix works for me in ubuntu karmic, but I had to use libsdl1.2debian-esd, not libsdl1.2debian-all. Thanks bpont

---

