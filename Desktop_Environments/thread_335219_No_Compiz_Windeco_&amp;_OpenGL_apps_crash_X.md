---
title: "No Compiz Windeco &amp; OpenGL apps crash X"
date: 2007-01-10
forum: Desktop Environments
---

### Post by Schalken on 2007-01-10
I installed Compiz on top of AIGLX yesterday and the whole lot was working swell until now. 

While tweaking with compiz-settings something turned off the window decorations, even though the plugin 'decroation' was enabled and had the right settings. After playing a bit the whole thing crashed the X server and sent me to the login. Now no matter what I do (even resetting compiz's gconf options) it still has no windeco and I cant even move/resize/minimise/raise windows.

Restarting with metacity I found that Blender crashes X as well. I tried GLXgears - crash. Screensavers - crash. Every OpenGL app crashes X! :(

I am trying to figure out what the problem could be. Can someone point me to some logs or something to diagnose this?

---

### Post by Schalken on 2007-01-10
BUMP

OpenGL apps still crash X. Surely there are some logs that will tell me whats going on?

**Edit:** Mouse problem solved - faulty hardware.

---

### Post by nkkromhof on 2007-01-11
There was an update to xserver-xorg, which might require you to reinstall your videocard drivers, might be worth a shot since you don't seem to have tried that yet. The lack of window decoration and OpenGL crashing your X seems to suggest that you need to reinstall your videocard drivers and do:
> 
sudo nvidia-xconfig --add-argb-glx-visuals

Or the equivalent for your particular videocard.

If you're using an nVidia card, try using these instructions (Step 2): [PriceChild's thread]("http://www.ubuntuforums.org/showthread.php?t=263851").

If you're not using an nVidia card then it's still worth reinstalling drivers and following the steps you initially did to get Compiz working.

Just my two cents,

---

### Post by Schalken on 2007-01-11
That fixed it! Thank you so much! :D :D :D

---

### Post by hartz on 2007-01-29
Aaargggg, I have exactly the same problem

which of nkkromhof's suggestions actually solved it?

Did you re-install Xorg, or the graphics card drivers?

Thanks in advance!

---

