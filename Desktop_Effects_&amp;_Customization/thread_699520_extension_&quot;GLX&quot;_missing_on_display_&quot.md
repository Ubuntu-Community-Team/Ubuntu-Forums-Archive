---
title: "extension &quot;GLX&quot; missing on display &quot;:0.0&quot;"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by Rat2000 on 2008-02-17
I've tried to install the new NVIDIA drivers from the NVIDIA website, all seemed well until X failed to start. I've reinstalled the nvidia-glx-new package for my GeForce 8800, that let me start X, there I switched to binary proprietary drivers and my system ran OK. Except Compiz won't work anymore!

Running "SKIP_CHECKS=yes compiz" returns "extension "GLX" missing on display ":0.0"".
I have GLX module in my xorg.conf (I copied/pasted my xorg.conf from before installing the drivers).

Please help me :-).

---

### Post by pdub on 2008-02-17
I use the binary drivers from nvidia and I followed these instructions. It works great with Compiz.

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Look for this section.

**Debian GNU/Linux or [K]Ubuntu with Xorg 7.x**

---

### Post by Rat2000 on 2008-02-18
Thanks, that helped a lot!
Only that when I tried to activate compiz using the Visual Effect window it reinstalled the nvidia-glx-new package and that screwed my system again. I suspect there is something in the restricted driver removal I did wrong. I will try redoing some of the steps and see if I can get this thing stable.

Edit: Well I got a bit tired and tried ENVY to install the driver once again. I must say it's the best way to go but I was almost their thanks to Pdub. Instead of going in the Appearance window and screw it again, I ran "SKIP_CHECKS=yes compiz" and badabing! Screen flashed for 2 seconds, desktop redrawed, AWN came to life, transparent borders where there again :-). I'm happy now. Thanks Pdub for your great help.

---

### Post by Rat2000 on 2008-02-18
Ah, one last obstacle: when I reboot, the compiz doesn't start automatically.
I've tried modifying my .config/compiz/compizconfig/ file with "SKIP_CHECKS=yes", I've tried creating a compizmanager file in that same folder and adding the same line and I still can't get compiz to autostart :(.

---

### Post by pdub on 2008-02-19
Here is link to help you with the automatic startup problem.

[http://forum.compiz-fusion.org/showthread.php?t=5154](http://forum.compiz-fusion.org/showthread.php?t=5154)

Read the entire thread before you attempt anything.

---

### Post by Rat2000 on 2008-02-20
Thanks, that worked fine :-).

Edit: It's curious but out of luck I ran the "GL Desktop" application (I don't remember installing it or seeing it before, I guess it must have come from compiz). From that point on I no longer need to run fusion-icon at start-up to start Compiz. It just starts with Compiz running.

---

