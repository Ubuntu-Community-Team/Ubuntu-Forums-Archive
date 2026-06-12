---
title: "Sony VGN-AR770 Headphone jack not working. Sorry!"
date: 2009-03-05
forum: General Help
---

### Post by inspirations365 on 2009-03-05
*sigh* All I want is sound through the headphone jack...

Hello everyone. I've seen this problem a lot over the internet. I've tried to fix it myself, as other people have managed to, but it's funny how the same model of machine could have so many solutions to the same problem.

Some things that might help you:
The command:
 grep Codec /proc/asound/card0/codec#*
Yeilds:
 /proc/asound/card0/codec#0:Codec: SigmaTel CXD9872AKD
 /proc/asound/card0/codec#1:Codec: Conexant ID 2c06

I've tried many "option THIS" fixes and none of them have worked, but I'm willing to try them again with guidance this time. Those go at the very end of the /etc/modprobe.d/alsa-base file, correct? 

Thank you for all your help!

---

### Post by inspirations365 on 2009-03-05
Sorry for the double post.
The command:```
aplay -l
```
will return: ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by inspirations365 on 2009-03-05
I've looked through the list, but nothing is working! Can't anyone help me with this?

---

### Post by inspirations365 on 2009-03-05
Okay, so I'm going to post here what I've already tried adding to my alsa-base file just to rule those out.

**hippo**   Hippo (ATI) with jack detection, Sony UX-90s
**hippo_1**   Hippo (Benq) with jack detection
**sony-assamd**   Sony ASSAMD
**ultra**   Samsung Q1 Ultra Vista model
**vaio**	  Setup for VAIO FE550G/SZ110
**vaio-ar**   Setup for VAIO AR

from [http://multidisciplinary.wordpress.com/2009/01/15/sound-headphones-fix-in-linux-on-sony-vaio-vgn-ar51su-laptop/]("http://multidisciplinary.wordpress.com/2009/01/15/sound-headphones-fix-in-linux-on-sony-vaio-vgn-ar51su-laptop/"),
**options snd-hda-intel model=vaio enable=1 index=0 position_fix=1**

Also:
**options snd-hda-intel model=vaio probe_mask=1**

And from [http://ubuntuforums.org/showthread.php?t=953973]("http://ubuntuforums.org/showthread.php?t=953973"), I've tried:
**options snd-hda-intel model=vaio**

^but I didn't do "sudo apt-get install linux-backports-modules-$(uname -r)" from that site because I'm not sure what that does.

---

### Post by poojac20 on 2009-04-27
Before playing further with Alsa, can you check if the "headphone" check box under Switches in Volume Control is checked? If not, check it. 

I tried multiple solutions from the web but in the end this obvious setting worked for me.

---

