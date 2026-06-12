---
title: "Ubuntu Beryl problems AIGLX or XGL w/ Dell Inspiron 640m (rain effect)"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by newbie2expert on 2007-08-13
Hi
I am new to linux and i am trying out the ubuntu distro. 
I have a laptop:
[COLOR="Red"]Dell Inspiron 640m
1.66GHZ Core Duo T2300 CPU
1GB Memory
Integrated Intel GMA950 graphics adapter (up to 224MB)
Resolution of 1,280 x 800 pixels[/COLOR]

I installed ubuntu edgy eft (6.06) and now feisty fawn(7.04) with gnome and beryl(AIGXL). Everything worked fine except for a couple of things.

Now my first problem is that I dont know the difference between AIGLX(or AIGXL) and XGL. Is one better than the other and which one best suits my hardware (GMA950).

The reason Im asking is because in beryl Almost everything works except for the rain effect. I dont know whether its because of hardware incapability or that I need to have installed a beryl plugin or installing beryl with either AIGLX or XGL. either ways it doesnt work. Snow works and so on.

Another thing is that when you rotate the 3d screen cube whilst a video is playing it doesnt show the video or it flickers. How can i stop this. Am i supposed to use KDE rather than gnome?

Apparently the beryl wiki isnt showing here and the forums wont allow me to register so i can post any queries. Ubuntu is a great OS and beryl is fantastic but I like everything running smoothly and I need your help to achieve this.
Thanks

---

### Post by iggykoopa on 2007-08-13
The intel video cards for some reason seem to have trouble with the water effects, not sure why but its not working on my x3100 either. For the flickering video if your using totem try running gstreamer-properties and in the video section set the output to No XV and see if that helps.

---

