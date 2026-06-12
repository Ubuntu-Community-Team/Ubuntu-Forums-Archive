---
title: "nvidia driver problems"
date: 2010-03-09
forum: Desktop Environments
---

### Post by dd1linux on 2010-03-09
Sorry for everyone whos heard this problem a million times, but this time I cant figure it out by reading other posts.  I have installed ubuntu several times and gotten the nvidia drivers working (my main goal of course is the desktop cube and wobbly windows).  But today when I decided to install ubuntu again, i downloaded the drivers from the nvidia siteand then I got rebooted to a black screen.  So I tried Envy, which also produced the same result.  Then I tried synaptic and installing nvidia-185.xxx (or whatever the latest one is).  Please help me!  I swear im not a complete newb but for some reason my brain is just not working on this one.  

I have:
2 8600GT Graphics cards
AMD64 Athlon
Ubuntu 64bit AMD OS

If you need any more info, please let me know and I will respond FAST!

---

### Post by sikander3786 on 2010-03-09
Have you tried to uninstall the driver?

```

sudo sh NVIDIA* --uninstall

```

---

### Post by dd1linux on 2010-03-09
Yeah, when I did it that way, but that just brought me back to square one....  sorry for my ignorance, but what would that solve?

---

### Post by sikander3786 on 2010-03-09
What do you see now? Broken X-Server or the GUI is there?

Are you able to login in to your desktop?

---

### Post by dd1linux on 2010-03-09
Well for now i nano the xorg.conf to use the vesa driver and i have these crappy graphics.  but when i just let it try and start up, i hear the sound and everything, but no video.  Just a black screen

---

### Post by sikander3786 on 2010-03-09
```

sudo dpkg-reconfigure xserver-xorg

```

Follow the on screen instructions and you should be able to reconfigure to previous state.

---

### Post by dd1linux on 2010-03-09
sorry after all the changes ive made im not sure what happened but when i did that there was no on screen instructions.  I got this:

dustin@dustin-desktop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for dustin: 
dustin@dustin-desktop:~$

basically nothing happened i dont think

---

### Post by sikander3786 on 2010-03-09
Reboot.

---

### Post by dd1linux on 2010-03-09
k brb

---

### Post by dd1linux on 2010-03-09
it said its going to run in low graphics mode.  I didnt get the full error message though, u want me to?

---

### Post by sikander3786 on 2010-03-09
Try to install the nvidia drivers from

System>Administration>Hardware Drivers.

Choose the one that is labelled recommended.

---

