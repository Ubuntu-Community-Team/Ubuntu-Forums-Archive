---
title: "Onboard sound disabled but still being initialized"
date: 2005-04-24
forum: Desktop Environments
---

### Post by kwdy on 2005-04-24
Hello, I am a new user of Ubuntu and so far this is the first time I have run into this issue. My MB has onboard sound but I don't want to use it, I have a SB Live 5.1 I would rather use instead. For some reason Ubuntu recognizes my onboard sound even though I have it disabled in the BIOS and I can't figure out how to switch to my SB Live.

Any help would be great.

---

### Post by ludi on 2005-04-24
[QUOTE=kwdy]Hello, I am a new user of Ubuntu and so far this is the first time I have run into this issue. My MB has onboard sound but I don't want to use it, I have a SB Live 5.1 I would rather use instead. For some reason Ubuntu recognizes my onboard sound even though I have it disabled in the BIOS and I can't figure out how to switch to my SB Live.

Any help would be great.[/QUOTE]
Hi. 
You can use both at same time without problems.
Probably you have to disable by jumper set. Well, like I said before, you can use both without any problems.
Go to control center then Sound and Multimedia > Sound System.
Now, go in Hardware section. In the option "Overwrite device location" put the location of your sound blaster card. The standard is /dev/dsp (use /dev/dsp1 or 2 that should work).
You can take a look at  /dev dir.
OBS: I'm not english, so something may appear different.
Good luke.

TIP: There are some apps that you can switch between the cards (eg. xmms in OSS mode). Is a reliable way to test your setup. 
Regards

---

### Post by Gianni Exile on 2005-04-24
I had the same problem.

The most complete solution is to figure out which card you want to use and modify system files to set them to use that.

Here's the thread: [http://ubuntuforums.org/showthread.php?t=24937](http://ubuntuforums.org/showthread.php?t=24937)
This sets ALSA, OSS, arts, and ESD to default to whatever card you want.

If all your apps run through ALSA, just do that part (modify /etc/asound.conf).
The binary Flash plugin and other programs may not work out of the box though.

If there's a better way that works with all apps, even on slower hardware, I'm all ears.

---

### Post by ludi on 2005-04-24
[QUOTE=Gianni Exile]I had the same problem.

The most complete solution is to figure out which card you want to use and modify system files to set them to use that.

Here's the thread: [http://ubuntuforums.org/showthread.php?t=24937](http://ubuntuforums.org/showthread.php?t=24937)
This sets ALSA, OSS, arts, and ESD to default to whatever card you want.

If all your apps run through ALSA, just do that part (modify /etc/asound.conf).
The binary Flash plugin and other programs may not work out of the box though.

If there's a better way that works with all apps, even on slower hardware, I'm all ears.[/QUOTE]

HI.
Here I use ALSA (kde) and I have no problems with flash plugin (OBS: Now I replaced the Firefox by Konqueror).
Now I figure out that I'm able to use the amarok (or another sound app) and the flash plugin at same time (at firefox), but I have to choose the xine engine, the artsd broken.. 
I used the OSS system in control center and now I can play a music and watch an animation on flash whenever I want.
But I'm using konqueror, and I found an option at plugin section called "Use the artsdsp to direct the sound ... aRts" and everything works fine without problems (using the alsa and arts).
You can also use the esd system but I haven't tested yet.

---

### Post by Gianni Exile on 2005-04-25
Yeah those programs (artsdsp etc) work great if you have a fast computer, I hear.  On my machine though the sound breaks up when I'm doing long computations (I write medical imaging apps), so they're useless to me.  Redirecting at the hardware level uses no extra resources = better sound.

I've got a 1GHz machine, so maybe I'll try it out when I setup my new machine next week.

---

