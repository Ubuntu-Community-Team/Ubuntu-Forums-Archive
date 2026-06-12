---
title: "Celestia"
date: 2006-07-24
forum: Education &amp; Science
---

### Post by calvinthomas on 2006-07-24
Does anyone know why after installing Celestia when I click on it it comes up on the taskbar starting Celexia, waits about 5 seconds and then just vanishes  without starting up? If so, is there a way of fixing this?

Calv

---

### Post by editrix on 2006-07-25
> **calvinthomas said:**
> Does anyone know why after installing Celestia when I click on it it comes up on the taskbar starting Celexia, waits about 5 seconds and then just vanishes  without starting up? If so, is there a way of fixing this?
Calv

First off, does it really say "starting *Celexia*" or is that just a typo?

I don't know the program (but it sounds wonderful). Did you check the list of bugs?
[http://shatters.net/forum/viewforum.php?f=3](http://shatters.net/forum/viewforum.php?f=3)

---

### Post by mcduck on 2006-07-25
Try starting it from terminal and post any error messages here..

---

### Post by calvinthomas on 2006-07-25
Sorry that was a typo, I have resolved this now, the problem went away when I correctly installed my x700 graphics card drivers, along with my inability to use lyricue and google earth!

Calv

P.S If you haven't used Celestia before its really worth checking out, im not big on space and astrology but it is interesting to see the universe and beyond!

---

### Post by taurus on 2006-07-25
> **calvinthomas said:**
> 
P.S If you haven't used Celestia before its really worth checking out, im not big on space and astrology but it is interesting to see the universe and beyond!
It's ASTRONOMY, NOT astrology!!!  ](*,) 

Astronomy = science
Astrology = a pile of crap

---

### Post by pcit on 2006-07-30
Does anyone have the  big lag during the celestia?
My cpu time got to 100% @@

---

### Post by MarkSheely on 2006-07-30
Celestia is very demanding on any computer's resources.  In my experience, it is even more so in Linux.  I've compared memory usage, CPU usage, etc., between Celestia and Windows on several different models of laptops - running Celestia in Linux always demanded more resources than in windows. 

I had one laptop that could run Celestia fine in Windows, but would overheat and shut itself down if I tried running Celestia in Linux.  

This may have something to do with the fact that the gentleman who spearheaded the development of Celestia worked for Microsoft for a while.
It was probably developed with Windows in mind.  

These are all just my opinions and expereinces, anyway.  Maybe some more savvy linux users out there can show us both how to take care of these problems.

--Mark

---

### Post by Ripfox on 2007-05-01
I just saw a reference to this program on one of those "CSI" type shows (there are like 300 of them?) This guy was using it as a diary...they even made a reference to open source and explained what that meant....cool.

---

### Post by heinar on 2009-01-02
I've just installed Intrepid, and went to install Celestia. I'm new at this but tried my best. I followed [these]("http://www.autopackage.org/docs/howto-install/") instructions, and was directed to the terminal where it said: 

The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection A --> OK to install support code now? (Y/n): 

So I select Y, because I downloaded autopackage.tar.bz2 to my desktop. It then gave me this message: 

autopackage/libexec/autosu-gtk: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I've downloaded the Celestia install file thing from the website twice and downloaded autopackage.tar.bz2 a bunch but I'm still getting this same message. How can I fix it?

---

### Post by kleeman on 2009-01-03
> **heinar said:**
> I've just installed Intrepid, and went to install Celestia. I'm new at this but tried my best. I followed [these]("http://www.autopackage.org/docs/howto-install/") instructions, and was directed to the terminal where it said: 

The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection A --> OK to install support code now? (Y/n): 

So I select Y, because I downloaded autopackage.tar.bz2 to my desktop. It then gave me this message: 

autopackage/libexec/autosu-gtk: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I've downloaded the Celestia install file thing from the website twice and downloaded autopackage.tar.bz2 a bunch but I'm still getting this same message. How can I fix it?
I strongly advise you to install celestia from the standard Ubuntu repository using synaptic. Don't use autopackage unless there is no alternative.

---

### Post by heinar on 2009-01-05
What if that isn't possible? The only linux link is this autopackage that I can tell.

---

### Post by heinar on 2009-01-05
If there is no other option I can find, what should I do?

---

### Post by kleeman on 2009-01-06
Go to the "Software Sources" app (System----> Administration). Make sure that the "Community maintained Open Source Software (universe)" radio button is filled.

Got to the Add/Remove... menu item in Applications. Search for celestia. Install and profit.

---

### Post by skywatcher on 2009-01-29
I have just installed Celestia on Intrepid with Synaptic, but it doesn't work correctly.

I installed the KDE frontend which has a few (limited) menu items. It also doesn't show any stars, even when I select this option, although it does show the star names (e.g. the members of the Pleyades).

I then removed the KDE frontend and installed the GNOME frontend. Celestia now has a different appearance, but I cannot get to the menus - they briefly appear when I click on them in the menu bar, but then disappear again.

Has anyone experienced this problem?

---

### Post by vanadium on 2009-01-29
You will need to disable desktop effects while you run Celestia. For many graphical cards, compiz still does not work well together with applications that use 3D acceleration themselves (Celestia, Google earth, ...).

If you do not want to loose all your custom compiz settings, do this with the command line:

```

metacity --replace

```

and

```

compiz --replace

```

to switch back to compiz. Do this preferably with no applications open.

---

### Post by skywatcher on 2009-01-29
Thanks, Vanadium, that solves the problem, although I don't understand why!

---

### Post by vanadium on 2009-01-29
Compiz is the new Windows manager that features nice and sometimes spectacular visual effects. These rely among other things on 3D acceleration, provided by your graphical card.

Compiz still has to be considered as early software, though. In addition, many graphical cards with proprietary drivers are difficult to control by the free software community. For these reasons, compiz does not always go well together (yet) with other software that also intensively interacts with the graphical card.

As a workaround, you temporarily revert to the "traditional" window manager, metacity.

---

### Post by skywatcher on 2009-01-29
Thanks, now I understand.

Sorry to be a nuisance, but maybe you could give me some advice on scripting: is it possible to write a script that would switch to metacity, then run Celestia, then switch back to compiz when Celestia is closed?  Or is this asking too much?

---

### Post by vanadium on 2009-01-29
> Or is this asking too much?
I don't think so. It is three lines of code (actually four)

```

#!/bin/bash
metacity --replace
celestia
compiz --replace

```

You store this in a text file, for example "celest". Then store the text file in a convenient location. I use a directory "bin" in my home directory. Give the file execute permissions (right-click in nautilus, properties).

Now you can change the menu item for celestia such that it calls "celest" instead of "celestia-gnome" (you need to provide the full path: "~/bin/celest".

---

### Post by skywatcher on 2009-01-29
Works like a charm after a minor change:

```
#!/bin/bash
metacity --replace &
celestia
compiz --replace &
```

Thanks -- you're a star! (No pun :) )

---

### Post by jjpm1 on 2009-11-02
I've just installed Celestia using Synaptic (rather than the Software Centre) on 9.10 but it hasn't been added to the Applications list of programs. Is there a simple way of adding it to that list?

Cheers.

---

### Post by gesslein on 2009-11-02
> **pcit said:**
> Does anyone have the  big lag during the celestia?
My cpu time got to 100% @@
With Celestia, it is usually the system graphics drivers that are inadequate.
Without good OpenGL support like nVidia graphics cards have, Celestia hogs the CPU and runs slowly.  I am able to run it fine with the correct graphics driver and without 3D acceleration, it needs at least good DRI, I think.  Without the proper graphics driver to do the OpenGL display function in hardware, Linux steps down to doing the displaying in software, making it hog the CPU and run slowly.

Tell us the graphics card you are using, maybe someone here will be able to help you find a good driver for that.

Regards,
George Gesslein II

---

### Post by TBerk on 2009-11-14
> **jjpm1 said:**
> I've just installed Celestia using Synaptic (rather than the Software Centre) on 9.10 but it hasn't been added to the Applications list of programs. Is there a simple way of adding it to that list?

Cheers.

I did the same thing; I would suggest you also install the Celestia-Gnome front end.

Seems it now shows up under 'Education'. (Stellarium shows up under 'Science'.)


berk

---

### Post by byrong on 2009-11-30
I start up Celestia and it goes to Earth.  If I push F1-F7 it moves.  I can move with the mouse.  I can move with the arrows.  But, I don't have any menus.  I read the documentation and one area says go to "File".... and I don't have File anywhere.  All I have is a dot in the up left corner that brings up minimize, move to desktop, maximize, etc.  Any ideas?

Thank you.

---

### Post by jjpm1 on 2009-12-07
> **TBerk said:**
> I did the same thing; I would suggest you also install the Celestia-Gnome front end.

Seems it now shows up under 'Education'. (Stellarium shows up under 'Science'.)


berk

Thanks. I'll try that in the coming days but I'm ever wary of how the program seems to enjoy chewing up my comp (RAM?) with the amount of processing power it needs to run!

---

### Post by TBerk on 2009-12-14
> **jjpm1 said:**
> Thanks. I'll try that in the coming days but I'm ever wary of how the program seems to enjoy chewing up my comp (RAM?) with the amount of processing power it needs to run!

Well, I'm running 9.10 with a 3GHz, (albeit dual core) CPU but only 768M of RAM.


Santa might get me to 2G one day but I haven't been a good-boy it seems, or something.

In any case, while I run Stellarium much more I find Celestia 1.5.1  (Gnome front end) runs great on this thing.



berk

---

### Post by luotinen on 2010-11-29
> **kleeman said:**
> Got to the Add/Remove... menu item in Applications. Search for celestia. Install and profit.

I get:
W: Tiedostoa [http://fi.archive.ubuntu.com/ubuntu/pool/universe/c/celestia/celestia-common_1.5.1+dfsg1-1ubuntu1_all.deb](http://fi.archive.ubuntu.com/ubuntu/pool/universe/c/celestia/celestia-common_1.5.1+dfsg1-1ubuntu1_all.deb) ei voi noutaa
  404 Not Found

W: Tiedostoa [http://fi.archive.ubuntu.com/ubuntu/pool/universe/c/celestia/celestia-glut_1.5.1+dfsg1-1ubuntu1_amd64.deb](http://fi.archive.ubuntu.com/ubuntu/pool/universe/c/celestia/celestia-glut_1.5.1+dfsg1-1ubuntu1_amd64.deb) ei voi noutaa
  404 Not Found

(Ubuntu 8.10 Intrepid Ibex)

---

