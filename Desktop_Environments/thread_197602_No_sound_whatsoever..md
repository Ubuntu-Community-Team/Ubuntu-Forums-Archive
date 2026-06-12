---
title: "No sound whatsoever."
date: 2006-06-16
forum: Desktop Environments
---

### Post by screw_ball on 2006-06-16
I am positive this has been posted before, but a search didn't really bring up any results.  I am on a Dell Dimension 9100 and just finished installing Dapper.

I installed all the current versions of gstreamer, but still no sound.  Not for amaroK or XMMS or any other music program, not for video, not for Flash.  No sound.  I sppent a while on Google and still found nothing.  Anyone have any idea what's wrong?  If not, I"ll just go back to Breezy.

---

### Post by dlpfmVfH on 2006-06-16
did you set analog/digital switch in gnome-mixer...?
with my soundblaster audigy 2ZS this helps..

---

### Post by Garyu on 2006-06-16
I had some problems on Breezy, but that was fixed by setting default audio to ALSA rather than OSS. Also, I once tried to install my Jabra bluetooth headset to use with Skype, but that never worked well and the result was that all sounds was redirected to this new device and I never managed to change back, so I had to uninstall everything. 

So: 
* check how many/if your sound device is right
* check if changing default to ALSA or  OSS makes a difference
* run ALSA-mixer (if you are running ALSA) and boggle the switches here and there, that got me from 2.0 to 5.1 sound once. :cool:
* check that your cables are plugged in everwhere they should. Then check it again to make sure. (surprisingly common mistake)
* are you sure you checked your cables? check again!

---

### Post by screw_ball on 2006-06-16
I reinstalled Breezy, but not just for the sound.  I don't like the Dapper feel.  Not one bit.

---

