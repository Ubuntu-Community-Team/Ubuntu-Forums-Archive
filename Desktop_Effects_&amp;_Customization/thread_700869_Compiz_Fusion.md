---
title: "Compiz Fusion?"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by SIXAXIS on 2008-02-18
Hey guys, 

Can you guys help me get Compiz-Fusion up and running on my machine? I'm using the 64-bit version of Ubuntu Gutsy Gibbons and I've installed Compiz-Fusion. Everytime that I try to enable it, I get the error "Desktop Effects could not be enabled". I'm using a Compaq Presario V2000 and it has an ATI Radeon XPRESS 200M graphics card in it. I have the official ATI drivers installed with the restricted drivers turned on. Can someone please help me get Compiz-Fusion running? I'm dying for some eye candy!

---

### Post by Jammin80503 on 2008-02-19
I'm having the same problem with my e-Geforce 7200.
bump.

---

### Post by kristjans on 2008-02-19
Did you already install proprietary nVidia drivers? If not, [here's a guide](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) (top of the page).

edit: Sorry, the second post got me off the track. Guide for ATI [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). Unfortunately you have a good chance of not getting it working properly with XPRESS 200M, its drivers are not very good. If you don't get it working, but are adventurous enough, you may *test* out Enlightenment E17, it has some great 2D eye candy.

---

### Post by SIXAXIS on 2008-03-02
I'll try Enlightenment because I've tried every way I can to get compiz fusion running. I even deleted my 64-bit Linux and installed the 32-bit version (which I'm using for good now).

---

### Post by smartboyathome on 2008-03-02
Did you try using Envy? I used it to install the drivers for my NVidia GeForce 6100 (on a 64 bit machine) and Compiz works great on it.

---

### Post by SIXAXIS on 2008-03-06
> **smartboyathome said:**
> Did you try using Envy? I used it to install the drivers for my NVidia GeForce 6100 (on a 64 bit machine) and Compiz works great on it.

I tried Envy, but when I try uninstalling or installing a driver, it searches for .deb files and doesn't find any so it closes. Can some one help me use Envy? BTW, I have the ATI restricted drivers already installed, but there is no compiz, effects, or composite extension. But Unreal Tournament 2004 demo works fine.

---

### Post by santiagoward2000 on 2008-03-06
> **SIXAXIS said:**
> Hey guys, 

Can you guys help me get Compiz-Fusion up and running on my machine? I'm using the 64-bit version of Ubuntu Gutsy Gibbons and I've installed Compiz-Fusion. Everytime that I try to enable it, I get the error "Desktop Effects could not be enabled". I'm using a Compaq Presario V2000 and it has an ATI Radeon XPRESS 200M graphics card in it. I have the official ATI drivers installed with the restricted drivers turned on. Can someone please help me get Compiz-Fusion running? I'm dying for some eye candy!

I'm using the same card on my laptop and it works! You'll need to install **xserver-xgl** to get it working. Look for it in **Synaptics** or open a terminal and type:
```
sudo apt-get install xserver-xgl
```
Then restart your computer and try to run it again.
Good luck!

_EDIT:_
> **Jammin80503 said:**
> I'm having the same problem with my e-Geforce 7200.
bump.

What I posted is for ATI cards, it won't work with NVidia. Sorry :(

---

### Post by boofly on 2008-04-09
I am new to Linux, and found the same problems with a Compaq Presario and 200M video card not running Desktop Effects / Compiz.  I'm happy to report that installation of XGL solved the problem for me and it runs very nicely indeed, now.  I didn't do any mucking around with shared memory or other suggestions from elsewhere.
One thing I noticed, it ran very nicely at first, then I went and turned on some effects (reflection?) and it became an absolute dog. So there's definitely some things to stay away from!  But overall, totally satisfied and my system seems to be stable.
I installed the proprietary ATI drivers, by the way.
Cheers
A

---

