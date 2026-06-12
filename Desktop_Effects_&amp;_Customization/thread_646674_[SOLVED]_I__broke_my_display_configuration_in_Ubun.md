---
title: "[SOLVED] I  broke my display configuration in Ubuntu 7.10  - need help fixed it"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by vortex0007 on 2007-12-21
I messed up and managed to break the configuration for my video card un Ubuntu 7.10 

 I'm now just trying to start over without having to re-install Ubuntu. Here's my current problem:

Problem 1:

Each time I turn on the computer I get prompted with a screen that reads: 

"Ubuntu is running in low graphics mode" 
Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself. "

I have the options "Configure" "Shutdown" or "Continue"

I choose Configure

Problem 1a: 

On the Graphics Tab, there are 2 graphics cards listed, both currently set to vga - Generic VGA video cards.

the machine has an Intel graphics card on the motherboard and then I've added an ATI Radeon X1950 Pro video card with 2 monitors attached to the card. 

What order are they being listed on this configuration option? 

Problem 1B: 

I have 3 ATI related drivers listed in the configuration box. No matter which one I pick, GNOME desktop loads in 640X480 mode and when I reboot I'm back into this same screen.

Problem 2: 

Once I get into GNOME desktop, the only way I'm able to move windows is to run the command "sudo metacity --replace" - which fixes the GUI oddities I'm seeing but only utnil the next reboot when this problem repeats

Help!

---

### Post by l33t_3lv3n_g33k on 2007-12-21
```
sudo dpkg-reconfigure xserver-xorg
```
 
That should run you through a "wizard" to reconfigure your display configuration.  It should get you back to an "out-of-the-box" configuration.  I think you'll have to reinstall any drivers (or at least re-run their configuration utilities)
 
Alternately, you could restore a backup copy of your xorg.conf file.  You may have one of those sitting in your /etc/X11 directory.  Something like "xorg.conf-original" or even "xorg.conf.0".  Anything from before you started having the issue shoudl fix it.
 
If you don't have a backup copy of the xorg.conf, then consider this a lesson in backups. :)

---

### Post by vortex0007 on 2007-12-21
I ran through the xserver-xorg reconfigure - went through the wizard, and then rebooted - problem 1 continues.

I was able to solve problem 2 so that no longer happens. Anything else I can do?

---

### Post by vortex0007 on 2007-12-21
Well for better or worse I keep reading forum posts and keep trying to make this work. 

I ran the following:

```
sudo apt-get autoremove xserver-xorg 
```

and that appeared to have completed removed xserver so I rebooted, and that cleared up the prompting - of course GNOME won't load but I expected that.

So I ran 

```
 sudo apt-get install xserver-xorg 
```

and again - reboot, and now GNOME desktop loads up and I can see the login screen in 640X480 mode. I login and my desktop resizes to something I can't even read. It's almost as if it's shunk my 25" display into 5 small windows and drawn a bunch of horizontal black lines through everything. :confused:

Um, any thoughts on how to reset GNOME? I'd be happy even with the crappy 640X480 I was getting before.....

---

### Post by vortex0007 on 2007-12-21
I should also mention I ran

```
sudo apt-get install ubuntu-desktop 
```

but I need help figuring out how I can reconfigure the GNOME screen resolution from the command line.

---

### Post by bigken on 2007-12-21
I would run sudo dpkg-reconfigure xserver-xorg again and select vesa as your driver then use the space bar to select your resolution sizes this will at least give you a working desktop

---

### Post by vortex0007 on 2007-12-21
Thank you very much 

Re-running:

```
 sudo dpkg-reconfigure xserver-xorg

```

a second time and then using VESA and  the configuration worked.

All of the problems in this thread are now solved.

---

### Post by birdywa on 2007-12-22
I tried this and I am confused. Is it supposed to walk me through all of the keyboard crap? It doesn't autodetect anything like it's supposed to. In fact, nothing ever works like it's supposed to. I'm so tired of this. I just want my computer to work properly now.

---

### Post by birdywa on 2007-12-22
I just did the reconfigure thing, and x is BROKEN! When I start up, after the splash, the screen just flashes. I give up. I am sending this from my functioning computer - the windows one. Thanks for the help. I have posted on this problem like 5 times and no answers.

---

### Post by bigken on 2007-12-22
> **birdywa said:**
> I just did the reconfigure thing, and x is BROKEN! When I start up, after the splash, the screen just flashes. I give up. I am sending this from my functioning computer - the windows one. Thanks for the help. I have posted on this problem like 5 times and no answers.


what type of video card do you have

---

