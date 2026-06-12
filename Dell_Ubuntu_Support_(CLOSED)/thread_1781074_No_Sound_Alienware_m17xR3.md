---
title: "No Sound Alienware m17xR3"
date: 2011-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vVvSHADOWvVv on 2011-06-12
Would like some help. do not have sound on my new Alienware M17xR3, everything else works fine. 
Running Ubuntu 11.04
2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Would love to have sound on this beast

---

### Post by vVvSHADOWvVv on 2011-06-19
[SOLVED] This was odd, you  must change the sound preferences on the input tab to internal micrphone or you will not have sound. This is fixed, I finally have sound.

---

### Post by pinan on 2011-09-24
There are some other changes required as well add

options snd-hda-intel index=0 model=alienware to the bottom off /etc/modprobe.d/alsa-base.conf

set output to 'Internal Audio Analogue Stero
The connector to Analogue Output

Hardware to HDA Nvidia 1 output Digital Output
Profile to Digital Stereo (HDMI) output

And it all works :-)

---

### Post by vVvSHADOWvVv on 2011-09-25
I have noticed that I cannot get the MIC meter to light up while in sound settings. Thoughts?

---

### Post by mavv on 2012-01-01
Does anyone know how to get this working on a M17xr3 machine with a radeon gfx card.  Obviously selecting the nvidia output isn't working as there isn't one.  I've tried going through the steps suggested here with no luck.

---

### Post by vVvSHADOWvVv on 2012-01-01
> **mavv said:**
> Does anyone know how to get this working on a M17xr3 machine with a radeon gfx card.  Obviously selecting the nvidia output isn't working as there isn't one.  I've tried going through the steps suggested here with no luck.

Get what working?

---

### Post by mavv on 2012-01-01
The sound on my laptop isn't working at all right now.  It seems like its being detected, at least I have 2 devices shown in the sound prefrences, they are:

Juniper HDMI audio [Radeon HD5700 Series]
    1 Output
    Digital Stereo (HDMI) Output
Internal audio
    1 Output
    Digital Stereo  (IEC958) Output

There are several options in the profile menu, I've been through all of these testing as they go.  I've tried adding the line to the modprobe.conf file and retried all the profiles for all the cards and still no luck.  I've tried grepping the codec in the proc directory as suggested in the support on the website, got this response:
> 
mav@mav-M17xR3:~$ grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: IDT 92HD73C1X5
/proc/asound/card0/codec#3:Codec: Intel CougarPoint HDMI
/proc/asound/card1/codec#0:Codec: ATI R6xx HDMI
From what I can see, the cards are being recognised, just no sound coming out.  Anyone got any ideas what the problem might be, or is there any other debugging info i can find about?

*Edit
Just been through the syslog and got this error coming up:
[   16.001390] init: alsa-restore main process (1087) terminated with status 99
thought this may be causing the problem, anyone know how to fix this?

---

### Post by vVvSHADOWvVv on 2012-01-01
> **mavv said:**
> The sound on my laptop isn't working at all right now.  It seems like its being detected, at least I have 2 devices shown in the sound prefrences, they are:

Juniper HDMI audio [Radeon HD5700 Series]
    1 Output
    Digital Stereo (HDMI) Output
Internal audio
    1 Output
    Digital Stereo  (IEC958) Output

There are several options in the profile menu, I've been through all of these testing as they go.  I've tried adding the line to the modprobe.conf file and retried all the profiles for all the cards and still no luck.  I've tried grepping the codec in the proc directory as suggested in the support on the website, got this response:
From what I can see, the cards are being recognised, just no sound coming out.  Anyone got any ideas what the problem might be, or is there any other debugging info i can find about?
Tabs

Hardware Should be HD Audio Controller with profile of Digital Stereo (HDMI) Output
Input should be Internal Audio Analog Stereo
Output should be Internal Audio Analog Stereo with Connector Analog Output

You must have 
options snd-hda-intel index=0 model=alienware to the bottom off /etc/modprobe.d/alsa-base.conf

Restart machine 

My m17xR3 is running Ubuntu 10.10

---

### Post by vVvSHADOWvVv on 2012-04-26
Great news everyone. After upgrading to Ubuntu 12.04 LTS, all audio systems and Internal mic is working perfectly on my Alienware M17xR3.

:popcorn:

---

