---
title: "Neverball: No sound &amp; choppy graphics"
date: 2008-06-04
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2008-06-04
Hello all,

I am hoping anyone can assist me with a couple of problems I have with getting Neverball to work.

1) Sound:  Simply put, there is none.  I have a Sound Blaster X-Fi installed with OSS.   It works with audio files and pretty much anything in Ubuntu itself.  It also works on the internet with Firefox, but thus far I can't get it to work with Neverball (It also isn't working with Gens either).

2) Video is choppy:  I have an nVidia 5200 series card and it works beautifully in Windows.   Here in Ubuntu with Neverball, it seems a bit "slow" and the framerates are low.   I do have much of the non-essential items turned off, but unless I go down to 640 resolution (800 is fairly OK too), I cannot really run it full screen.   I DO have the 3D accelerator driver installed and that did improve things drastically from when I first installed Neverball (it wasn't even playable before installed the 3D drivers).

I did get to thinking that perhaps Ubuntu didn't install an up to date 3D driver?  Is there any way I could check this?  Is there anyway I could tweak the current set up to improve performance?

I have a 2.8ghz machine with 1.5 gig of RAM.

Any advice would be much appreciated.

Thank you,

Geo

---

### Post by jukingeo on 2008-06-06
Hello?  Can anyone help me out?

Thanx,

Geo

---

### Post by fredbird67 on 2010-09-05
I too would like to see this corrected.  While I have sound, the graphics in Neverball are very choppy.  What's even more strange is I'm running the Xfce edition of Linux Mint, which is a little lighter than GNOME, on a machine with 1 GB of RAM, and you'd think that that's not supposed to happen under those conditions -- but it is...

---

### Post by fredbird67 on 2010-09-05
I just tried what you mentioned about the graphics by downloading and installing the NVidia chipset video driver (you know, the one that enables Compiz and all that fun stuff), and that fixed the problem for me, so if you haven't done that already, you might want to.  On the GNOME desktop (I'm going to assume that that's the desktop environment you're running here), if I remember correctly, I think you go to System --> Administration --> Hardware Drivers.  From there, just follow the dialog boxes to install the 3D drivers.  In my case, that greatly smoothed out the animation.

As for the sound though, I don't really know what to tell ya, as I'm not having any problems with the sound.  I'm going to assume here that you've checked to make sure you're not muted or anything.  Also, Neverball has its own volume settings for the music and the sound effects, which you might want to check as well.  Also, is it possible that your speakers may have come unplugged from the back of your computer?

Fred in St. Louis

---

### Post by jukingeo on 2010-12-10
> **fredbird67 said:**
> I just tried what you mentioned about the graphics by downloading and installing the NVidia chipset video driver (you know, the one that enables Compiz and all that fun stuff), and that fixed the problem for me, so if you haven't done that already, you might want to.  On the GNOME desktop (I'm going to assume that that's the desktop environment you're running here), if I remember correctly, I think you go to System --> Administration --> Hardware Drivers.  From there, just follow the dialog boxes to install the 3D drivers.  In my case, that greatly smoothed out the animation.

As for the sound though, I don't really know what to tell ya, as I'm not having any problems with the sound.  I'm going to assume here that you've checked to make sure you're not muted or anything.  Also, Neverball has its own volume settings for the music and the sound effects, which you might want to check as well.  Also, is it possible that your speakers may have come unplugged from the back of your computer?

Fred in St. Louis

Hello,

I found the trouble to be with the video card.  I have an ATI 7600XT and after the time I wrote the OP on this I found out that this card has a problem with getting "stuck" at 60hz setting and when this happens in Linux, you also loose the Open GL capability.

Soooo long story short, I am going to go back to Nvidia after this poor ATI experience, BUT my computer's power supply can't handle a larger video card to be up to date.    Two problems against me are a small 250watt power supply AND AGP.   I figured by the time I stick MORE money in my computer, I am going to wait to get a newer computer with an Nvidia card.

Still saving up for it though...

Geo

---

### Post by jukingeo on 2011-01-16
Hello All,

Well, the problem WAS with the video card!  I bought a new computer with an Intel i5 650 3.2ghz processor.  This is one of those processors that comes with the on-board graphics acceleration.

Now Neverball works like a charm!

---

