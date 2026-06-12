---
title: "[intrepid] Very Slow 3D Acceleration on IBM ThinkPad T30 (TeeWorlds)"
date: 2008-12-30
forum: General Help
---

### Post by GenuineXP on 2008-12-30
Ever since upgrading (fresh install) to Ubuntu Intrepid Ibex, 3D acceleration on my IBM ThinkPad T30 has been abysmal. Graphics performance is usually not very good, but I've noticed a few things in particular.

For one thing, I used to be able to squeeze out between 400 and 500 frames per second when running glxgears. Now, I typically get 90. After some tweaking, I get 105.

The biggest annoyance occurs when trying to play games. With previous versions of Ubuntu, the game TeeWorlds performed quite well (not great, but very playable). Now the game hardly runs and eats the CPU (96% usage by the teeworlds process).

What's with this? I've followed guides and have gotten an unnoticeable improvement (see above) and can't seem to use fglrx. What can I do? Any suggestions are greatly appreciated.

The laptop has an ATI Radeon Mobility 7500. Pathetic. But I've gotten performance in the past at least 500% faster than what I'm getting now. What gives?

Thanks!

---

### Post by GenuineXP on 2008-12-30
Bump.

**Edit:** Also, screen savers run very slowly. I'm currently using the "Lockward" screen saver, and it is very slow in full screen or preview mode. This was not the case in previous versions of Ubuntu (I can't remember now, but either Gutsy or Hardy seemed to run this screen saver just fine).

---

### Post by GenuineXP on 2008-12-30
Bump.

---

### Post by GenuineXP on 2008-12-31
Hm, seems I fixed it. It may be because I enabled EXA mode, but glxgears gives me a strong 700 frames per second and TeeWorlds seems to run. The only remaining problem is terrible smearing of sky textures in the game, but I can't be sure if the issue is related to my graphics configuration or the game itself.

**Edit:** Looks like it's a common problem with the game. I'll have to try a patch. Otherwise, the background is either smeared or an ugly solid yellow color.

---

