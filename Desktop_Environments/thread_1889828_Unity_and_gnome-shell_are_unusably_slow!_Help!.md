---
title: "Unity and gnome-shell are unusably slow! Help!"
date: 2011-12-02
forum: Desktop Environments
---

### Post by kio_http on 2011-12-02
Hi, 

On Ubuntu 11.10 the GTK3 stuff seem sluggish to use. Unity itself is faster than gnome-shell but applications launched withing gnome-shell are faster than in Unity.

I have the following problems

The UI takes time to update itself, e.g there is a lag between clicking a menu and when it actually appears. In gnome-shell when I use the search, text takes time to appear. Moving from the panel popups e.g if I click on the chat button in gnome-shell and move the mouse to the accessibility button is slow. Scrolling is slow in some applications and Ubuntu Software Center has an extremely laggy UI. 

Gnome-shell and Unity both use less RAM when idle than KDE but experience high CPU usage when the system is uses E.g 80% when repeatedly clicking on menus.

If I use GTK2 apps and environments like XFCE and LXDE it is extremely fast.

KDE 4.7.3 works with all sorts of effects like blur and is extremely fast on this system, so is Windows Vista. The computer is an Intel Atom n280 netbook with 2GB ram and a GMA 950 GPU.

Are there any setting adjustments or something to improve this?

While I am happy on KDE which has always been my primary environment, I find Unity impressive and would like to get it working properly.

---

### Post by CryptAck on 2011-12-02
Check your video settings. Unity uses some 3d effects that I've noticed caused the OSS version of my video "drivers" to cause lag. Once I switched to the Nvidia sources, it fixed itself.

---

### Post by kio_http on 2011-12-02
> **CryptAck said:**
> Check your video settings. Unity uses some 3d effects that I've noticed caused the OSS version of my video "drivers" to cause lag. Once I switched to the Nvidia sources, it fixed itself.

This card has an Intel GPU, the official driver is OSS and works fine under KDE, which features much more advanced compositing than mutter and arguably compiz.

---

### Post by 3Miro on 2011-12-02
Nvidia and some ATI cards have proprietary drivers, Intel is nice enough to provide all the source code so Intel cards work fine right out of the box. 

My guess is that the graphics are too weak for good Unity or Gnome-shell experience, Atoms are the weakest of the Intel chips after all (in both CPU and GPU power). LXDE and XFCE don't have 3D effects and hence work very fast. KDE has the kwin windows manager and kwin can works both with and without 3D effects. If KDE is working fine, I am guessing that you have desktop effects disabled (actually KDE will automatically disable the effects if things get slow).

Unity (3D) and Gnome-shell come with nice visual effects and those cannot be turned off. You can switch to Unity 2D and Gnome-fallback (i.e. Gnome-classic), those are the weak versions of Unity and the new Gnome.

PS: Compiz features more effects than Kwin and in my experience Kwin tends to be more efficient. In terms of hardware requirements, Kwin with effects and Compiz should be about the same. Kwin without effects is much lighter, of course. Gnome-shell has much weaker effects, but they are 3D effects nevertheless.

---

### Post by kio_http on 2011-12-05
> **3Miro said:**
> Nvidia and some ATI cards have proprietary drivers, Intel is nice enough to provide all the source code so Intel cards work fine right out of the box. 

My guess is that the graphics are too weak for good Unity or Gnome-shell experience, Atoms are the weakest of the Intel chips after all (in both CPU and GPU power). LXDE and XFCE don't have 3D effects and hence work very fast. KDE has the kwin windows manager and kwin can works both with and without 3D effects. If KDE is working fine, I am guessing that you have desktop effects disabled (actually KDE will automatically disable the effects if things get slow).

Unity (3D) and Gnome-shell come with nice visual effects and those cannot be turned off. You can switch to Unity 2D and Gnome-fallback (i.e. Gnome-classic), those are the weak versions of Unity and the new Gnome.

PS: Compiz features more effects than Kwin and in my experience Kwin tends to be more efficient. In terms of hardware requirements, Kwin with effects and Compiz should be about the same. Kwin without effects is much lighter, of course. Gnome-shell has much weaker effects, but they are 3D effects nevertheless.

1) I have all effects on on KDE including blur
2) I run Windows Vista on this netbook and it runs fine.

Are you trying to tell me that the system requirements of Gnome 3 are higher than that of WIndows Vista and KDE (with desktop effects)? The Intel Atom may not be an i7 but its powerful enough to run a modern OS interface (same goes for GMA 950). This netbook can even run Age of Empires 3, Spore and Sims 3 on Windows.

