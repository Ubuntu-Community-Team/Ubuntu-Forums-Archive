---
title: "Xinerama not working. Panel stretches on both screens"
date: 2008-12-09
forum: General Help
---

### Post by sdlyr8 on 2008-12-09
I have been using Xinerama for my dual monitor setup for about 6 months now, and everything has been working great! But a few weeks ago I tried to get compiz working, with no success. So I temporarily gave up on it, and put everything back to normal (or so I thought). Today I restarted for the first time and now everything is all mucked up. My panels stretch across both screens and when I maximize a window, it goes across both as well. I've replaced my xorg.conf file with my previous one and it didn't help fix anything. Anyone know what happened and how to fix it?

---

### Post by easybake on 2008-12-09
> **sdlyr8 said:**
> I have been using Xinerama for my dual monitor setup for about 6 months now, and everything has been working great! But a few weeks ago I tried to get compiz working, with no success. So I temporarily gave up on it, and put everything back to normal (or so I thought). Today I restarted for the first time and now everything is all mucked up. My panels stretch across both screens and when I maximize a window, it goes across both as well. I've replaced my xorg.conf file with my previous one and it didn't help fix anything. Anyone know what happened and how to fix it?

In your xorg.conf, do you have this line?```
     Option         "Xinerama" "0"
```

If you do, change that "0" to "1"

---

### Post by sdlyr8 on 2008-12-09
Nope. I had "true" instead of "1". I tried switching it just to say I tried it, and it didn't change anything.

I've attached my xorg file for anyone to see it...

---

### Post by easybake on 2008-12-09
> **sdlyr8 said:**
> Nope. I had "true" instead of "1". I tried switching it just to say I tried it, and it didn't change anything.

I've attached my xorg file for anyone to see it...

Err. I think I was backwards. Change that To a Zero. Xinerama is for doing exactly what you don't want to do.

---

### Post by sdlyr8 on 2008-12-09
> **easybake said:**
> Err. I think I was backwards. Change that To a Zero. Xinerama is for doing exactly what you don't want to do.

I don't think so. I just tried that, and it did something weird with my screens. Yes the panel is only on one screen, but the left monitor is now gray and the cursor is the X, and that's not how I had it before...

Just noticed this.. When I run the nvidia settings, I get a message > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
I tried the `nvidia-xconfig` but nothing happened..

---

### Post by easybake on 2008-12-09
> **sdlyr8 said:**
> I don't think so. I just tried that, and it did something weird with my screens. Yes the panel is only on one screen, but the left monitor is now gray and the cursor is the X, and that's not how I had it before...

Just noticed this.. When I run the nvidia settings, I get a message 
I tried the `nvidia-xconfig` but nothing happened..

what I would do is, if you haven't already, download envyng-gtk

sudo apt-get install envyng-gtk 

Launch and redownload the latest driver for nvidia.

Then set up your screens in sudo nvidia-settings.

(Be sure to uncheck xinerama. and Save to X Configuration file.(if you don't run nvidia-settings as root it won't let you save)

---

### Post by sdlyr8 on 2008-12-10
> **easybake said:**
> what I would do is, if you haven't already, download envyng-gtk

sudo apt-get install envyng-gtk 

Launch and redownload the latest driver for nvidia.

Then set up your screens in sudo nvidia-settings.

(Be sure to uncheck xinerama. and Save to X Configuration file.(if you don't run nvidia-settings as root it won't let you save)

Nope. Did everything you said. Rebooted after the envy setup, ran the nvidia driver installation, and when it came up, I still get the "You do not appear to be using the NVIDIA X driver."

---

