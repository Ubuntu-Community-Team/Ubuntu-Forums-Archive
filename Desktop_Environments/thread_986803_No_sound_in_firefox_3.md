---
title: "No sound in firefox 3"
date: 2008-11-18
forum: Desktop Environments
---

### Post by j_dog on 2008-11-18
Suddenly there is no sound in firefox. the sound works in rythmbox and mplayer. Can anyone help ?

---

### Post by hictio on 2008-11-18
Had the same problem myself, suddenly music and video sound was great, but audio from Flash and system sounds were not audible at all.
On my case, I had to raise the volume of 'PCM', right click on the speaker icon on your Gnome Panel, and select "Open Volume Control", and check the level of the PCM playback.

Hope this helps.

---

### Post by j_dog on 2008-11-19
Thank you for your help. The pcm is up.

I have installed Opera, still no sound in it.  Maybe I should reinstall flash.

---

### Post by APNelson.L on 2008-11-19
Are you using the ALSA drivers? Switching to them seemed to clear up a lot of my sound problems. You can switch to them by going to system preferences then sound.

---

### Post by hictio on 2008-11-19
> **APNelson.L said:**
> Are you using the ALSA drivers? Switching to them seemed to clear up a lot of my sound problems. You can switch to them by going to system preferences then sound.

That's another option, I had to "move myself" to the OSS ones...

[[IMG]http://img58.imageshack.us/img58/8707/audiodemierdaqk2.th.png[/IMG]](http://img58.imageshack.us/my.php?image=audiodemierdaqk2.png)

---

### Post by j_dog on 2008-11-20
> **hictio said:**
> That's another option, I had to "move myself" to the OSS ones...

[[IMG]http://img58.imageshack.us/img58/8707/audiodemierdaqk2.th.png[/IMG]](http://img58.imageshack.us/my.php?image=audiodemierdaqk2.png)

The Alsa would only allow one speaker to work. So I switched to the OSS.
Rythmbox sounds great. No sound in firefox or Opera.

---

