---
title: "Webcam With Mic Software"
date: 2009-05-01
forum: General Help
---

### Post by AdamShumpisxXx on 2009-05-01
I tried Cheese and all it does is flicker green and what-not. My webcam supports 30FPS at 640x480 under YUY2 rendering in Windows but I cannot find the equivalent in Ubuntu Intrepid. I'm looking to make YouTube videos with my Ubuntu setup rather than my Windows setup.

I tried VLC but it was still producing these flickery lines and green spots. I believe the culprit is MJPEG because when I use that type of rendering in Windows using AVS Video Capture I get the same flickery crap as I do in Ubuntu.

My webcam also has a built in microphone so I'd like to use that instead of the one plugged into my sound card that I use as a headset in Windows.

This is my lsusb read-out:

```
Bus 001 Device 004: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0c45:62e0 Microdia 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I don't know why it says Microdia but it's made by Rosewill. It's a model RCM-3201V if that helps. Maybe I have to switch drivers? I have no idea. That's why I'm here...haha!

Any help would be greatly appreciated!!!

---

### Post by BslBryan on 2009-05-01
You have tried Camorama, right?  

Also, you can try it through Gimp, maybe?  I'm almost positive you won't get sound out of it, though.

---

### Post by AdamShumpisxXx on 2009-05-01
As per your suggestion I installed Camorama using Add/Remove Applications. When I run it I am getting this error:

[IMG]http://pic19.picturetrail.com/VOL1091/3953709/8379178/363083257.jpg[/IMG]

Thank you for your response.

---

### Post by BslBryan on 2009-05-01
Well, the first suggestion is to try another app.

EasyCam2 might work for you.
[B]
However[/B], there are no Rosewill webcam drivers available for Linux at this time, but the results of your lsusb say Microdia...

And even those are hard to configure in Linux.  You can always try to follow a tutorial, like one found [here]("http://ubuntuforums.org/showthread.php?t=375005"), but there are no promises.  

Just don't give up on searching for an answer, because it's possible to get anything working, it just may take some time.

Good luck, AdamShumpisxXx.

---

### Post by AdamShumpisxXx on 2009-05-01
I have tried EasyCam in the past and it changed nothing. I will try the tutorial you've linked me to and post my results here. I doubt it will work however as the tutorial is pretty dated (2007). Are there any updated versions of this?

Also, I understand what you mean about always searching for the answer. If I hadn't I would not have realized I had to use YUY2 (or YUYV?) instead of MJPEG. On that note I don't believe it's a driver issue. Do you know of any way to force any available program to utilize YUY2 or YUV instead of MJPEG?

Thanks again.

---

### Post by BslBryan on 2009-05-01
I'm sorry to say that I'm at a loss for that.

Though, in certain applications' properties, I have seen the option "Force YUY2" in the past but after a bit of tinkering, I haven't seen it again.

---

### Post by AdamShumpisxXx on 2009-05-01
> **BslBryan said:**
> I'm sorry to say that I'm at a loss for that.

Though, in certain applications' properties, I have seen the option "Force YUY2" in the past but after a bit of tinkering, I haven't seen it again.

That's a complete tragedy! Hahaha. So, I know it's somewhere but nobody knows exactly where it is. SOMEBODY HELP! :P

---

### Post by AdamShumpisxXx on 2009-05-01
Gotta' BUMP it. I need this. Haha. But seriously, I do. I hate using Windows for anything other than gaming. HALP!

---

### Post by AdamShumpisxXx on 2009-05-01
Bump...

---

