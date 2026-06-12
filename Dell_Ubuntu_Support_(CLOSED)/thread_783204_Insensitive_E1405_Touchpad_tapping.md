---
title: "Insensitive E1405 Touchpad tapping"
date: 2008-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by analyzer123 on 2008-05-05
Hello,
    I have used 3 versions of Ubuntu now (Hardy, Gutsy and Feisty) and I have noticed one thing common with all of them - the synaptics touchpad tapping sensitivity is terrible compared to windows! I have to literally press hard twice or thrice to get a tap recognised. In windows, every small tap is perfectly recognised.

I have fiddled around with gsynaptics, qsynaptics and tried changing the sensitivity settings but I can never make it work like windows. It feels much more snappier in windows.

Note: the normal mouse movement is good. I just have a problem with the tapping.

Anyone else facing this issue and can suggest a solution?

---

### Post by chezzo on 2008-10-25
i have exactly the same problem on my dell inspiron 640m - i dual boot and in windows xp tapping works perfectly, but in ubuntu it is unresponsive

i have gsynaptics installed and sensitivity turned right up, but still some taps are just not registered

the strange thing is that middle-click (two fingers) and right-click (three fingers) always work perfectly

---

### Post by paulchinnz on 2009-01-27
Newbie to Ubuntu using the 640m/e1405 too.  Any solutions to this?

---

### Post by MooseMagnet on 2009-01-28
I have the same problem with Intrepid on my Inspiron 1300.
However, with Feisty it worked great. But now with Intrepid it's terrible.
But... I suspect it is some process running that's causing the machine to ignore the touchpad clicks, and not the touchpad itself.

There is surely a way of testing this idea.

And... with past versions of Ubuntu, the touchpad was adjusted with System -> Preferences -> Touchpad.  But now it's done with -> Mouse.

And... I remember being able to adjust the touchpad with text values from the Terminal. That worked.

But again, with Intrepid, I do suspect it is something causing the machine to ignore the clicks. How can this be tested or fixed?

---

### Post by elyz on 2009-02-19
Hi everybody,

I had the same problem with insensitive tapping. I played around a bit with the settings and here is how it worked for me:

- Install gsynaptics
- go to System -> Preferences -> Mouse -> Touchpad and uncheck "Enable mouse clicks with touchpad"
- go to System -> Preferences -> Touchpad -> Tapping and make sure that "Tapping" is checked. Maybe you would want to uncheck an re-check, to make sure it's on.

This method definitely worked for me. Tapping is much more sensitive now.

Regards,
elyz

---

### Post by paulchinnz on 2009-02-20
Thanks Elyz, unfortunately when trying to run gsynaptic I get this:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Any idea how I do this?

---

### Post by elyz on 2009-02-20
Yes, follow this: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

---

### Post by paulchinnz on 2009-02-20
Thanks elyz. Managed to sort out SHMConfig.

Can't say it's made a great difference. I've even turned touchpad sensitivity all the way to high.

By the way, your instruction to uncheck "Enable mouse clicks with touchpad" in 'Mouse' was curious: I couldn't tap at all until I had it checked.

Are there any other settings I should be playing with?

---

### Post by ugm6hr on 2009-02-21
Perhaps "High" is still not high enough for your touchpad?

```
synclient -m 100
```

It gives you an x,y and z (pressure) measurement for every movement you make every 100ms.  See what the z measurements are if you tap repeatedly.

Mine are between 16-40 for a light tap.

Depending on whether you use Intrepid or Hardy, this should be possible to change the tap sensitivity manually (Hardy is actually easier using xorg).

---

### Post by paulchinnz on 2009-02-21
Thanks. My 'z' is typically around 60 (what does that mean?). So how do I improve the sensitivity?

---

### Post by elyz on 2009-02-22
> **paulchinnz said:**
> Thanks. My 'z' is typically around 60 (what does that mean?). So how do I improve the sensitivity?

Sorry that my advice didn't work for you.

you can try ```
synclient -l
``` to see your current settings. Of special interest would be "FingerLow" which is the threshold, over which a press is recognised as a tap. What value have you set there? Try lowering it by ```
synclient FingerLow=XX
```Also interesting are FingerHigh, MaxTapTime and MaxTapMove. To see what those and the other settings mean: ```
man synaptics
``` To exit "man" press q.

Regards,

elyz

---

### Post by paulchinnz on 2009-02-22
Thanks. I got the following from synclient -l:

    FingerLow               = 10
    FingerHigh              = 15
    FingerPress             = 256
    MaxTapTime              = 111
    MaxTapMove              = 220

It appears (to me) that my FingerLow and FingerHigh are appropriate. Thanks for man synaptics, but I'm still not very clear about what FingerPress is (I tried setting this to 30 but to no avail).

Any other ideas?

---

### Post by ugm6hr on 2009-02-23
Try increasing the MaxTapTime to something like 180-200ms.

```
synclient MaxTapTime=200
```

---

### Post by paulchinnz on 2009-02-23
I dropped MaxTapTime to 100 but not much different. Any more ideas?

---

### Post by ugm6hr on 2009-02-23
> **paulchinnz said:**
> I dropped MaxTapTime to 100 but not much different. Any more ideas?

Errrm... Did you try *increasing* it, as I suggested?

---

### Post by paulchinnz on 2009-02-23
My bad. I've increased it to your suggested values and also 300 without any noticeable difference.

It's quite odd in that scrolling (sliding finger up/down right side of touchpad) is very nice and sensitive but tapping isn't.

---

### Post by ugm6hr on 2009-02-23
All your settings appear to be reasonable.  I'm afraid I would just be guessing from here on, so you'd be just as well trying different numbers for the various settings.

Perhaps the problem is that the FingerLox / High are actually too *low*; obviously, because if the pad detects a touch for too long, it will not be seen as a tap?  Consider trying something like 35 / 40.

Good luck trying to work this out!

---

### Post by paulchinnz on 2009-02-24
Set FingerLow to 30 and FingerHigh to 50, maybe a little better.  Will keep messing around with it, thanks for all the guidance (why wasn't this a problem with Windoze ... yeah I know, I should go back to it if I can't cope with Noobuntu).

---

### Post by chezzo on 2009-05-14
> **paulchinnz said:**
> Set FingerLow to 30 and FingerHigh to 50

Wow, that worked for me! Awesome! I've had the same problem since I first installed Gutsy, I can't believe it's gone!

---

