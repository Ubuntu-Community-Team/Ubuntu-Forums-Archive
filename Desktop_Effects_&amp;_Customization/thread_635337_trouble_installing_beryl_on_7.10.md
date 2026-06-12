---
title: "trouble installing beryl on 7.10"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by ride1226 on 2007-12-08
Hello all. First I would like to say I'm sorry if I have overlooked the solution to this elsewhere. I am tryin to install Beryl on my new 7.10 laptop and am running into trying to follow this simple install tutorial but am only getting the first two lines of code to work.

[http://forum.beryl-project.org/viewtopic.php?f=36&t=4781&st=0&sk=t&sd=a](http://forum.beryl-project.org/viewtopic.php?f=36&t=4781&st=0&sk=t&sd=a)

Here is what I have in my terminal.

milby@milby-laptop:~$ sudo -i
[sudo] password for milby:
root@milby-laptop:~# cd /usr/local/bin
root@milby-laptop:/usr/local/bin# wget [http://distfiles.gentoo-xeffects.org/beryl-setup](http://distfiles.gentoo-xeffects.org/beryl-setup)
--13:29:41--  [http://distfiles.gentoo-xeffects.org/beryl-setup](http://distfiles.gentoo-xeffects.org/beryl-setup)
           => `beryl-setup.1'
Resolving distfiles.gentoo-xeffects.org... 69.73.191.2
Connecting to distfiles.gentoo-xeffects.org|69.73.191.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22,238 (22K) [text/plain]

100%[====================================>] 22,238        40.00K/s             

13:29:48 (39.87 KB/s) - `beryl-setup.1' saved [22238/22238]

root@milby-laptop:/usr/local/bin# chmod 755 beryl-setup
root@milby-laptop:/usr/local/bin# chmod 755 beryl-setup.1
root@milby-laptop:/usr/local/bin# 
root@milby-laptop:/usr/local/bin# 
rec

Simply put I am stuck. Any help greatly appreciated. Thanks!

---

### Post by kodoku on 2007-12-08
why do you want beryl?  Gutsy already has compiz-fusion, which is an updated and refined beryl+compiz.  

Go to System -> Preferences -> Desktop Effects to enable it.

---

### Post by ride1226 on 2007-12-08
> **kodoku said:**
> why do you want beryl?  Gutsy already has compiz-fusion, which is an updated and refined beryl+compiz.  

Go to System -> Preferences -> Desktop Effects to enable it.

I go to System > Preferences > but there is no desktop effects there. 

Wonder why?

---

### Post by kodoku on 2007-12-08
> **ride1226 said:**
> I go to System > Preferences > but there is no desktop effects there. 

Wonder why?

yeah scratch that.. I think it was there for feisty.  Try going to a terminal and typing > compiz --replace

If compiz is installed correctly and your video card is running on appropriate drivers, it should work.  What kind of video card are you using?

---

### Post by ride1226 on 2007-12-08
i typed that into terminal and here is wat i got back

milby@milby-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '1002:5955' found 
aborting and using fallback: /usr/bin/metacity 

thank you for helping...not sure wat that means but im still trying

my computer is a compaq presario v5000 laptop so watever is integrated is the graphics card.

---

### Post by ride1226 on 2007-12-08
i just installed two packages tryin to figure things out. The first package gave me System> Preferences> Compiz Settings Manager and the other gave me System>Preferenced> CompizConfig Settings Manager. When I go into Compiz Settings Manager it loads but gives me the following readout " DBUS FAILED TO LOAD Compiz is not running. The dbus pluggin cannot be activated unless compiz is running" I guess that obviousley means compiz isnt installed and running therefore thats why i cant mess with its settings. That seems obvious to me but I am a newby. The second program that is Compizconfig settings manager will not load at all. I click and nothing happens. Any more help thanks!

---

### Post by Ub1476 on 2007-12-08
In Gutsy do this:

```
suo apt-get install compizconfig-settings-manager
```

Open System>Preferences>Appearance>Visual Effects>Select normal/extra/custom.

If it says "visual effects could not be enabled" post the outpout of:

```
lspci | grep VGA
```

---

### Post by ride1226 on 2007-12-08
So it did as you expected and said "Desktop effects could not be enabled."

The output from your code gave me the following...

milby@milby-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
milby@milby-laptop:~$ 

thank you again and again for the help. Hopefully we can get this working.

---

### Post by fmartinez on 2007-12-08
to compiz in Ubuntu Gusty......
For Gusty... 1. enable the restricted drivers in System>Admin>Restricted drivers
2. install xserver-xorg  sudo apt-get install xserver-xgl
3. restart for changes to take effect
4. I used the process on [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) to install compiz, and it works great... no issues... this has worked on every gusyt install I have....

---

### Post by Ub1476 on 2007-12-08
Wow, you're the third I have stepped into today with an ATI Xpress 200:lolflag:

Anyway, look [here]("http://www.ubuntu1501.com/2007/11/compiz-fusion-with-xgl-in-gutsy.html").

---

### Post by ride1226 on 2007-12-08
that link got it installed and now i can go into the system > preferences > compiz settings manager however i dont know if there is a certain way you have to turn it on for all the things to begin to work or what because nothing has changed. also after putting visual effects to custom when i click preferences nothing comes up.

---

### Post by ride1226 on 2007-12-08
i typed in compiz --replace into the terminal and got the following

milby@milby-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

all of my windows begin to change and then nothing happens and my top bar on apps dissapears (the bar to close and minimize and whatnot) so i typed it again and now they are back but when i close terminal they dissapear again.Not too sure what is going on here.

---

### Post by Ub1476 on 2007-12-08
Press alt+f2 and write compiz --replace in there.

To use the Advanced Desktop Effects, set it to custom in "Visual Effects" tab. Edit your preferences in System>Preferences>Advanced Desktop Effects.

---

### Post by macaholic on 2007-12-08
What is your output of```
dpkg -l | grep xserver-xgl

``` and ```
fglrxinfo
```?

---

### Post by ride1226 on 2007-12-09
here you go macaholic

milby@milby-laptop:~$ dpkg -l | grep xserver-xgl
ii  xserver-xgl                                1:1.1.99.1~git20070727-0ubuntu3 GL-based X server
milby@milby-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

---

### Post by Ub1476 on 2007-12-09
First set Visual Effects to normal. If it works (Windows fade away when you close them etc), set it to custom, like I said above.

---

### Post by ride1226 on 2007-12-09
i dont really see any difference at all. the windows dont fade they just go away as normal it seems. im not too sure wats going on.

---

