---
title: "i need to install intel 945g graphic drivers but im new to linux"
date: 2009-02-10
forum: General Help
---

### Post by a13xgx on 2009-02-10
can anyone help me? i also want to install beryl but is seems really hard.

i own a 

gateway gt5622
3.5gb ram
1tb
1.80ghz dual core

---

### Post by photon_man62 on 2009-02-10
Go to System>Administration>Hardware Drivers and activate any driver, preferably the one flagged as "(recommended)".

Now, Beryl has been discontinued for a long time. Now we have Compiz Fusion. I'll explain that later, first let's finish this driver business.

---

### Post by a13xgx on 2009-02-10
> **photon_man62 said:**
> Go to System>Administration>Hardware Drivers and activate any driver, preferably the one flagged as "(recommended)".

Now, Beryl has been discontinued for a long time. Now we have Compiz Fusion. I'll explain that later, first let's finish this driver business.

i dont have any drivers in that section.

---

### Post by photon_man62 on 2009-02-10
OK then you need to install the official driver. Go here:

[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2947&lang=eng](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2947&lang=eng)

And select Linux. Then go and download the driver. After that, tell me the name of the driver, complete with the file extension.

---

### Post by a13xgx on 2009-02-10
IEGD_9_0_2_GOLD_1203.Exe

---

### Post by photon_man62 on 2009-02-10
Wait, what?! An .exe? Are you sure you chose Linux?

---

### Post by a13xgx on 2009-02-10
yeah i did i just double checked.

---

### Post by photon_man62 on 2009-02-10
I have just noticed that they don't release Linux drivers. Bummer. I have noticed a site that has some, though. Do you have some time now? This might take a while.

---

### Post by a13xgx on 2009-02-10
yeah i have time

---

### Post by photon_man62 on 2009-02-10
OK. Then download ALL this:

