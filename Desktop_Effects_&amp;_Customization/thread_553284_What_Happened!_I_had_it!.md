---
title: "What Happened!? I had it!"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by guaterickie on 2007-09-17
I have been trying for days to get desktop effects and compiz fusion to work in ubuntu with my 8800GTS. Yesterday night i finally did it by installing ubuntu then changing to vesa drivers and installing the restricted drivers when asked to. then i used envy to install the latest nVidia drivers and after that i restarted and expected to get a x server error but it actually worked. i was finally able to enable compiz fusion and desktop effects! then i had to get my native resolution of 1680x1050 and i just decided to try and add the resolution to my xorg.conf file. that also worked. i was pretty happy and decided to install all the updates (113 total) to ubuntu via the bar from the top. after the updates were installed i restarted only to find that i was back at square one! the x server failed to launch and the only way of getting in was with the vesa drivers. back to measly resolution and no desktop effects. What happened? was it something in the updates?

oh i also have 2 choices in the grub boot loader now also. one is like .15 generic and one is .16 generic. why did that happen?

HELP!

---

### Post by Forlong on 2007-09-17
Congratulations, you have just installed your first kernel. :)

Since you chose to install the Nvidia driver yourself (using envy) Ubuntu doesn't know that. So you have to install it for the new kernel again.

Next time, you might want to stick with the driver in the repositories. That's what the whole package management system is about: dependencies. This way Ubuntu will make sure you get all the necessary packages you need when updating something that affects your graphics driver.

---

### Post by guaterickie on 2007-09-17
oh so i just reinstall the drivers. cool i thought all that work had gone to waste. thanks

---

### Post by joshuachad on 2007-09-17
Ya thats correct. I had the same thing happen when i first gave CF a try lol. Now i dont really like using envy. I just use the repos for glx.

---

### Post by Mavtech on 2007-09-17
Same thing happened to me on my 8800GTX.  So, I uninstalled all Compiz stuff, reinstalled the Nvidia driver with Envy, then reloaded Compiz from the below repo.  It has the newest version of Compiz (0.5.2).  It is working perfectly with 7.04 and Wubi.

```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
```

---

### Post by hyperair on 2007-09-18
Actually you don't need to remove Compiz at all. Just install the new drivers and you're good to go.

---

