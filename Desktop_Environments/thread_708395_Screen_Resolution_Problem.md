---
title: "Screen Resolution Problem"
date: 2008-02-26
forum: Desktop Environments
---

### Post by edq on 2008-02-26
I just installed Ubuntu 7.10. My monitor needs  to use a resolution of 1024x768 which is not the default setting. I have been trying to change this setting using "screen resolution" in preferences or "screen and graphics" in administration, so far without success.In both cases after I try to apply the new setting a new window appears asking if I want to keep the current setting. Regardless of which answer I give the new resolution does not apply. Does anyone have a suggestion of how to resolve this problem?

thanks,

Edward

---

### Post by geekcliff on 2008-02-27
If you are using restricted drivers and they are nvidia try typing sudo nvidia-setting in the terminal, this will give you the proper UI to set up your screen, if your using ATI just ignor me and i'll go away.:)

---

### Post by edq on 2008-02-27
I do in fact have an Nvidia GeForce FX 5200 graphics card. I tried using the command you suggested but was told by the computer that the "command  (is) not found".  Was there a mistake in the command?

To complicate matters, today when I booted Ubuntu I found the resolution had changed to 640x480 and the only other resolutions I was offered in the "Screen and Graphics" panel were 400x300 and 320x240. This puzzles me because I think I did reboot the computer when I was trying to correct this problem yesterday.

Thanks for your help.

---

### Post by geekcliff on 2008-02-28
Sorry, i did make a mistake, it should be: sudo nvidia-settings, i keep catching my self out with that one.

---

