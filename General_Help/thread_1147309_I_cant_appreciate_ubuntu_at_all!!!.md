---
title: "I cant appreciate ubuntu at all!!!"
date: 2009-05-03
forum: General Help
---

### Post by VyperX on 2009-05-03
Hello, I've been an Ubuntu fan for several years now and I just installed the version 9.04 (32 bit) on my laptop but I am having graphic problems with it now.:(
I'm still a noob at ubuntu, but I'm willing to improve.:P
I used to have the Gutsy Gibon version and it worked PERFECTLY!!! 
I dont know why it is not working well at all...

Here is an image of the problem that I am having now:
[http://img408.imageshack.us/img408/7514/dsc0074v.jpg]("http://img408.imageshack.us/img408/7514/dsc0074v.jpg")

I can't install any drivers for my video card as you can see:
[http://img131.imageshack.us/img131/8937/screenshothardwaredrive.png]("http://img131.imageshack.us/img131/8937/screenshothardwaredrive.png")

My laptop:
Toshiba Satellite A215-S4767
AMD Turion 64 X2 @ 2.2 GHZ
2 GB RAM
ATI Radeon X1200
250 GB HDD

Also, I can't appreciate the nice graphic effects that Ubuntu has because if I put them my computer would freeze. I DID put them on version 7.10 (gutsy gibon) and I had no problems with them.

I'll appreciate any kind of help!!!:)****

---

### Post by ashmew2 on 2009-05-03
> Hello, I've been an Ubuntu fan for several years now and I just installed the version 9.04 (32 bit) on my laptop but I am having graphic problems with it now.:sad:
I'm still a noob at ubuntu, but I'm willing to improve.:razz:
I used to have the Gutsy Gibon version and it worked PERFECTLY!!! 
I dont know why it is not working well at all...

Here is an image of the problem that I am having now:
[http://http://img408.imageshack.us/i...4/dsc0074v.jpg]("http://http//img408.imageshack.us/img408/7514/dsc0074v.jpg")Hi , Well as far as i believe , you should stick with Gutsy Gibbon if it works perfectly for you.But then again , if you like to be kept up to date with the latest what FOSS has to offer , i cant blame you much. ;)

Also , i cant understand exactly what problem you are having , and you could have just posted the screenshots of your monitor instead of clicking photos with your camera. :P 
Just Press the Print Screen button , that will be much clearer.

PS - The links in your post , there's an extra http:// at the start ..So it will just open to http.com instead of imageshack ;)

---

### Post by pbpersson on 2009-05-03
I was not able to view either one of your images, the links do not work

---

### Post by VyperX on 2009-05-03
> **ashmew2 said:**
> Hi , Well as far as i believe , you should stick with Gutsy Gibbon if it works perfectly for you.But then again , if you like to be kept up to date with the latest what FOSS has to offer , i cant blame you much. ;)

Also , i cant understand exactly what problem you are having , and you could have just posted the screenshots of your monitor instead of clicking photos with your camera. :P 
Just Press the Print Screen button , that will be much clearer.

PS - The links in your post , there's an extra http:// at the start ..So it will just open to http.com instead of imageshack ;)

I don't want to stick with Gutsy Gibbon because it won't detect my wireless card unless I type some commands on terminal and I wouldn't be up to date.

Anyway, I've fixed the links for the images.

---

### Post by ashmew2 on 2009-05-03
By that last screenshot , do you mean you cannot install Drivers for your ATI card ? And is your WiFi working ?

---

### Post by VyperX on 2009-05-03
> **ashmew2 said:**
> By that last screenshot , do you mean you cannot install Drivers for your ATI card ? And is your WiFi working ?

My wifi is working perfectly, with that image, I'm just showing you that there are no drivers for my ati video card.

---

### Post by pastalavista on 2009-05-03
> **VyperX said:**
> My wifi is working perfectly, with that image, I'm just showing you that there are no drivers for my ati video card.My graphics were also borked when I upgraded to 9.04. There are open source drivers in use but they don't work as well as the fglrx drivers in previous releases. The only option is to use an earlier release. 8.10 (Intrepid) uses the old drivers and is still supported whereas Gutsy isn't any more so you might try it if 3D graphics are important to you. I don't use compiz or play games so I don't need the drivers that much.

---

### Post by earthquakefish on 2009-05-03
I haven't upgraded to Jaunty for precisely this reason as ATI dropped support for a bunch of cards in their 9.4 release of Catalyst (X1200 being one of them).  The version of xorg installed on Jaunty requires 9.4 or higher.

There isn't really much you can do,

1) complain to ATI if you are so inclined
2) use Intrepid 8.10 instead
3) or continue using the open-source version installed

Myself I'm using the open-source version (radeon driver) under Intrepid and finding the 2d faster than fglrx.  As I don't really use 3d effects much anyways.  I'm also using Xubuntu with xfwm4 acting as the compositor, which is much less resource intensive.  The overall speed right now actually feels faster using the radeon driver.

Good luck.

---

### Post by VyperX on 2009-05-03
> **earthquakefish said:**
> I haven't upgraded to Jaunty for precisely this reason as ATI dropped support for a bunch of cards in their 9.4 release of Catalyst (X1200 being one of them).  The version of xorg installed on Jaunty requires 9.4 or higher.

There isn't really much you can do,

1) complain to ATI if you are so inclined
2) use Intrepid 8.10 instead
3) or continue using the open-source version installed

Myself I'm using the open-source version (radeon driver) under Intrepid and finding the 2d faster than fglrx.  As I don't really use 3d effects much anyways.  I'm also using Xubuntu with xfwm4 acting as the compositor, which is much less resource intensive.  The overall speed right now actually feels faster using the radeon driver.

Good luck.

I think I'm going to install Intrepid 8.10... I don't know whether I should install the 32 bit version or the 64 bit version... which one should I install??

And so there will never be more drivers for my ATI X1200 video card?? in ubuntu???

Thanks!

---

### Post by Mirge on 2009-05-03
Might re-check ATi's site and see if one of their drivers works (try the latest they released I'd say) for your specific card.

---

### Post by VyperX on 2009-05-03
> **Mirge said:**
> Might re-check ATi's site and see if one of their drivers works (try the latest they released I'd say) for your specific card.

There are no drivers for X1200...

---

### Post by ashmew2 on 2009-05-04
Well i dont know if ATI is going to release drivers for your cards for 9.04 , but i think that in say 6 months (or more ? ) nouveau will be up to speed ...

---

### Post by VyperX on 2009-05-04
> **ashmew2 said:**
> Well i dont know if ATI is going to release drivers for your cards for 9.04 , but i think that in say 6 months (or more ? ) nouveau will be up to speed ...

So there's not going to be any problems  wih my graphics card in the  next version of ubuntu??

---

