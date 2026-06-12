---
title: "I bought a used mini 10... would like Ubuntu advice"
date: 2010-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by david.is.goliath on 2010-06-07
So I just got a ubuntu 10 used off of craigslist. It has the disks for XP but I think I would rather just install Linux. I was wondering what I should know about installing ubuntu netbook remix on the mini 10. For example:
Will I be able to get flash working easily just using the medibuntu repositories?
Will the webcam drivers and wireless drivers work out of the box or is there something I should know about getting them to work? Same thing with the microphone.
Any tips on making the fonts bigger so they are easier to see (or does netbook remix take care of that?).
Any tips on getting the most out of the tiny screen (internet browsing for example).
I would also like tips on getting Java run. I am an English teacher and having Java working is more helpful than you could believe.

---

### Post by myddewji13 on 2010-06-07
This will help:
[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by mikewhatever on 2010-06-08
There are two versions of that particular machine, Dell mini 10 - Z500 CPU+gma500(Poulsbo), and Dell mini 10v - N270 CPU+gma950. The two look exactly the same from the outside, but differ very substantially hardware wise. The resource that myddewji13 kindly posted above deals with the second model, whereas the first one is a little harder to setup. Any way you could verify what you have?

...and just to answer your question,
- flash works well, but has nothing to do with Medibuntu
- Webcam works out of the box, but wireless requires activation
- I had a sound/mic problem on the mini 10, required editing a config file.
- fonts are easily made bigger or smaller in Ubuntu
- it's worthwhile customizing Firefox's interface
- Java is in the repositories

---

### Post by White Rasta on 2010-06-08
I too have got a deal on a mini 10
but it is the 1010
after reading and research I learn that there is a problem with the GMA500 graphics
I'm sticking with xp for now.

a little reading:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Additional%20Reading](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Additional%20Reading)

[http://swiss.ubuntuforums.org/showthread.php?t=1253406](http://swiss.ubuntuforums.org/showthread.php?t=1253406)

[http://www.plasmaburn.net/2009/07/27/how-to-fix-your-dell-mini-101010-to-have-the-correct-display-with-ubuntu-9-04/](http://www.plasmaburn.net/2009/07/27/how-to-fix-your-dell-mini-101010-to-have-the-correct-display-with-ubuntu-9-04/)

---

### Post by mikewhatever on 2010-06-08
> **White Rasta said:**
> I too have got a deal on a mini 10
but it is the 1010
after reading and research I learn that there is a problem with the GMA500 graphics
I'm sticking with xp for now.


Yes, there is a problem. That said, Karmic has biin working very well on my mini 10, after installing the poulsbo driver, and Lucid has 2d support with 3d on the way. There are also Jolicloud and Mandriva2010 that have out of the box gma500 support. As you can see, there is no need sticking to XP, unless you want to.

---

### Post by david.is.goliath on 2010-06-08
It has an hdmi port which I think marks it as a GMA 500 Ubuntu.
I still need to buy a new usb key (the other one died when I tried to use it for this and can not be reformatted).
I will consider Jolicloud but I am pretty used to ubuntu and would prefer to go with 10.04.

---

### Post by mikewhatever on 2010-06-09
Among various Ubuntu version, Karmic currently has the best support for gma500. Unfortunately, it's not out of the box, so you'll have to manually install the driver.
Lucid has been reported to work, but currently has only partial gma500 support. Keep an eye on the following two links for updates:
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

---

### Post by david.is.goliath on 2010-06-09
Thank you for the advice. I really appreciate it.

---

