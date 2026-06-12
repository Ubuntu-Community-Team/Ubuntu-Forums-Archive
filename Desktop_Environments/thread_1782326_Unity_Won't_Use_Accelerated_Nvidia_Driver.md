---
title: "Unity Won't Use Accelerated Nvidia Driver"
date: 2011-06-14
forum: Desktop Environments
---

### Post by wmichaelb on 2011-06-14
I've loaded 11.04 with Unity on a Dell GX260 test machine (2.4 GHz P4, 1 GB of RAM, 40 GB HD, GeForce 6200 video card). I've tried installing both accelerated video drivers, but Compiz won't start and the Additional Drivers program informs me that the driver is loaded but "This driver is activated but not currently in use." How do I put it into use? There seems to be no switch for that effect in the system controls, and I haven't found any informative posts. Any help is welcome, and thanks.

---

### Post by Joe of loath on 2011-06-14
Which driver have you been using? IIRC you have to use the 176xx (legacy) driver with your card.

---

### Post by wmichaelb on 2011-06-14
Joe: thanks for your response, but I've tried both nVidia drivers offered with the same (no) results. I'm also running a 6200 card on my P4 PC-BSD machine, and it composites just fine on that system. ???

---

### Post by Mia1990 on 2011-06-14
The error  "This driver is activated but not currently in use." is just a bug in jockey or additional drivers the driver is really in use.There are bug reports and people all over the forums asking the same question myself included.

---

### Post by wmichaelb on 2011-06-15
Mia: thanks for the links! I ran compiz-check, and it showed the latest Ubuntu recommended Nvidia driver as being blacklisted...????? So I clicked on ignore/yes, and ran compiz config. But the only difference that I can see is wobbly windows. Unity doesn't support the cube effects, and all the icons are 2-D. I get that Unity uses OpenGL, but other than benefiting the programmers, I have to ask what good this is doing for the average user. I've heard it said that KDE offers leading edge technology to provide a poor user experience, and Gnome uses obsolete technology to create a great user experience. On this machine, Gnome is smoother, and has a lot more functionality at this point. I think that I'll stick with 10.4 for the moment and wait for another release or two. 

Thanks again for your time and trouble! I've tried Unity now, and have a more informed opinion.

---

