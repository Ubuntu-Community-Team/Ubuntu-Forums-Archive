---
title: "Unity launch bar icons invisible"
date: 2012-07-23
forum: Desktop Environments
---

### Post by Netich on 2012-07-23
Hi, ive had this problem for several weeks. The icons in the bar doesnt show, but i can click on them, even the tooltip shows ok.

Ive tried unity --reset, and removing .compiz & ./config/.compiz folders, but it doesnt work.

Unity 2D works ok. 

Any help?

---

### Post by Frogs Hair on 2012-07-23
Here are some possible solutions and a bug report. 

[http://askubuntu.com/questions/91865/invisible-icons-in-the-launcher-bar](http://askubuntu.com/questions/91865/invisible-icons-in-the-launcher-bar)

[http://askubuntu.com/questions/162854/launcher-icons-invisible-still-work-in-12-04](http://askubuntu.com/questions/162854/launcher-icons-invisible-still-work-in-12-04)

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/772986](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/772986)

---

### Post by markbl on 2012-07-23
> **Netich said:**
> Hi, ive had this problem for several weeks. The icons in the bar doesnt show, but i can click on them, even the tooltip shows ok.

Netich, are you using xorg-edgers ppa by any chance?

If you are then note the comment currently on the main xorg-edgers page at [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa). I.e. currrently mesa in that ppa is exhibiting the problem you describe.

I am using that ppa and see this problem in unity 3D.

---

### Post by Netich on 2012-07-24
Thanks to both. Yes, i am using that ppa, ill try to purge and see if it works. I thought it was that unity couldnt find the icons...

---

