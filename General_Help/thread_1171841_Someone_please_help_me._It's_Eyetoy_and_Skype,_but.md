---
title: "Someone please help me. It's Eyetoy and Skype, but different from other problems"
date: 2009-05-27
forum: General Help
---

### Post by Zer0 Suii on 2009-05-27
Okay, people talk about getting a stretched, green-barred image in skype, some talk about getting a "black test cam" image. I don't get any of those. I get either one of two problems. 

1: I have something that looks like white noise... but green... looks like what you see when you're trying to watch HBO when you're not subscribing to their service, but adding white noise to it... just green.

Problem #2: Skype just closes on me when I click test cam on the set up. Sometimes I get to see the green view then it crashes, or it just completely closes on me.

Like everyone else, my eyetoy works GREAT with Cheese. But here's what's different from other people's problems... They say they can't get audio when using skype. I do the test call, and I hear my voice just fine after setting the input to eyetoy and the outputs to pulse. After that, there are no audio problems at all.

Doing research I came across this:
```
Skype 2.0.0.72: You should setup [ov51x-jpeg]("http://www.rastageeks.org/") (version here: 1.5.8) and "sudo modprobe ov51x-jpeg forceblock=1" or edit /etc/modprobe.d/options and add there "options ov51x-jpeg forceblock=1". Loading ov51x-jpeg without forceblock-option results in a black video stream for skype, while it works fine using "cheese".
```... but that entire and "sudo modprobe ov51x-jpeg forceblock=1" doesn't tell me anything. It sounds to me like "You download this driver, then you speak this phrase, and viola! Everything works!" No. It doesn't. There is no way for me to install the drivers because all the tutorials tell me to do the Terminal trick. It tells me it can't find files or something.

Anyway, if someone could get me instructions other than "Download this program. Then sudo modprobe ov51x-jpeg forceblock=1" that'd be great. Because sudo modprobe ov51x-jpeg forceblock=1 doesn't tell me anything other that "Cannot find files."

Thanks!

---

### Post by Zer0 Suii on 2009-05-30
Okay, I guess I've waited long enough to bump this... so bump. Can someone PLEASE reply...

---

### Post by andersja on 2009-06-18
Some relevant info for you here, perhaps: 

[http://ubuntuforums.org/showthread.php?t=1004539]("http://ubuntuforums.org/showthread.php?t=1004539")

---

