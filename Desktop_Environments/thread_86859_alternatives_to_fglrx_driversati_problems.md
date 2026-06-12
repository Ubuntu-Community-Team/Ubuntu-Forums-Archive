---
title: "alternatives to fglrx drivers?/ati problems"
date: 2005-11-06
forum: Desktop Environments
---

### Post by jamesford on 2005-11-06
wondering if ther are any usable alternatives to fglrx for my radeon 9600.

i really need 3D accelleration but whenever i install fglrx and configures it (ive followed ALL the guides and howto's) my 2D performance gets completely crippled. for example if i watch a movie at full screen it uses all of my cpu and the movie is really lagged, like there are whole blocks moving slowly around. same happens when moving windows around on desktop.3D however works great.

this is not the case without fglrx drivers being used, then movies are smooth like they were in hoary.

so it seems i cant have both 3D and 2D unless someone can help me either find an alternative driver or another solution to my problem

---

### Post by bjourne on 2005-11-07
There are two drivers availible for modern ATI cards, fglrx and radeon. fglrx is very good on 3d, but bad on 2d graphics. radeon is the free driver and it is good at 2d, but has no support for dri which is needed for 3d accelerated graphics. However unless you have a really slow computer video should play decently no matter which driver you have. It may be that you do not have the xorg XVideo extension installed/enabled or that it doesn't work with the settings you have choosen for your fglrx driver. XVideo makes video playing much faster.

---

### Post by bionnaki on 2005-11-07
perhaps you should enable dma on your drives.

---

### Post by Khannie on 2005-11-07
Yup. I'll bet it's the ol' dma. You're looking for info on hdparm. I think there's some info in the 5.04 unofficial guide.

---

### Post by jamesford on 2005-11-07
dma is enabled, its not that. the xvideo thing sounds more interesting. what is it? where do i get it and how do i enable it, ot how do i check if its enabled ? i dont seem to have any reference to xvideo in xorg.conf

btw im using totem-xine, with gstreamer performance is even worse

---

