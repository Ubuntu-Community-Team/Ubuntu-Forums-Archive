---
title: "No HDMI Sound On Dell XPS M1330"
date: 2008-02-06
forum: Dell  Ubuntu Support
---

### Post by B0SS on 2008-02-06
Hello Everyone!

So, after installing an Ubuntu home file server on an old P3 I decided to make the big switch!

I have a Dell XPS M1330 Laptop with Ubuntu 7.10 (The DVD's I Got In The Mail), Yesterday I wanted to try and connect it with my 32" Sharp Aquos via HDMI and basically I got these following problems.

No Sound From TV (just laptop)
And when I switch a movie to fullscreen it basically goes into "Slow Motion Mode" (This Only Happenes When I Open Fullscreen [Both VLC/Movie Player])

What do you suggest I do?

Thanks Alot!
Ben.

---

### Post by john_hull-DELL on 2008-02-06
There's no solution yet for the audio not working through HDMI. We're actively working on it...hopefully it will be resolved in Hardy Heron

---

### Post by B0SS on 2008-02-06
Ok I guess I have to wait till April then..Also about the other problem I just noticed that when I switch a video into full screen it gets all jerky even when not connected via HDMI.. I have the integrated X3100 What do you suggest I do?

---

### Post by Trollslayer on 2008-04-11
> **B0SS said:**
> Ok I guess I have to wait till April then..Also about the other problem I just noticed that when I switch a video into full screen it gets all jerky even when not connected via HDMI.. I have the integrated X3100 What do you suggest I do?

What are you playing back with? I find VLC is fine as long as I use the specific driver. The generic VESA driver is far too slow because it doesn't use the hardware acceleration of the card.

---

### Post by B0SS on 2008-04-13
VLC + No Compiz works best on M1330 running gusty.. But now I am using hardy with compiz and vlc.. everything is great.

---

### Post by steenbras on 2008-04-30
@john_hull-DELL: what is the latest with the HDMI audio support? I upgraded to Hardy on my XPS M1530 and have HDMI video out but audio still comes out of the laptop speakers.

---

### Post by maky555 on 2008-06-05
My sound go to TV via HDMI.
Ubuntu 8.04
Just install NVIDIA driver 173.14.05

:guitar:

---

### Post by danijel on 2008-06-05
Hmm you didn't do anything else then upgrade the nvidia drivers to 173.14.05? Couldn't get it to work here.

---

### Post by jdelaros1 on 2008-06-05
I think there's an IEC958 setting that you need to unmute. Run can use alsamixer to do so.

---

### Post by mazy on 2008-06-07
I've did it!
XPS 1330
Hardy 8.04
1. updated BIOS from A09 to A10 revision
2. apt-get remove nvidia-glx-new (169)
3. download from nvidia fresh drivers - 173 and install
4. setted up twinview (AV receiver mute sound without video)
5. Sound -> changed from auto to STAC92xx Digital
6. pressed 'Test' and IT WORKS !!!

---

### Post by doktorn on 2008-07-09
I just wanted to tell.. I did ALMOST exactly this, but for people that didn't understand everything...

With Hardy:
Open System/Administration/Synaptic

Open Settings and make sure you add every repository listed.
Now reload. Find nvidia-glx-new, and mark uninstall. Then find nvidia-glx-new-envy and install that one instead. You'll also need libasound2-plugins to be able to get sound.

Now restart computer and if you had HDMI-cable inserted while rebooting, it should now show your desktop on the tv.

Go to System/Settings, and at the bottom of list you'll find settings for multimedia. Open this one and select ALSA as your sound output. Change to the Digital output as told from previous poster. Double-click on the sound-icon at the clock and find a button named IEC958. Make sure it's checked.

Now you'll be able to get sound through HDMI output.

(My system is in Swedish and I didn't change to English before writing, so some of the menu-posts might be called by the wrong names.) =)

---

