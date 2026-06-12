---
title: "Juk + gstreamer"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Mikebgr on 2006-07-01
I recently upgraded from 5.10 to 6.06. Had some problems not booting up with the newer kernels but fixed those. My only problem is this:

Juk wont play. Before the upgrade, I could output to gstreamer and it would play just fine, now I can only output to arts and aKode, none of which play (I press play and nothing happens). 

Is there any way to make juk output directly to gstreamer again? Or any other way to configure arts or akode? I have been searching for about 2 hours now to no avail... *sigh*.

---

### Post by aysiu on 2006-07-01
Try this: ```
sudo aptitude update && sudo aptitude install libarts1-xine libxine-extracodecs
``` And then restart JuK.

---

