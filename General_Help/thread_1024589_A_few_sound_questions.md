---
title: "A few sound questions"
date: 2008-12-29
forum: General Help
---

### Post by Scarlath on 2008-12-29
Hello!

Didn't know where else to put this so it went into General Help, if there's a more appropriate section feel free to direct me there :)

Installed Ubuntu a while ago and the sound seem to be working fine except for one thing: The sound in my headset is very low and cannot be adjusted. When I drag the sound icon-thing nothing happens, the sound level stays the same. 

I have both the speakers and the headset plugged in at the same time. I have yet not tried plugging the headset's cords into where the speaker is plugged in, that might work but would mean extra work each time I want to use my headset (which I wouldn't like :p). Anyone got any ideas?

Thanks!

EDIT: Oh, and another question; when I updated my Ubuntu I got two more entries in GRUB. From what I've read those are probably other kernels or something... should I just leave it as is (right now I have like... 5 entries (2 versions, 2 recovery modes, one memtest+) about Ubuntu) or should I somehow clear the older kernel versions?

Thanks again!

---

### Post by 73ckn797 on 2008-12-29
> **Scarlath said:**
> Hello!

Didn't know where else to put this so it went into General Help, if there's a more appropriate section feel free to direct me there :)

Installed Ubuntu a while ago and the sound seem to be working fine except for one thing: The sound in my headset is very low and cannot be adjusted. When I drag the sound icon-thing nothing happens, the sound level stays the same. 

I have both the speakers and the headset plugged in at the same time. I have yet not tried plugging the headset's cords into where the speaker is plugged in, that might work but would mean extra work each time I want to use my headset (which I wouldn't like :p). Anyone got any ideas?

May try to set front speaker volume higher if you have not tried that.

---

### Post by Scarlath on 2008-12-29
> **73ckn797 said:**
> May try to set front speaker volume higher if you have not tried that.

Excuse me for my newbieness but how do I do so? I cannot find anything like that in Settings -> Sounds. o:

Thanks again!

EDIT: Nevermind, I found it. Didn't seem to make much of a difference though. :(

---

### Post by linux_tech on 2008-12-29
Applications>Accessories>Terminal-
In terminal type:
To open volume control type:
```
gnome-volume-control

```


You may also want to install Gnome-alsamixer It is a little is easier to use than alsamixer. 
To install it type:
```
sudo apt-get install gnome-alsamixer

``` 

To open gnome-alsamixer type
```
gnome-alsamixer

```

---

### Post by Scarlath on 2008-12-29
> **linux_tech said:**
> Applications>Accessories>Terminal-
In terminal type:
To open volume control type:
```
gnome-volume-control

```

Well, I have the volume control thing up already, it's just that it's not affecting my headset volume whatsoever (or very little; unnoticable) which is sorta weird. I tried doing as **73ckn797** (setting front volume higher) said but that didn't do anything either.

Any other ideas?

---

### Post by 73ckn797 on 2008-12-29
> **Scarlath said:**
> Well, I have the volume control thing up already, it's just that it's not affecting my headset volume whatsoever (or very little; unnoticable) which is sorta weird. I tried doing as **73ckn797** (setting front volume higher) said but that didn't do anything either.

Any other ideas?


Try setting all levels up. Maybe the center volume also. Have you gone into volume control then preferences and turned all speakers on?

---

### Post by Scarlath on 2009-01-03
> **73ckn797 said:**
> Try setting all levels up. Maybe the center volume also. Have you gone into volume control then preferences and turned all speakers on?

Didn't make any difference. :(

---

### Post by Scarlath on 2009-01-04
No other suggestions?

---

### Post by Scarlath on 2009-01-05
Anyone?

---

### Post by gldearman on 2009-01-05
OK, just to clarify,

You can adjust the sound level on your speakers, right?  Just not your headset?

Is this a wireless headset?

Do you have a sound card, or are you using the sound support on your motherboard?

This hardware configuration did work properly before you installed Ubuntu, right?

---

### Post by Scarlath on 2009-01-05
Let's see... 

*You can adjust the sound level on your speakers, right? Just not your headset?*

Correct. 

*Is this a wireless headset?*

No.

*Do you have a sound card, or are you using the sound support on your motherboard?*

To be honest, I have no clue. How do I find out?
DXDIAG says that the unit name is "Realtek HD Audio Output".

*This hardware configuration did work properly before you installed Ubuntu, right? *

Yes, it's working fine in Windows XP.

Thanks!

---

### Post by gldearman on 2009-01-05
OK, I'm no expert in audio.  

But I suspect the problem might be that your sound card (or the equivalent component on your motherboard) isn't properly configured in Ubuntu.  Your speakers, unless they are very simple, probably contain their own simple amplifier, so they wouldn't be as affected.  The headphones, though, would be. (The speakers probably have their own AC power cord, right?  And the headset almost certainly does not?)

I don't possess enough expertise to fix the problem, but I bet that you can find the answer here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

At the very least, the steps on that page can identify your sound card, if any.

Let us know if you find your answer there, or if you need more help.

Good luck.

---