See screenshot,this is desktop composition on KDE (not effects off)

While I have always used KDE as main DE, I know that Gnome is supposed to be less resource hungry than it. Does this mean the tables have turned with Gnome 3?

---

### Post by kio_http on 2011-12-06
Bump

---

### Post by 3Miro on 2011-12-06
> **kio_http said:**
> 1) I have all effects on on KDE including blur
2) I run Windows Vista on this netbook and it runs fine.

Are you trying to tell me that the system requirements of Gnome 3 are higher than that of Windows Vista and KDE (with desktop effects)? The Intel Atom may not be an i7 but its powerful enough to run a modern OS interface (same goes for GMA 950). This netbook can even run Age of Empires 3, Spore and Sims 3 on Windows.

See screenshot,this is desktop composition on KDE (not effects off)

While I have always used KDE as main DE, I know that Gnome is supposed to be less resource hungry than it. Does this mean the tables have turned with Gnome 3?

When you run Vista is that with or without Aero. Under KDE, you should also check the desktop effects section to see if you have xrandr or OpenGL enabled, XRender can give you transparency and blur, but only OpenGL gives you full effects like a desktop cube.

I am not sure if Gnome 3 is more resource demanding than KDE, it may be just a bug. When KDE 4.0 first came out, it wouldn't run on the best Nvidia cards at the time. Unity on the other hand doesn't run on the 7xxx Nvidia series, you need at least 8xxx. It is not that your hardware is weak as much as it is old and newer software will likely have issues.

Gnome-fallback and Unity 2D should work great on your system.

---

### Post by kio_http on 2011-12-06
> **3Miro said:**
> When you run Vista is that with or without Aero. Under KDE, you should also check the desktop effects section to see if you have xrandr or OpenGL enabled, XRender can give you transparency and blur, but only OpenGL gives you full effects like a desktop cube.

I am not sure if Gnome 3 is more resource demanding than KDE, it may be just a bug. When KDE 4.0 first came out, it wouldn't run on the best Nvidia cards at the time. Unity on the other hand doesn't run on the 7xxx Nvidia series, you need at least 8xxx. It is not that your hardware is weak as much as it is old and newer software will likely have issues.

Gnome-fallback and Unity 2D should work great on your system.

You don't seem to understand, I know perfectly well how KDE works
. 

1) Yes vista is with aero
2) KDE did not need the best cards agreed it was buggy but I've been testing KDE pre releases since foreever 4.0 worked fine on an Nvidia Vanta and that is 1999.
3) KDE works on this Intel with desktop effects Open GL using plugins like blur (which is the most demanding plugin). On gnome 3 whether I use Unity, gnome-shell, unity 2d or whatever it makes no difference. Even if I run a gtk3 application under kde it is slow.

And no Xrender would never give you blur on KDE. All effects work on this computer including desktop cube etc.

My hardware is not that weak, it may not run modern games but it runs Visual Studio 2010 on Windows and can handle databases and all. On KDE it works just as fast as any other machine would. 

Unity 2d and gnome-fallback are also slow here. Also KDE, Windows vista, 7 and 8 works (and always worked)with full desktop effects on a Geforce 5200 for me. And that is a 2003 graphic card. If Gnome cannot provide an experience without desktop composition (using the same UI and WM)then this is a bug. More so if it needs Geforce 8 or higher. Such a requirement would imply higher resource than many 3d games and all versions of Windows (including windows codename 8).

---

### Post by 3Miro on 2011-12-06
> **kio_http said:**
> On gnome 3 whether I use Unity, gnome-shell, unity 2d or whatever it makes no difference. Even if I run a gtk3 application under kde it is slow.


That's a bug, desktop effects may be slower, but general GTK3 shouldn't be. It is strange that I cannot find any information about others having the same issue. You may want to report this on Launchpad.

---

### Post by kio_http on 2011-12-06
> **3Miro said:**
> That's a bug, desktop effects may be slower, but general GTK3 shouldn't be. It is strange that I cannot find any information about others having the same issue. You may want to report this on Launchpad.

I see, but which package should I file the bug against. I have no idea about how gnome packages are named.

Its not always that slow. 

Software center is quite slow though.
Also in general most GTK3 applications feel slightly unsmooth compared to KDE/QT and GTK2 if you know what I mean. 

