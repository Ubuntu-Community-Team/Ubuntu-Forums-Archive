---
title: "Workaround for low mic volume XPS m1330"
date: 2009-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x C0MMAND0 x on 2009-01-23
**The following fix worked for me.  If somebody could try it who DOES have pulseaudio installed and confirm it works, please let me know because I did this with pulseaudio uninstalled.**

Fix workaround for Dell XPS M1330 Skype low mic volume.

```
sudo apt-get remove volumecontrol.app
```

```
sudo apt-get remove sound-recorder
```

```
sudo apt-get install kmix
```

```
kmix
```

1. Click on new volume icon in top right corner
2. Click on "Mixer"
3. Hit "Ctrl-M" if you DONT see the "Settings" option up top
4. Click Settings, choose "Configure Channels"
5. Be sure to select "Digital Input Source", "Digital", "Capture".
6. Choose "Digital Mic 1" and be sure to maximize "Capture" and "Digital".

*Note, you don't have a sound recorder but you can download many other free ones.

**I did this work around with pulseaudio UNINSTALLED and removed completely.  ALSA owns and it's all I need.  Now, Skype works PERFECT and the volume recording is loud.  Be sure in Skype to UNcheck the "Allow skype to adjust levels" option.

***I hope this works for you as it did for me.

****I have an image of what my Kmix setup looks like if anyone is interested, let me know as I haven't taken the time to figure out how to add images on here because they need scaling down.

---

### Post by Ancalagon82 on 2009-01-23
If I remove that stuff, how hard will it be to get it back?  On a Mini with no optical drive?

---

### Post by x C0MMAND0 x on 2009-01-24
> **Ancalagon82 said:**
> If I remove that stuff, how hard will it be to get it back?  On a Mini with no optical drive?
It will be as easy as running replacing "remove" with "install" to get it back.

---

### Post by sam hassell on 2009-02-25
Hey,

This fixes skype for me and I still have PulseAudio installed.

Thanks!

---

### Post by PsychedelicReaction on 2009-02-25
Im gonna trying this, when it finishes with all the unmet kde dependencies :P

---

### Post by x C0MMAND0 x on 2009-02-25
> **sam hassell said:**
> Hey,

This fixes skype for me and I still have PulseAudio installed.

Thanks!

I am VERY glad to hear that someone finally let me know.  Thank you very much.

---

### Post by dt_ on 2009-04-23
sorry to bump an old thread, but i am having a low microphone volume in Skype as well (in Jaunty) and when trying to follow these instructions it says volumecontrol.app is not installed. SAme with  sound-recorder, so i can't remove them. Any ideas?:confused:

---

### Post by x C0MMAND0 x on 2009-04-25
Try skipping straight to installing kmix, and then from within kmix change the capture source to "digital mic 1" and make sure that the capture volume is all the way up.

---

### Post by midtown on 2009-04-30
> **x C0MMAND0 x said:**
> Try skipping straight to installing kmix, and then from within kmix change the capture source to "digital mic 1" and make sure that the capture volume is all the way up.

I've had this problem in Intrepid, and am running Jaunty currently. Since neither of those packages to remove are installed, I installed kmix and enabled channels, ensured that Capture and Digital were maximized (digital was originally around 70%), and that Digital Input Source was set to digital mic 1. This didn't seem to help. Any other ideas? Have you tried your fix in Jaunty? Maybe you could try from a livecd and figure out something and greatly help the rest of us :)

---

### Post by pixar on 2009-05-10
It didn't work for me . I am using m1530.

---

### Post by isaidi on 2010-02-05
I was able to increase db gain on my internal digital mic in pusle audio to more than 100% using pulse audio manager

see screenshot.

although now I can record and hear my self ok. But increasing the gain in this fashion also increased the noise.. i am getting lots of humming 60hz noise now from power...

this seems to be an issue with not having proper gain on the digital mic ?  it is rooted at the alsa level ??

anythoughts ?

---

### Post by ahjulsta on 2010-09-09
My solution is to edit  /etc/pulse/default.pa  and add the following line to the bottom: 

[FONT=Courier New]set-source-volume 1 170000[/FONT]

That way I don't have to reset it every time.

[http://myramblingsonprogramming.wordpress.com/2010/09/09/mic-volume-on-dell-xps-m1330-running-ubuntu-10-04/](http://myramblingsonprogramming.wordpress.com/2010/09/09/mic-volume-on-dell-xps-m1330-running-ubuntu-10-04/)

---

