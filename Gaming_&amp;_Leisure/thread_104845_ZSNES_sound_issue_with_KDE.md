---
title: "ZSNES sound issue with KDE"
date: 2005-12-17
forum: Gaming &amp; Leisure
---

### Post by abou on 2005-12-17
So I did a clean install of Kubuntu for kicks and went ahead and did the proper audio config that is listed in the Ubuntu guide.  I turned off system sounds in the system settings menu and everything seems to be working well.  Audio and video is smooth and in sync; however, when I use ZSNES there is no sound.  At first the frame rate was poor, but I remembered to install the nVidia drivers and settings tools solving that problem.  Regardless, sound still remains a problem.  

Any ideas?

I will say though that on the occasional event when amaroK crashes and the soundserver goes with it, sound in ZSNES does work.

---

### Post by shadesfox on 2005-12-17
The problem is that zsnes wants to grab the sound device all for it self.  I can usually just hit stop on amarok and it will work fine (looks like arts is nice and lets go of the sound device when arts is not using the device).  Hope that works, may be different for you though, I had to hack zsnes together to make it work at all, doesn't build on amd64.

---

### Post by noigeaR on 2005-12-26
```
sudo killall artsd
```
this usually helps for sound problems in kde. i have to do this when i want sound in zsnes or quake 4. artsd will be automatically restarted when it's needed for some system sounds, so don't worry about killing it.

to get zsnes working on amd64 you could try to use the newer wip sources from ipher with lots of fixes and improvements over the last official release.
[http://zsnes.ipherswipsite.com/](http://zsnes.ipherswipsite.com/)

---

### Post by whitesox on 2005-12-31
I think theres an easyer way than that.  go to system settings > sound and multimedia > and change the auto-suspend time to 5 seconds.  I dont think you can run amarok and zsnes at the same time with this fix :(

---

