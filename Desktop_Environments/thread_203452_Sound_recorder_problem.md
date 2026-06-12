---
title: "Sound recorder problem"
date: 2006-06-25
forum: Desktop Environments
---

### Post by lemmy999 on 2006-06-25
I can't get sound recorder to work at all. I keep getting  " Your audio capture settings are invalid. Please correct them in Multimedia settings" 

I have tried everything but nothing seems to cure the problem.

I don't know if this  helps but when i use skype i can hear the other person but they can't hear me. I know the hardware is Ok because Skype works really well using a Mepis live CD.

---

### Post by hbweb500 on 2006-06-25
In a terminal, try:

```
gstreamer-properties
```

See what it says for input devices and try changing it.

---

### Post by lemmy999 on 2006-06-25
No mention of input devices!

Output is

chris@chris-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for reading. [gstalsasrc.c(526): gst_alsasrc_open (): /pipeline1/alsasrc1:
Recording open error: Invalid argument]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline3/v4lsrc1]
chris@chris-desktop:~$

---

### Post by hbweb500 on 2006-06-25
Im assuming that your audio-in is handled by your soundcard, and since you have sound, then your soundcard must be detected.

Thats odd. I dont have much experience with ALSA, so hopefully some more experienced users will see this.

---

### Post by nmsa on 2006-07-01
I had the same problem but after runing gstreamer-properties I was able to choose the input device and now works fine.
I had some errors before (which I did not capture) but now running a second time gstreamer-properties I have:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'

Thanks and Regards

---

### Post by ubtpenguin on 2006-07-23
Yeah I fixed sound recorder problem

Thanks for poiting gstreamer-properties.

But funny thing is when I choose ALSA as audio input. It would not work. It only works with OSS. 

I had ATIIXP AC97 onboard sound.

anyways, This sound problems are really messy

Thanks.

---

