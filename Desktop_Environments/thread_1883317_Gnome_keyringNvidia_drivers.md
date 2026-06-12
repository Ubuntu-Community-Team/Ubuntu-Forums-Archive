---
title: "Gnome keyring/Nvidia drivers"
date: 2011-11-18
forum: Desktop Environments
---

### Post by Mike Loubet on 2011-11-18
Hello there! I have turned an old box into an entertainment system using Lubuntu (11.10) through a HDMI output to my TV.

My first question is regarding services. I have disabled all non-essential services and the only ones left are the Gnome Keyring services:

Gnome Keyring: SSH Agent
Gnome Keyring: GPG Agent
Gnome Keyring: Secret Service

What would happen if I were to disable these services? Which ones do I NEED. They take up a reasonably large chunk of my CPU and RAM capacity which I would like to see freed-up.

My second question is regarding the proprietary Nvidia drivers. I installed the driver and saw a boost in performance for emulation and HD video playback, but despite running under the 1280x720 resolution I need, the borders of the screen were out of the monitor (this doesn't happen in the open source drivers). This basically made the machine pretty unusable since the small LXDE menus were out of view, as were full screen window controls, so I have now reverted to the open source drivers. Any way to fix this under proprietary drivers? I searched the forums and google many times, couldn't find anything that worked.

I will post any additional information needed :)

Thanks!

---

### Post by hhh on 2011-11-18
Gnome keyring saves your password through a session, for example you run gksu nautilus, enter your password, close nautilus and if you run gksu nautilus again without logging out first you don't need to enter your password the second time. It can be removed without issues.

The Nvidia problem makes no sense to me, did you adjust resolution with gksu nvidia-settings? Did you try different refresh rates too?

---

### Post by marinara on 2011-11-18
Sounds like you're in Linux driver hell just like me.

[http://www.ypass.net/blog/2009/07/dvi-to-hdmi-overscan-screen-edge-cutoff-on-an-hdtv/#comments](http://www.ypass.net/blog/2009/07/dvi-to-hdmi-overscan-screen-edge-cutoff-on-an-hdtv/#comments)

read the comments.  

I know that solution works, because it fixed the exact same problem for me. I skipped to the comment about changing the settings on the tv.  Turns out my HDMI monitor was in 'Video' mode.  

About the keyring daemons... I could give you my best guess, but how would that help?
Let me tell you not to worry about the CPU/ RAM they are using.

---

### Post by Mike Loubet on 2011-11-18
Thanks hhh, I disabled those services with no impact on my system. It boots faster now and there's more of my precious 1gb of RAM to go round :D

marinara, unfortunately my TV doesn't have those options (cheap flatscreen I picked up, only gives me the option of 4:3 and 16:9, no other video options) and there is no xorg.conf in Lubuntu, which is why when I tried some other solutions before, they didn't work. If I can find a way of making those changes to xorg, I will but just don't know how to.

---

### Post by marinara on 2011-11-18
yeah, i'm in the same boat.  Everything I read is config xorg this, config xorg that.
but I don't know the first damn thing about config xorg

---

### Post by Mike Loubet on 2011-11-18
Yeah, it's made even harder by the fact that Lubuntu is not a hugely popular distro. I had problems with ATI drivers on an Ubuntu machine a couple of years ago and solved them by typing a few commands in from the forums... But with Lubuntu it's much harder to find anything useful.

---

### Post by marinara on 2011-11-18
what kills me is that it was working before you installed Nvidia drivers.  So there's probably a fix that doesn't involve the LCD

---

### Post by hhh on 2011-11-19
[http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/](http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/)

Run nvidia-settings (Alt+F2 for the "Run" dialog, the "gksu nvidia-settings" without the quotes).

If you don't have nvidia-settings, install it via a terminal...```
sudo apt-get install nvidia-settings
```

-edit- Hmm, I don't know, though. I have the latest Nvidia drivers and I don't see those settings in nvidia-settings. It might be that my card is old (an integrated GeForce 6150LE).

---

### Post by Mike Loubet on 2011-11-19
I'm going to try and play with the Nvidia settings again. If it fails and I get a command line screen (happened before) how do I reset to default (open source drivers, standard config)? Just in case...

---

### Post by Mike Loubet on 2011-11-20
OK, increased the resolution to 1920x1080 in Nvidia settings from the native resolution of 1280x720 (under which the open source drivers worked), then in GPU Scaling, I changed it to Aspect Ratio Scaled.

Then on my TV, there is a setting called "point to point", which normally centres the image and makes it very small, but in this case fills the screen perfectly. Only problem is, when I use an emulator in full screen, I have to switch to 16:9, but doesn't really bother me. Also now runs on 1080p rather than 720p, which is cool.

Had to increase all the font sizes because they were unreadable and Plymouth looks like crap, but it usually does with proprietary drivers. 

The only thing left was the sound, which under ALSA didn't work after installing the drivers (I'm assuming because the sound now wanted to be played through HDMI). Installed pulseaudio and changed the profile to "Digital Stereo (HDMI) nr 2 Output" in the list of options, that was the only one that gave sound.

Hopefully that will help anyone having similar problems, other threads seem to be outdated. I will now mark the thread as solved since the issues have been resolved! Thank you :)

---

