---
title: "Problem with sound"
date: 2008-04-22
forum: Desktop Environments
---

### Post by jicarre on 2008-04-22
Hi everybody,



I recently update my UBUNTU to 7.10, for any reason, no sound working anymore. The little speaker on the right top screen is showed with a little cross in red. So when I action the mute key on the key board, the little panel appear on the middle screen but it is noway to change the level.

REM :  When I use the live CD Ubuntu, the sound is working.

Do you have any idea of what occured ?

Thanks already

---

### Post by SpaceMaster on 2008-08-26
It sounds like you don't have the ALSA mixer properly configured.
Alternatively, you may need to set up High Definition sound (this is what I had to do with my laptop).

Unfortunately, I only know how to do this through xconfig while compiling a custom kernel (which I'd assume is step you'd rather avoid).  You may be able to find under System -> Administration a manner of configuring your hardware.

---

### Post by silkstone on 2008-08-26
The first thing to try is System > Preferences > Sound, and change everything to ALSA. You can test the sounds there. Right-clicking on the top panel volume icon lets you 'Open Volume Control' - it's possible that you need to adjust the mixer or that sound is muted by default.

---