[http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.6.0.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.6.0.tar.bz2)
[http://intellinuxgraphics.org/download/2008Q4-rc4/mesa-20090115.tar.gz](http://intellinuxgraphics.org/download/2008Q4-rc4/mesa-20090115.tar.gz)
[http://intellinuxgraphics.org/download/2008Q4-rc3/drm-intel-2.6.28-20090112.tar.bz2](http://intellinuxgraphics.org/download/2008Q4-rc3/drm-intel-2.6.28-20090112.tar.bz2)
[http://intellinuxgraphics.org/download/2008Q4-rc4/2008q4-kernel-against-2.6.28.patch](http://intellinuxgraphics.org/download/2008Q4-rc4/2008q4-kernel-against-2.6.28.patch)
[http://dri.freedesktop.org/libdrm/libdrm-2.4.4.tar.bz2](http://dri.freedesktop.org/libdrm/libdrm-2.4.4.tar.bz2)

And put everything in a folder on your Desktop called... let's call it Intel.

Tell me when you're done downloading ALL that.

---

### Post by adult swim on 2009-02-10
there is an intel driver in the repos
you should be able to run this from a terminal
```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by 3rdalbum on 2009-02-10
Drivers for Intel graphics should be built-in. If you run this command:

```
glxinfo | grep "rendering"
```

what comes back? (that's a vertical line, not an l or a 1).

What happens if you go to Appearance > Visual Effects and just click "Normal"?

---

### Post by photon_man62 on 2009-02-10
> **adult swim said:**
> there is an intel driver in the repos
you should be able to run this from a terminal
```
sudo apt-get install xserver-xorg-video-intel
```

Thanks for pointing that out. The site said something about distro-specific precompiled drivers, but I couldn't find instructions for Ubuntu :D

So, OP, you have the choice of either this (simple process, but old drivers) or the source way (bit more complicated, but newest drivers). Your call.

---

### Post by photon_man62 on 2009-02-10
Are you even there? Answer us!

---

### Post by photon_man62 on 2009-02-10
All right, well, when you wake up, open a terminal (Applications>Accessories>Terminal) and type in
```
sudo apt-get install xserver-xorg-video-intel
```
After that, restart your computer, open up a terminal and type in:
```
sudo apt-get install compiz compizconfig-settings-manager
```
Restart your computer again. Now go to System>Preferences>CompizConfig Settings Manager and set up the effects you want. After that, close the settings manager, press Alt+F2 and type in compiz --replace. Now you have your effects. Enjoy!

---

### Post by a13xgx on 2009-02-10
> **photon_man62 said:**
> OK. Then download ALL this:

[http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.6.0.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.6.0.tar.bz2)
[http://intellinuxgraphics.org/download/2008Q4-rc4/mesa-20090115.tar.gz](http://intellinuxgraphics.org/download/2008Q4-rc4/mesa-20090115.tar.gz)
[http://intellinuxgraphics.org/download/2008Q4-rc3/drm-intel-2.6.28-20090112.tar.bz2](http://intellinuxgraphics.org/download/2008Q4-rc3/drm-intel-2.6.28-20090112.tar.bz2)
[http://intellinuxgraphics.org/download/2008Q4-rc4/2008q4-kernel-against-2.6.28.patch](http://intellinuxgraphics.org/download/2008Q4-rc4/2008q4-kernel-against-2.6.28.patch)
[http://dri.freedesktop.org/libdrm/libdrm-2.4.4.tar.bz2](http://dri.freedesktop.org/libdrm/libdrm-2.4.4.tar.bz2)

And put everything in a folder on your Desktop called... let's call it Intel.

Tell me when you're done downloading ALL that.

i am finally done

---

### Post by a13xgx on 2009-02-10
> **3rdalbum said:**
> Drivers for Intel graphics should be built-in. If you run this command:

```
glxinfo | grep "rendering"
```

what comes back? (that's a vertical line, not an l or a 1).

What happens if you go to Appearance > Visual Effects and just click "Normal"?

direct rendering: Yes

---

### Post by photon_man62 on 2009-02-10
Done? Good. Do you want to install the driver you just downloaded (may take a while) or would you like to download a preconfigured one from the repo?

---

### Post by photon_man62 on 2009-02-10
Where are you going all the time? You were here just a while ago.

---

### Post by a13xgx on 2009-02-10
it doesnt really matter what do you think is best?

---

### Post by a13xgx on 2009-02-10
im just messing around with all ubuntu features. i really wanna to get to know it

---

### Post by photon_man62 on 2009-02-10
If it doesn't matter to you then install from the repo, you'll be sure it'll work then. Do this:

Open a terminal (Applications>Accessories>Terminal) and type in

```
sudo apt-get install xserver-xorg-video-intel
```

After that, restart your computer, open up a terminal and enter

```
sudo apt-get install compiz compizconfig-settings-manager
```

When this finishes, restart your computer again. Now go to System>Preferences>CompizConfig Settings Manager and set up the effects you want. After that, close the settings manager, press Alt+F2 and type in compiz --replace. Now you have your effects. Enjoy!

---

### Post by a13xgx on 2009-02-10
thankz for all the help.

---

### Post by photon_man62 on 2009-02-10
Does it work?

---

### Post by a13xgx on 2009-02-10
yeah i have all the effects.

---

### Post by photon_man62 on 2009-02-10
Good, so the driver is correctly installed. You can safely delete all the stuff I told you to download at the beginning. Sorry :D

---

### Post by a13xgx on 2009-02-10
its alright thankz

---

### Post by Kclements on 2009-03-21
Ok i am working on a sim issue with the video card i have in my dell

i downloaded all the packs and belive i unpacked them right ( too me 2 days just to figure that one out ) any ways is there any way you can help with rest of this walk thru .. because my issue is with the repo driver and would love to get it cleared up 

Thanks for your time

---

### Post by JPtja on 2010-06-10
Hi,
For the program GMABooster, I need the newest intel-drivers being installed, but I don't know how to do that from doze tar.bz2 files..

Can somebody post here how to install them?

Thank you,
Jacob

---

### Post by jwdv22 on 2010-07-13
> **photon_man62 said:**
> If it doesn't matter to you then install from the repo, you'll be sure it'll work then. Do this:

Open a terminal (Applications>Accessories>Terminal) and type in

```
sudo apt-get install xserver-xorg-video-intel
```

After that, restart your computer, open up a terminal and enter

```
sudo apt-get install compiz compizconfig-settings-manager
```

When this finishes, restart your computer again. Now go to System>Preferences>CompizConfig Settings Manager and set up the effects you want. After that, close the settings manager, press Alt+F2 and type in compiz --replace. Now you have your effects. Enjoy!

Hi photon_man,

I didn't want to hijack this thread but I am sort of a noob when it comes to linux. That is to say, I have been able to get apache running and vnc and other complex I.T. things, but I am having a real tough time understanding how to compile intel drivers. I have the latest ones from the repo but they are buggy, cause both CPU cores to go thru the roof, makes my laptop hot, etc... Can you finish the instructions you were going  to give to the other person? I have the Intel 915Chipset.

Or if anyone else can help it looks like 
[http://intellinuxgraphics.org/2010Q2.html](http://intellinuxgraphics.org/2010Q2.html)
Is what I want, but I have no idea where to begin with all those components and I don't want to completely hose the system now that I finally got it setup. Thanks

---

