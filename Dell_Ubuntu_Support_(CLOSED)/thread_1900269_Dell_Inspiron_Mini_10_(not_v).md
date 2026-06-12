---
title: "Dell Inspiron Mini 10 (not v)"
date: 2011-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JWColeman on 2011-12-25
Hey everyone, I'm really new to the linux environment.  Currently my max resolution is 800x600 and I know that this is not as high as it can go, it's widescreen for one.  Also I'm using lubuntu, I'm not sure if that matters, but I need help finding drivers I think for my video.

---

### Post by snowpine on 2011-12-25
First step is to identify your graphics card with:

```
lspci | grep VGA
```

I believe most Dell Mini 10 (not v) units have Intel GMA500 Poulsbo graphics. If that is the case then here's some light reading material:

[http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If your card is something different then let me know and I'll try to dig up some info. :)

---

### Post by JWColeman on 2011-12-25
okay that command worked in the terminal, I was surprised to notice I had to do VGA in caps, anyways, my video card is 

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

Let me take a look at your linkies.

---

### Post by JWColeman on 2011-12-25
Okay that third link seems to be the most useful, I'm gonna try and sit through reading the wiki's for some more background knowledge.  The first wiki made it sound kind of bleak, but more and more I'm finding that grand question "will it work" seems to be yes and yes again with Ubuntu.

---

### Post by JWColeman on 2011-12-25
I have one problem, when I enter this:

```
sudo gedit /etc/default/grub

```

It doesn't know what "gedit" is.

Can anyone tell me what gedit is and how I can get the terminal to recognize it?

---

### Post by JWColeman on 2011-12-25
Dur, I didn't know gedit was a program haha! I got it installed now.

This is definitely a learning experience.

---

### Post by mikewhatever on 2011-12-26
Gedit is the default text editor in Ubuntu. Lubuntu should have leafpad or mousepad.

---

