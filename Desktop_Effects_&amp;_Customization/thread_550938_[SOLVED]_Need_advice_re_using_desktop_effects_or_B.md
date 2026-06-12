---
title: "[SOLVED] Need advice re using desktop effects or Beryl"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by dylanologist on 2007-09-14
I'm running Ubuntu Feisty on a desktop w/ Core 2 Duo E4400 (2.0ghz), 1gb ram, and Intel integrated graphics (GMA 3100 I think).

I tried to get desktop effects working on my machine but it's not happening.  My question is this:

Will the next release of Ubuntu, due in October, be likely to allow me to run desktop effects on my current system?  Or is running it with Intel integrated graphics just a bad idea?

Also, my xorg.conf shows me running a "Generic Video Card" with the driver being "vesa".  I've never been able to change to the Intel driver.  Will a new version of Ubuntu start fresh in identifying my graphics card and choosing a driver?

I guess if there's a chance that the next version of Ubuntu will make these problems go away, then I won't bother spending hours looking for solutions right now.

Thanks for any advice you have to offer.

P.S.  I also want to upgrade to a widescreen LCD monitor at Christmas, so getting the correct graphics card driver will probably be very useful when I upgrade to a really good monitor.

---

### Post by cubeist on 2007-09-14
Have you tried using a restricted driver... I am not 100% sure if there is one, but look in "System/Administration/Restricted Driver Manager".  As far as I know there is decent support for intel graphics on linux.  If there is no restricted driver available, try searching the intel site for a linux driver.

Hopefully other, more experienced intel people will add some useful info... I am more of an nvidia user...

---

### Post by Maestro23 on 2007-09-14
You do know that the integrated card relies on your system's RAM for storage which will cause a performance penalty as both the CPU and GPU have to access memory over the same bus. 

So when it comes to the pretty 3-D eye candy/effects you are trying to use, the card is taking some of that 1GB of RAM you have to try and display the effects.  This is causing a bottleneck in your system.

I would look into getting a new video card with its own dedicated memory when you go shopping for the new monitor.  

Do you run windows XP/Vista also.  Vista itself is a resource hog.  And if you play any games, the current setup of your 1GB RAM and the integrated card may not be up to task.

I'm not sure what the support for the Intel chipset will be in the next version.  I would look into getting a dedicated video card though in the long run.  No sense in choking that processor.

Just my 2 cents man.  Welcome to Ubuntu man. :guitar:

---

### Post by dylanologist on 2007-09-14
Thanks for the advice.  I'll wait and see if the new version of Ubuntu helps me out at all, but I was already halfway thinking about getting a dedicated video card anyway.  Once I get my new monitor, I'm going to want to show it off with some cool graphics.

As for restricted drivers, every time I try to access that manager I get the message that I have no restricted drivers and it closes.  I assume that means that there is nothing available for me.  Besides, I thought Intel offered open source drivers (and thus they wouldn't be restricted).  Am I wrong about that?

---

### Post by cubeist on 2007-09-14
direct from the intel site

try either this
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&ProductID=2568&DwnldID=13653&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&ProductID=2568&DwnldID=13653&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng")

or this
[http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=2568&DwnldID=10783&agr=N&lang=eng&PrdMap=2568]("http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=2568&DwnldID=10783&agr=N&lang=eng&PrdMap=2568")

I didn't read through any of the specs or release notes ... that's up to you to do ... so I don't know if either of those will work with your system, but at least it is a place to start....

Also I agree dedicated graphics are better, but they are not needed for beryl... at the moment I am using an hp laptop with 1GB of RAM and an integrated nvidia 6150 and beryl is smooth as glass... no hiccups at all...

---

### Post by dylanologist on 2007-09-17
Thanks for the links.  I checked out the release notes on those driver downloads, and it all seemed a bit above my head.  I think I'll just wait until the next release of Ubuntu and see if I have any better luck using desktop effects.

I'm just not sure if, when I upgrade to the next version of Ubuntu, it will automatically update the drivers for my hardware, or if the update would maintain all the same hardware settings and drivers.

---

### Post by PlantHead on 2007-09-18
[http://ubuntuforums.org/showthread.php?t=494943&highlight=g33](http://ubuntuforums.org/showthread.php?t=494943&highlight=g33)

Try the above thread, should fix your problems.

---

### Post by dylanologist on 2007-10-02
Finally bought a new NVIDIA graphics card.  Had a hell of a time trying to get a driver installed that would work for it.  So I just upgraded to Ubuntu 7.10 Beta (Gutsy) and that solved my driver problems, and the built in desktop effects seem to be working fine.  Still finding my way around in the new version of Ubuntu, but I'm happy that it solved persistent problems that I've had with graphics drivers in Feisty.

---

