---
title: "Help with Installing Compiz on Intel Chipset"
date: 2007-09-10
forum: Desktop Effects &amp; Customization
---

### Post by Milyardo on 2007-09-10
This is somewhat of a complicated Story, I'll keep it as clear an concise as I can.

I don't have an internet connection at home, so my Feisty Fawn install until yesterday was a clean install from the CD. Before Yesterday, I had Desktop Effects Enabled and it ran fine. I have a Intel Chipset, Intel Corporation 82845G/GL, Is was I think it was from memory. That may be wrong, but if not then it close to that.

Yesterday I took my Computer to a friends house who had the internet. When I booted into Ubuntu at my friends I was limited to a very small screen resolution and Compiz was disabled. I already knew this was because my friend had a monitor with a different vertical and horizontal refresh rate, and I didn't really feel like changing my xorg.conf to include his refresh rate. I decided to try running compiz anyways at this low resolution (This may be my first mistake) just to see if it would run, but it just crashed as I thought it would.

After that I proceeded to install updates and through the update manager (this may be my second mistake). Also I thought it would be a cool Idea to download the compiz-config-manager from Compiz-Fusion on my Original Compiz(My third Mistake), so I added the compiz fusion repository and downloaded the compiz-fusion-manager, and made sure not to update compiz-core or any other compiz packages.

So I go home, connect my original monitor, and try to run compiz but it crashes. It starts up, then quits and returns to metacity. So I opened up my Terminal and ran compiz in the Terminal, to see why it crashed. Reading the terminal after the crash I didn't see any output that looked like it could have been helpful. 

So I take my computer back to my friends and completely remove all compiz packages. Since I was had to reinstall all my compiz packages I decided I might well install compiz fusion. I install compiz fusion.

So I go home, start up compiz and it crashes again, this time terminal output gives me alot more error information. So I thought to my self "EFF Compiz-Fusion, I'll go back in reinstall the original compiz just so I don't have to tinker with Compiz Fusion."

So I go back to my friends one more time, remove all compiz packages and compiz fusion repositories. I then Install Compiz from the Official Ubuntu repositories. I go home start up compiz and still compiz crashes, The terminal outputting a large about of crash info I wish I could paste for you today. But I will get it later.

In the meantime, Is compiz crashing because the newest version is no longer compatible with my graphics card? Direct Rendering is On, or had the numerous install, uninstalls, etc. corrupted some obscure setting that despite when completely remove with synaptic remains? Or is it something Else?

If anyone has an opinion it'd be much appreciated.
Also I'm happy to clarify any questions you may have.

---

### Post by Cool Surfer on 2007-09-10
i have 845gvad2 and compiz is working fine :)

---

### Post by Milyardo on 2007-09-10
With what version of Compiz?

---

### Post by Cool Surfer on 2007-09-10
compiz-0.4.0

---

### Post by Cool Surfer on 2007-09-10
Try [http://compiz.org/Home/Start](http://compiz.org/Home/Start) Its very easy to install / upgrade.
I am yet to rotate windows in a cube though. The delayed animation effect is working already.:guitar:

---

### Post by Milyardo on 2007-09-11
Today I have the crash dump from the compiz core.
EDIT: Actually never mind the dump is too large for me to upload

---

### Post by Forlong on 2007-09-11
Here's a guess: you messed up your gconf by using an old version of Compiz with CCSM.

Try this:
Start your usual window manager, e.g. for GNOME:
```
metacity --replace
```Make sure you don't have Compiz set to autostart (that includes disabling desktop-effects).
Then delete the configs for compiz:
```
rm -r /home/juni/.gconf/apps/compiz
```DO NOT START COMPIZ.
Reboot.
Start Compiz.


Please use always the Flat-file Backend with Compiz Fusion.

---

### Post by Milyardo on 2007-09-11
Thanks for your Help forlong but I already fixed it.

As it turns out downloading compiz with synaptic caused a whole bunch of version mix matches among the packages. Synaptic would upadate some packages like the compiz-fusion ones but leave others unupdated(something about these versions being experimantal an unsupported).

By manualy downloading all the compiz packages and installing them I fixed my probolem.

Anyways now I'm happily running Compiz-Fusion and it runs great!

---

