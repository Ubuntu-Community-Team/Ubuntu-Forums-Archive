---
title: "Performance of X300 dropped without a visible reason  (Edgy)"
date: 2007-01-21
forum: Desktop Environments
---

### Post by Meister_Eder on 2007-01-21
Hello, yesterday I tried (k)ubuntu for the first time and most of my hardware works fine. 
However I experienced a very strange issue:
I installed a fresh edgy to my T43 (ATI Mobility X300 graphics card) and followed the tutorial on the Beryl website (with AIGLX). So I installed Beryl and before I actually started it I measured the FPS with glxgears (yeh, I know it is not a benchmark) and got around 1400 fps for the first 4 outputs followed by constant values of about 6000. I supposed it had something to do with the CPU scaling.
Then I started Beryl and got around 1100 fps which was quite obvious since Beryl slows down the GPU. 
Now the strange part: I installed an additional session (according to the tutorial) which allows me to choose between Beryl and a regular KDE Session in the beginning. So I chose the KDE entry the next time but glxgears only shows around 1300 fps (CPU at 800MHz) followed by 2600 (CPU at 1333 Mhz). It would not go higher. More strangely I did several measurements in a row and sometimes the CPU stays at 800MHz (although COU usage is 50%), sometimes CPU goes up to full (1833 MHz) but I only get around 1300 fps.
I do not know how to narrow my problem. Maybe someone can help me.
Some info: I am using the free driver (ati) from Xorg, I have direct rendering.

---

