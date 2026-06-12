---
title: "Sync to VBlank"
date: 2011-12-05
forum: Desktop Environments
---

### Post by koine on 2011-12-05
Can I enable Sync to VBlank in Xubuntu 11.10? Enabling this options in NVidia X Server Settings doesn't take any effect.

---

### Post by 3Miro on 2011-12-05
> **koine said:**
> Can I enable Sync to VBlank in Xubuntu 11.10? Enabling this options in NVidia X Server Settings doesn't take any effect.

Nvidia Setting should be running for those options to take effect. If you set the sync and then exit the Settings applications, then those wouldn't get saved.

How do you determine that sync isn't set?

---

### Post by koine on 2011-12-05
When I move windows or watch the film, image drops to the lines

---

### Post by 3Miro on 2011-12-05
> **koine said:**
> When I move windows or watch the film, image drops to the lines

About moving the window, this has nothing to do with sync. Xfce's xfwm4 is light on GPU resources mostly because it doesn't fully utilize the GPU power (it runs mostly on CPU). Xfwm4 is like Metacity and OpenBox and under those WM the image of moving windows and such would almost always be a bit choppy. This is in contrast with say Compiz, which uses the OpenGL capabilities of the GPU to give you a smooth picture, but requires a more powerful video card.

Other then getting a faster computer or using something like Compiz, I don't think you can solve this problem.

I am not sure about the choppy move, it can be caused by bad movie or bad codec as well as the above mentioned problem.

---

### Post by kamereon on 2011-12-17
can't seem to get sync to vblank working in xubuntu 11.10

nvidia-settings running, sync to vblank set for video and openGL, but videos are tearing in parole as well as vlc.
Hardware can't be a problem: GeForce GTS 450, nvidia driver 280.13, 2,9 Ghz Qaudcore, 4GB RAM.  :-(

btw. if koine has the proprietary nvidia driver activated, nvidia-settings will be started automatically in the background. Then you *can* exit the settings GUI without losing the settings.

---

### Post by COMECON on 2012-10-31
I know it's late, but...
You have to disable the Compositor at XFCE Control Panel -> Window Manager Settings / Compositor.
:)

---

