---
title: "video player settings in hoary"
date: 2005-04-07
forum: Desktop Environments
---

### Post by shmonkey on 2005-04-07
I have installed various video/multimedia players (gxine, totem-gstreamer, totem-xine) but when I come to change the brightness/contrast it has no effect at all on the picture.

Anyone got any ideas what could be causing this problem ?

I tried a live CD (Knoppix 3.7) and the video settings worked OK on that.

---

### Post by orion_114 on 2005-04-08
I have found that vlc is the best movie player for my system. It isn't the prettiest out there but its got all sorts of functionality. I could be mistaken, but I believe it has some tools for adjusting the colour settings of the movie.

---

### Post by shmonkey on 2005-04-08
I think it's a general problem, I have also installed mplayer and have the same problem with that. I have never had this sort of problem with these players before ????

So am I missing some library or something is it related to my video card (Nvidia 6600GT) ?

---

### Post by orion_114 on 2005-04-08
Have you installed the NVidia drivers yet ?
Check out these links:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

---

### Post by shmonkey on 2005-04-08
yep the nvidia drivers are installed and 3D acceleration is working OK.

I did try vlc as suggested and it works well, I can alter brightness etc. I also had to use libesd-alsa0 instead of libesd0 otherwise I had to kill esd to get the sound to work.

Still strange why these brightness/contrast adjustments did not work with Mplayer, Totem and Gxine.

Still vlc it is then !

---

