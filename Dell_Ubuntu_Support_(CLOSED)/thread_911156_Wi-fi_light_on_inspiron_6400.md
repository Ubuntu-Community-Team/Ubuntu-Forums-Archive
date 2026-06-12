---
title: "Wi-fi light on inspiron 6400"
date: 2008-09-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gryall on 2008-09-05
This is really a non-problem, It doesn't affect the use of my laptop at all. However it is one of those things that causes a niggling annoyance. 

After upgrading to hardy (Sometime ago) the Wi-fi status light on my Dell Inspiron 6400 ceased to function. I bought the Laptop with Ubuntu Pre-installed and am a bit new to ubuntu, so i have no idea where to start fixing this.

---

### Post by maruchan on 2008-09-05
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

Look at the bottom of that page; there's a link to your issue in the "known issues" list that shows how to fix this problem.

I had the problem and after installing the fix, no more problem. :)

---

### Post by gryall on 2008-09-06
That doen't seem to have worked. My Kernal is 2.6.24-21-generic (found by uname -a). So, as suggested, I ran:

sudo apt-get install linux-backports-modules-2.6.24-21-generic

I then restarted, but the LED still doesn't seem to work.

---

### Post by maruchan on 2008-09-06
Interesting. I guess your laptop isn't specifically mentioned there.

Try the last post on this page, or look elsewhere in the thread:

[http://ubuntuforums.org/showthread.php?t=774625](http://ubuntuforums.org/showthread.php?t=774625)

And this seems related:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55780)

---

### Post by gryall on 2008-09-06
I Tried out the  suggestion in the last bit of that first thread. The modules installed fine. But unfortunatly trying to run:

```
sudo modprobe iwl 3945
```

caused my system to freeze.

Thanks for the suggestions though. Will keep plugging away at this untill i Solve it.

---

### Post by maruchan on 2008-09-06
Do you know if that's the wireless card you have? That would be worth checking out.

---

### Post by gryall on 2008-09-06
just ran lspci and it came back with:

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by maruchan on 2008-09-06
Looks like you experienced this bug, bummer:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251252](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251252)

I would recommend working through this issue (perhaps using a different kernel version) and then seeing if the wifi-light problem can be fixed after the bug is addressed. Funny that you ran into this bug though.

---

### Post by maruchan on 2008-09-06
Oh, btw - just noticed your light issue is mentioned in that bug thread! lol

Edit: There seems to be a viable solution to your problem in that thread - copying the firmware files over from a different kernel version. Hope that or something else works for you.

---

### Post by gryall on 2008-09-07
Looks like I should wait till intrepid comes along and then work from there. I'm not in a huge rush to fix it, it's mroe of a niggle. Thanks for the help.

---

### Post by qiuyu76 on 2008-09-09
it's really nice post. thank you.------------------------------------------------------------------------------------------------------------[discount software](http://www.discount-softwares.com/), [software download site](http://www.julydownload.com/)

---

