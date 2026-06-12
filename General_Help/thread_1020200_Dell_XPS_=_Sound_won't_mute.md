---
title: "Dell XPS = Sound won't mute"
date: 2008-12-23
forum: General Help
---

### Post by MickG on 2008-12-23
Hi,

I have done a clean install of Ubuntu 8.1 after moving over from SUSE. Impressed so far, but a couple of problems (Which I will put in seperate posts).

Using the audio controller icon on screen and the on-laptop shortcut keys for audio, I can change the volume and/or mute the sound. This all shows up nicely according to the Ubuntu audio controller. However - its not actually muting the sound! Any suggestions? I have looked through the threads and can't see anything similair, so any help would be appreciated.

Thanks in advance!

---

### Post by Coder543 on 2008-12-23
Right-click on the volume control applet and click Open Volume Control. then set master, pcm, and front to zero (all the way down). Are you still able to hear stuff out of the speakers?

---

### Post by MickG on 2008-12-23
> **Coder543 said:**
> Right-click on the volume control applet and click Open Volume Control. then set master, pcm, and front to zero (all the way down). Are you still able to hear stuff out of the speakers?

That works, in that the sound is actually muted. However, just clicking on the icon and selecting mute, or using the buttons on the laptop only change the Master volume, but it appears that is ignored and only PCM (and headphone, it appears) controls the actual sound playing volume, which is only accessable from the Volume Control itself.

So, why would Master be ignored?

Thanks!

---