On the unity top bar if you click a menu e.g Help in firefox and then move the mouse to File, is the transition between menus very smooth? For me it doesn't update the menu changes quite smoothly.

---

### Post by 3Miro on 2011-12-06
> **kio_http said:**
> I see, but which package should I file the bug against. I have no idea about how gnome packages are named.

Its not always that slow. 

Software center is quite slow though.
Also in general most GTK3 applications feel slightly unsmooth compared to KDE/QT and GTK2 if you know what I mean. 

On the unity top bar if you click a menu e.g Help in firefox and then move the mouse to File, is the transition between menus very smooth? For me it doesn't update the menu changes quite smoothly.

Unity 2D should have everything reasonable smooth. GTK apps should take a bit longer to load under KDE, but they should work fine afterwards.

If things are bad under KDE, then the bug is either with GTK3 or the driver. I would call it for the hardware driver (i.e. the Xorg driver for your specific Intel), but I can't be sure.

---

### Post by kio_http on 2011-12-06
> **3Miro said:**
> Unity 2D should have everything reasonable smooth. GTK apps should take a bit longer to load under KDE, but they should work fine afterwards.

If things are bad under KDE, then the bug is either with GTK3 or the driver. I would call it for the hardware driver (i.e. the Xorg driver for your specific Intel), but I can't be sure.

How is the menu transition thing for you? I think it may be a funny quirk as gnome 3 is new and possibly has not undergone much performance testing yet. E.g KDE 4.0 to 4.5 focused on features and only after that have they really taken performance into consideration. [I wrote this about performance tuning KDE]("http://ubuntuforums.org/showthread.php?t=1889034"). Any similar thing for GNOME. 

Note while I don't plan to use Unity and gnome I would like to test it:KS

I can hardly find any settings in Gnome 3 and Unity any chance that this will change in some time.

Gnome advanced settings has nothing advanced about it and provides almost no big setting changes (why did they name it that?)

CCSM is still not what I am looking for.

---

### Post by 3Miro on 2011-12-06
> **kio_http said:**
> How is the menu transition thing for you? I think it may be a funny quirk as gnome 3 is new and possibly has not undergone much performance testing yet. E.g KDE 4.0 to 4.5 focused on features and only after that have they really taken performance into consideration. [I wrote this about performance tuning KDE]("http://ubuntuforums.org/showthread.php?t=1889034"). Any similar thing for GNOME. 


11.04 Unity was a bit sluggish on Pentium Dual Core with GPU one generation above yours. Gnome-shell with Fedora 15 was fine (it was buggy, but it was fast enough). Currently, Unity and Gnome-shell work fine on Sandy Bridge i7 Laptop and Nvidia GTX260 Phenom x6 desktop, but those are pretty high end.

I remember KDE 4.1 had some big issues on GF 8600 before they fixed some bugs for KDE 4.2 (actually I think the issue was Nvidia, not KDE).

> 
Note while I don't plan to use Unity and gnome I would like to test it:KS

Makes sense, I use xfce, but I do keep track of Gnome-shell and Unity.

> 
I can hardly find any settings in Gnome 3 and Unity any chance that this will change in some time.

Gnome advanced settings has nothing advanced about it and provides almost no big setting changes (why did they name it that?)

CCSM is still not what I am looking for.
One of the biggest criticisms of both Gnome-shell and Unity are the lack of customizations. Those take radically different approach compared not only to KDE, but the old Gnome 2 as well. You can expect a big culture shock coming from the most customizable DE out there.

CCSM has some Unity specific options and you can install Ubuntu-Tweaks to get a few more options.

[https://launchpad.net/~tualatrix/+archive/next](https://launchpad.net/~tualatrix/+archive/next)

Gnome-shell can be customized with extensions that you can download and install. The problem is that unless you are fluent in Javascript, you cannot make your own extensions and you have to rely on what other people have done. Look for Gnome-shell extensions on:

[https://extensions.gnome.org/](https://extensions.gnome.org/)

(they seem to update this page a lot, last time I checked there were only 10 or so extensions)

---

### Post by ajarmoniuk on 2011-12-14
I'm using a ThinkPad T500 which also features an Intel graphics card and I'm also experiencing Unity to be slower than Gnome3. That's strange to me, but I guess the Oneiric Unity WM is a bit slower than the one used in Natty (which was very fast).

I can't get used to Gnome Shell, I find Unity to be much more comfortable, but it's SLOW...

---

