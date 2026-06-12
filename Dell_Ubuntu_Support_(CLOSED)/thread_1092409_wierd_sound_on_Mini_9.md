---
title: "wierd sound on Mini 9"
date: 2009-03-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xkristoferx on 2009-03-10
ever since i've set up sound on Skype, i can "hear" the speakers. like when you're at a concert and before the music starts, there's that sound that comes from the speakers. it's a weird, all most static like sound. i have no other way of describing it. if i turn the speakers down, i can't hear anything. it's not a bad sound but it bugs the crap of me. suggestions?

X

---

### Post by garyedwardjohnston on 2009-03-10
I am not an expert on the subject but for my television I got this and I turned off Dolby 5.1 surround to get rid of it.  I was only using the tv speakers anyway.

---

### Post by jaqrah on 2009-03-10
I have had this issue.  If I remember correctly, double click on volume icon and open alsa mixer.  I either muted or lowered one the sliders.  You will have to play around to see which one it is.  Sorry I can't be more specific but I am at work now.

Good luck.

---

### Post by ugm6hr on 2009-03-11
> **jaqrah said:**
>  I either muted or lowered one the sliders.  You will have to play around to see which one it is. 

```
alsamixer
```

Use Tab, arrow keys and "M" to adjust settings.

It is likely you will have to mute (M) the microphone, or one of the other "inputs" (perhaps Mic Boost).

---

### Post by xkristoferx on 2009-03-12
well, i have a mic plugged in so that i can use skype. i lowered the speakers to 80% and left the Master at max and the sound has gone down but not away. i've played around with the Inputs and outputs and the sound doesn't change. i have go into Alsa Mixer every time my mini9 starts up and lower the speakers. any more suggestions?

X

---

### Post by dragonmojo on 2009-03-12
In your Skype options for sound devices, do you have the HDA Intel (hw:Intel,0) set up for input and output? That seemed to work for me.

---

