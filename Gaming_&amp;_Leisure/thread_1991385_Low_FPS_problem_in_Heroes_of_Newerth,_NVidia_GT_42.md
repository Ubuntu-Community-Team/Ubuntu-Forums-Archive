---
title: "Low FPS problem in Heroes of Newerth, NVidia GT 420 M"
date: 2012-05-30
forum: Gaming &amp; Leisure
---

### Post by Myrwyn on 2012-05-30
Hey there.

I have just installed ubuntu , and i really liked it. But i have a problem, i searched for it and couldn't find any proper solution.

I have i7-740qm processor , GT 420 M graphic card , and 4 giga ram. 

I've been playing this game, Heroes of Newerth when i was in Windows. It was working smoothly. But in Ubuntu i have really low fps and to lower special effects or resolution does not solve the problem.

 I searched HoN's forums for an answer but they only said that there is a problem with 3D desktop applications like Unity and they wanted me to remove or close them. But i am really new to Ubuntu and I just don't know how to do that. So I removed compiz and its components. Nothing changed. I don't know how to check if I had some of that 3D desktop applications or how to check if i installed correct driver for my graphics card. And I am not sure that closing or removing that applications will solve my problem.

Thank you so much for your time and replies.

---

### Post by sffvba[e0rt on 2012-05-30
*Thread moved to **Gaming & Leisure**.*


404

---

### Post by deadflowr on 2012-05-30
Have you fully read through this page:

[http://forums.heroesofnewerth.com/wiki/index.php/Technical_Support/Linux]("http://forums.heroesofnewerth.com/wiki/index.php/Technical_Support/Linux")

---

### Post by sffvba[e0rt on 2012-05-30
I would suggest we start by installing the Nvidia binary driver.

Have a look at this [How-to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and let us know if you run into any problems installing the driver.


404

---

### Post by Myrwyn on 2012-05-30
> **deadflowr said:**
> Have you fully read through this page:

[http://forums.heroesofnewerth.com/wiki/index.php/Technical_Support/Linux](http://forums.heroesofnewerth.com/wiki/index.php/Technical_Support/Linux)

Yes i tried everything written there.

---

### Post by Myrwyn on 2012-05-30
> **not found said:**
> I would suggest we start by installing the Nvidia binary driver.

Have a look at this [How-to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and let us know if you run into any problems installing the driver.


404

Thank you i am looking for that how-to now.

---

### Post by Myrwyn on 2012-05-30
> **not found said:**
> I would suggest we start by installing the Nvidia binary driver.

Have a look at this [How-to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and let us know if you run into any problems installing the driver.


404
 
I installed closed source restricted Nvidia driver when i first set up my ubuntu. So now I am already using Nvidia binary driver.

---

### Post by thatguruguy on 2012-05-30
I suspect I know the problem.  Are you running this on a laptop with Optimus graphics?

You need to install either bumblebee or ironhide.  Right now, you are only using the graphics capabilities of the intel CPU. Both bumblebee and ironhide allow you to switch between the intel chip and your nvidia gpu.

Here's some reading on bumblebee: [clicky]("https://wiki.ubuntu.com/Bumblebee").

---

### Post by thatguruguy on 2012-05-30
> **not found said:**
> I would suggest we start by installing the Nvidia binary driver.

Have a look at this [How-to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and let us know if you run into any problems installing the driver.


404

Actually, if his system is using optimus, he needs to remove the proprietary driver before installing either bumblebee or ironhide.

---

### Post by sffvba[e0rt on 2012-05-30
> **thatguruguy said:**
> Actually, if his system is using optimus, he needs to remove the proprietary driver before installing either bumblebee or ironhide.

Thanks for the info.  I have zero experience with Optimus.


404

---

### Post by Myrwyn on 2012-05-30
> **thatguruguy said:**
> I suspect I know the problem.  Are you running this on a laptop with Optimus graphics?

You need to install either bumblebee or ironhide.  Right now, you are only using the graphics capabilities of the intel CPU. Both bumblebee and ironhide allow you to switch between the intel chip and your nvidia gpu.

Here's some reading on bumblebee: [clicky]("https://wiki.ubuntu.com/Bumblebee").

Yes, i am trying that on my laptop, and i will try and let you know if it does work or not.

Thank you in advance for your concern.

---

### Post by Myrwyn on 2012-05-31
First of all, no matter what i did i couldn't run the glxspheres with optirun command. But when i run glxspheres normally looks like my fps's are really good ;

trker@ubuntu:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x285
Context is Direct
OpenGL Renderer: Gallium 0.4 on NVC1
129.894364 frames/sec - 115.164343 Mpixels/sec
133.805814 frames/sec - 118.632235 Mpixels/sec
135.276764 frames/sec - 119.936379 Mpixels/sec
139.670413 frames/sec - 123.831788 Mpixels/sec
132.167934 frames/sec - 117.180090 Mpixels/sec
139.459735 frames/sec - 123.645001 Mpixels/sec
137.974144 frames/sec - 122.327876 Mpixels/sec
134.311836 frames/sec - 119.080874 Mpixels/sec
131.724056 frames/sec - 116.786548 Mpixels/sec
134.967025 frames/sec - 119.661764 Mpixels/sec
128.025601 frames/sec - 113.507498 Mpixels/sec
128.708417 frames/sec - 114.112883 Mpixels/sec
134.121328 frames/sec - 118.911970 Mpixels/sec
139.148571 frames/sec - 123.369123 Mpixels/sec
134.943536 frames/sec - 119.640939 Mpixels/sec
133.433193 frames/sec - 118.301869 Mpixels/sec
133.709281 frames/sec - 118.546649 Mpixels/sec

but i am still having trouble in games :(.

---

### Post by Myrwyn on 2012-05-31
trker@ubuntu:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x27
Context is Direct
OpenGL Renderer: GeForce GT 420M/PCIe/SSE2
469.113854 frames/sec - 415.916343 Mpixels/sec
466.933594 frames/sec - 413.983325 Mpixels/sec
468.275871 frames/sec - 415.173388 Mpixels/sec
468.218687 frames/sec - 415.122688 Mpixels/sec
468.250876 frames/sec - 415.151227 Mpixels/sec
469.475431 frames/sec - 416.236917 Mpixels/sec
468.865186 frames/sec - 415.695874 Mpixels/sec
468.841551 frames/sec - 415.674919 Mpixels/sec
469.367895 frames/sec - 416.141576 Mpixels/sec
463.755203 frames/sec - 411.165363 Mpixels/sec
463.995936 frames/sec - 411.378797 Mpixels/sec
468.810377 frames/sec - 415.647280 Mpixels/sec
467.457704 frames/sec - 414.448001 Mpixels/sec
468.130902 frames/sec - 415.044858 Mpixels/sec
468.712747 frames/sec - 415.560722 Mpixels/sec
468.144508 frames/sec - 415.056921 Mpixels/sec
469.306428 frames/sec - 416.087079 Mpixels/sec

These are my last glxspheres results with latest drivers, but my fps is still getting incredibly low in game. Changing video preferences in game is not making any differences. I don't know what to do.

---

### Post by thatguruguy on 2012-05-31
Unfortunately, I can't really help you further, because I don't have a laptop with Optimus. I would suggest searching the threads about Bumblebee in the forums. There are a handful of them.

---

