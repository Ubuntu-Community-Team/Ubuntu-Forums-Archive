---
title: "? wierd box thing???"
date: 2010-09-04
forum: Desktop Environments
---

### Post by cody1233 on 2010-09-04
alright...im running gnome (whatever comes in karmic) and when i log on, i get this box that pops up in the upper right corner...it has small dots in it, but it's black and it doesn't say anything...

I appreciate your future help!

---

### Post by devondashla on 2010-09-04
> **cody1233 said:**
> alright...im running gnome (whatever comes in karmic) and when i log on, i get this box that pops up in the upper right corner...it has small dots in it, but it's black and it doesn't say anything...

I appreciate your future help!

may we have a picture?

---

### Post by cody1233 on 2010-09-06
right here

---

### Post by mcduck on 2010-09-06
Based on shape & location, that looks like a notification window, which is for some reason or other acting rather bad. Most likely because of it's use of transparency, which would point to graphics card/driver related problem.

What graphics card you have, and if it's a recently new AMD/nVidia card have you installed the drivers for it?

(in case you were wondering, the message in that window is most likely the Network Manager telling you that it has connected to a network)

---

### Post by cody1233 on 2010-09-11
alrite...cool...but my graphics card is really super old...how do i find out what it is to download drivers?

---

### Post by 73ckn797 on 2010-09-11
> **cody1233 said:**
> alrite...cool...but my graphics card is really super old...how do i find out what it is to download drivers?

Enter this in a terminal and post the results. It will tell you the video card information
```
 lspci | grep VGA
```

---

### Post by cody1233 on 2010-09-16
cody@cody-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
cody@cody-laptop:~$

---

### Post by 73ckn797 on 2010-09-17
Did you look in System/Administration/Hardware Drivers and install the recommended driver, if any?

---

### Post by cody1233 on 2010-09-19
no recommended drivers...

---

