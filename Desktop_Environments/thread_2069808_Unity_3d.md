---
title: "Unity 3d"
date: 2012-10-11
forum: Desktop Environments
---

### Post by ronbrooks on 2012-10-11
I am tring to get unity 3d to work on my old computer. I want to know if I can get the two missing programs (GL vertex, GL fragment) and the new version of GL so I can get 3D to work on this computer. Could someone let me know if this is possable and where I could get them, and how to install. I checked the package manager and could not find any of them. 

Please help.

---

### Post by addegsson on 2012-10-11
I'm not sure if it's possible in 12.04 but in 12.10 it's 3d by default. ;)

---

### Post by TheFu on 2012-10-11
Do you have a video card capable of 3D accel AND do you have the correct drivers loaded?

---

### Post by ronbrooks on 2012-10-11
I have Nvidia corp. NV11 (GeForce2 MX/MX 400)  with the Nouveau driver.  When I do a check to add drivers I get no proprietary driver.

---

### Post by TheFu on 2012-10-11
> **ronbrooks said:**
> I have Nvidia corp. NV11 (GeForce2 MX/MX 400)  with the Nouveau driver.  When I do a check to add drivers I get no proprietary driver.

If I'm reading this article [https://en.wikipedia.org/wiki/GeForce_2_Series](https://en.wikipedia.org/wiki/GeForce_2_Series) correctly, it seems like the card has the required capabilities.  There definitely were nvidia Linux drivers, but those may not have been ported to newer kernels.  

Sorry, I don't know anything more.  Finding a newer, supported, AGP video card for $20 might be the easier answer for this problem.

---

### Post by haresear on 2012-10-12
I'm not absolutely positive, but I believe an nVidia card that old is probably blacklisted by Unity from running 3D. You definitely won't be able to run Unity 3D with the nouveau driver. I have an nVidia 5000 series card, and I know it is blacklisted even after I installed the latest nVidia legacy driver.

---

### Post by mcduck on 2012-10-13
> **ronbrooks said:**
> I am tring to get unity 3d to work on my old computer. I want to know if I can get the two missing programs (GL vertex, GL fragment) and the new version of GL so I can get 3D to work on this computer. Could someone let me know if this is possable and where I could get them, and how to install. I checked the package manager and could not find any of them. 

Please help.

Those are not programs you could install, but rather features of the GPU itself. As far as I know Geforce 2 didn't have programmable vertex and fragment shaders in the same sense as the modern GPUs do.

---

### Post by grahammechanical on 2012-10-13
The printout is telling you that the video card/adapter does not support Unity 3D.

What version of Ubuntu are you using? 12.04?

Unity 2D has been removed from 12.10. Another method is being used to give the user a 3D experience on hardware that does not support 3D.

Read this blog:

[http://www.omgubuntu.co.uk/2012/08/unity-2d-removed-from-ubuntu-12-10]("http://www.omgubuntu.co.uk/2012/08/unity-2d-removed-from-ubuntu-12-10")

You might want to think about downloading the 12.10 ISO image in a few days time and testing out the 12.10 live CD/DVD. You might find that upgrading to 12.10 is the answer.

Regards.

---

### Post by ronbrooks on 2012-10-19
Thanks for the info

---

