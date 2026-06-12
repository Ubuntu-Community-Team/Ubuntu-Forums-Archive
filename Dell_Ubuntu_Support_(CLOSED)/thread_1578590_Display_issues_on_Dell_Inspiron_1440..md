---
title: "Display issues on Dell Inspiron 1440."
date: 2010-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vinu Raj V on 2010-09-20
Hi,

                    I usually see many unususal black lines on my screen which disappears suddenly after showing up. But one day,  it stayed and it almost used less than half the screen. I refreashed and it went out. It mostly appears on the lower part of the screen. There are some other display issues like, there is no picture quality. Even an image or a video file have no quality.
 What excatly is the problem? Is it the problem with the x server or my display device?

---

### Post by Vinu Raj V on 2010-09-21
Anybody please help. The lines are increasing day by day.

---

### Post by Vinu Raj V on 2010-09-27
I think the problem was with compiz. I disabled the visual effects and I hope it will work well. Which command is used to know about the display device and drivers?

---

### Post by Vinu Raj V on 2010-09-30
This is a post on the common bugs on 10.04.


> Haven't seen this on launchpad yet but:

Laptops with Intel graphics chips, post upgrade may not be able to enable desktop effects (compiz). May also get a warning during boot of "low res mode".

The problem is during the upgrade, all sorts of Nvidia drivers were installed, and they're clashing with the Intel drivers. The workaround (I know of two times this worked perfectly)

Code:
sudo apt-get --purge remove nvidia*
You may want to apt-get -s first (simulate) and make sure nothing unwanted is being removed. Then reboot and Bob's your uncle.


Found it useful.

---

