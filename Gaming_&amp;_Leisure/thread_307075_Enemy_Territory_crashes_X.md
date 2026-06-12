---
title: "Enemy Territory crashes X"
date: 2006-11-26
forum: Gaming &amp; Leisure
---

### Post by slimdog360 on 2006-11-26
Ive scoured the internet looking for a solution, I can find a number of people with the same problem but no one has an answer. 

I have installed enemy territory 2.60 numerous times and everytime I try to launch it it crashes back to the login screen.Ive tried installing it both as root and as a normal user with no difference.

Here is my setup:
  AlthonXP 2800+
  1GB RAM
  Nvidia 7600GS
  running a server install of Edgy with kde-core installed.

I can run other games like torcs just fine.
Can anyone help please?

---

### Post by slimdog360 on 2006-11-27
bump

---

### Post by slimdog360 on 2006-11-28
bump yet again. I really want to play this game. I'll take any suggestion even if it seems stupid.

---

### Post by kelbizzle on 2006-11-28
I'm just going to take a stab. Because I was going to suggest [www.truecombat.com](www.truecombat.com) which is a mod for et. 

I'm only guessing but I know before Installed the same thing happened to me. and thats because the default drivers didn't use opengl.

Try:
```
glxinfo | grep "direct rendering"
```

You should see direct rendering:yes
If not...You might have to search the forums and get the nvidia drivers for your card.

---

### Post by flake on 2006-11-28
What driver are you using.

The "new" NVIDIA driver has issues with chanching resolution in Opengl.

fOR me, ET seemed to start, but by the time it should display the fog/music it crashed without warning.

This problem has been resolved in the beta driver.

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9742/NVIDIA-Linux-x86-1.0-9742-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9742/NVIDIA-Linux-x86-1.0-9742-pkg1.run)

hope this helps

---

### Post by tedrampart on 2006-11-28
the beta driver solved this issue for me, probably will for you too..
[http://www.ubuntuforums.org/showthread.php?t=296933&page=2&highlight=nvidia+9742](http://www.ubuntuforums.org/showthread.php?t=296933&page=2&highlight=nvidia+9742)

now all I need is for sound to work well..

---

### Post by kelbizzle on 2006-11-28
The sound I found to be a problem too. If you guys head to [www.truecombat.com](www.truecombat.com) The guys there could help you get it working.

---

### Post by lakersforce on 2006-11-28
I have my ET game freezing the computer up. ctrl+alt+backspace does not work

---

### Post by slimdog360 on 2006-11-29
I just grabbed the Nvidia driver from synaptic. Thanks for the ideas, I'll try them out on the weekend.

---

### Post by d351GuJu on 2006-11-29
Unbelievable!  I too now face this problem after installing v1.0-9629 today.  I was able to play ET yesterday when I had the old version.  I spent nearly half an hour figuring out what was wrong because I also installed XGL and then True Combat: Elite mod for ET.  So, I thought it was probably was either of those two, lol.  Damn it, now I will have to install beta drivers to enjoy Elite mod.  :neutral:

---

### Post by Ademan on 2006-11-30
Hrm so it's the NVIDIA driver? I too installed 9xxx.  But not the beta (which is 9742 right)?  That might be the source of my problem.  Where the heck is NVIDIA's quality control?  I've noticed that all fullscreen games seem to crash X, some worse than others.  For example i was checking out some of the games in universe, Enigma, LxDoom and penguinracer all crash X.  I see some text about cups, then it goes black.  I have about 10 seconds where i can ctrl+alt+f1 and attempt to shutdown safely, i've never been fast enough.  With enemy territory it just crashed X and then gdm restarted X.  (I had a thread on it earlier)

As far as the beta drivers, halfway through installation it says it can't discern the filename for the kernel module.  I don't mean to hijack the thread, but does anyone know what's up with that?  I installed the other one 96xx?  With the binary installer "no problem".

thanks
-Dan

---

### Post by ZERO_SHIFT on 2006-12-01
I used to have a similar problem. I fixed it by installing the nVIDIA driver, I strongly recommend Automatix 2 for downloading the driver.

Good luck.

---

### Post by hadding on 2006-12-03
can XGL and openGL programs run at the same time?

---

