---
title: "Ubuntu 12.04 on a Intel P4 machine"
date: 2013-08-11
forum: Desktop Environments
---

### Post by psyllex on 2013-08-11
Hi all,

I have an old p4 machine with 2GB of ram that I would like to put ubuntu desktop on.  All I really want to do with this is go on the internet and play some movies.  Can this machine handle it or will unity be too much for it?  Please let me know your opinion.  Thanks.

---

### Post by davetv on 2013-08-11
12.04 works fine on my p4 2.8 and its only got 1 gig of RAM. I had to tweak some stuff to make the onboard Intel 965G video to work was the only thing but it wasn't hard. With luck you have a different graphics chip.

---

### Post by psyllex on 2013-08-11
> **davetv said:**
> 12.04 works fine on my p4 2.8 and its only got 1 gig of RAM. I had to tweak some stuff to make the onboard Intel 965G video to work was the only thing but it wasn't hard. With luck you have a different graphics chip.

I have a really cheap graphics card.  Well we'll see how it works.

---

### Post by SeijiSensei on 2013-08-11
Depending on what types of videos you are watching, the graphics card might need to be upgraded.  On an older machine, I recommend an NVIDIA card so you can use the "VDPAU" extensions to offload video decoding to the graphics card.  The P4 is too slow to handle 720p or higher H.264 decoding in the CPU.

Any recent NVIDIA card supports VDPAU.  If your machine does not have a PCI Express slot, you'll need a standard PCI card like [this one](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187213).

I recommend using SMPlayer for watching the videos as it has a convenient GUI for choosing what video decoder to use.  A "sudo apt-get install smplayer" should be all you need.

---

### Post by psyllex on 2013-08-11
> **SeijiSensei said:**
> Depending on what types of videos you are watching, the graphics card might need to be upgraded.  On an older machine, I recommend an NVIDIA card so you can use the "VDPAU" extensions to offload video decoding to the graphics card.  The P4 is too slow to handle 720p or higher H.264 decoding in the CPU.

Any recent NVIDIA card supports VDPAU.  If your machine does not have a PCI Express slot, you'll need a standard PCI card like [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187213").

I recommend using SMPlayer for watching the videos as it has a convenient GUI for choosing what video decoder to use.  A "sudo apt-get install smplayer" should be all you need.

Cool thanks for the tips!

---

### Post by carlexpc on 2013-08-12
Your machine is a bit old for Ubuntu Unity. Try installing Lubuntu or Xubuntu instead. Both are still Ubuntu, but with lighter desktop environment.

---

### Post by nashtrik on 2013-08-13
I run the same configuration as yours... old intel P4 processor, 2Gigs of DDR3 RAM, no separate graphics card, and a 9 year old 40GB PATA hard drive....it runs ubuntu 12.04 seamlessly which I use chiefly for surfing the net and watching movies on my DVD drive.....should work for you as well...moreover.. as I don't like the Unity interface( Compiz config utility in 12.04 doesn't have the Unity plugin Rotated option to shift the unity taskbar to the bottom of my screen unlike ubuntu 11.10), I have installed the Cinnamon Desktop environment which works great as well..absolutely no hassles..!

---

### Post by SeijiSensei on 2013-08-13
Watching a movie from a DVD does not push the hardware the way watching an H.264-encoded HD video stream does.  DVDs top out at a resolution of 720x480 and are encoded with the ancient MPEG2 codec.  A 1280x720 or, worse, 1920x1080 high-definition video encoded with the more heavily compressed H.264 codec would stutter so badly on your machine as to be unwatchable.

---

### Post by 3rdalbum on 2013-08-14
Some people replying here... to say it nicely, they probably haven't used 12.04.

You can definitely use Ubuntu 12.04 on a Pentium 4. If the default Unity 3D desktop is a bit slow, you can just log into the 2D version of Unity.

I used Unity 3D on a netbook, which is a lot slower than a P4.

If you want something later than 12.04 you can try 13.04, but if your GPU doesn't have official support you may only get decent performance on Lubuntu (LXDE) because Unity 2D is not available in 12.10 or later.

---

### Post by crazymonkey05 on 2013-08-14
i dont know what you guys are talking about i have a intel Celeron D 3.46 Ghz and 2GB ram and unity runs smooth as butter on my machine

---

