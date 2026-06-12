---
title: "Easily switch between fglrx and radeon drivers"
date: 2013-11-24
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-11-24
Hey guys,
I recently purchased Painkiller Hell & Damnation from Steam, it's in BETA and I have learned that it won't even start up if I am using the fglrx drivers. The nordic forums are suggesting I use the open source radeon driver. I am not gonna just waste $19.99 and forget about playing it so I was wondering if there's an easy way to switch to the radeon driver and then back to fglrx.

I just went through hell to get the darn fglrx drivers to work with my HD5750 and am getting great performance from the driver in games like Serious Sam 3 and Bastion so I was wondering if there was some easy way to uninstall the fglrx driver, install the radeon driver, set my xorg.conf, logout and back in and it then should be using the radeon driver correct? BUT, then when I am done playing Painkiller, I would remove the redeon driver, install fglrx, correct xorg.conf, logout and back in again to again be using the fglrx drivers.

Possibly a bash script containing all this somehow?
```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
```
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
```
sudo dpkg-reconfigure xserver-xorg
```
and then since my system is 64bit BUT I run Steam which is 32bit I have a multi-architecture system so I have to also do this
```
sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
```

Im leery of even trying this because I am have a multi-arch system due to using Steam which runs in 32bit but my main OS is obviously 64bit so there's all these symlinks to various opengl drivers

---

### Post by Bashing-om on 2013-11-24
dannyboy79; Hi again !

Not at all sure about this but, If you are using "/etc/X11/Xorg.conf" files in each of the scenerios,
MAFoElffen gives some good advise about switching between custom files to suit.

It is a long thread, and I can not recall exactly where in that thread that info is located - this one is a moving target.
Is this a thought worth considering ?
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86)

like I say :
[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by dannyboy79 on 2013-11-24
i read over that thread and that was in regards to switching off the integrated graphics card built into CPU's like the newer intel chips. THis was needed because not only did they have an intel built in graphics chip, they also had a discrete card as well. SO there was some script called acpi_call (or something or other) which would shut off the integrated chip so they would only be running the discrete card which would save on battery juice obviously.

What I need is a way to easily switch drivers but it's the same hardware. Im pretty sure there is no easy way I am just trying to find out a way to do it successfully due to all these multi-arch opengl libraries and what not. Not to mention the AMD binaries .run file when used with the --uninstall does NOT properly clean up after itself I believe so it leaves the system a mess which prevents steam from being able to use OpenGL GLX context direct rendering.

---

### Post by Bashing-om on 2013-11-25
dannyboy79; I do not know for certain for sure !

But is not all we are looking at are 2 configs files for controlling which situation ? such that in rebooting there is the option which config file is to be used ?

Now mind you I have never done it .. just seems like it should be a doable thing !

Also worth a think for that config situation :
> 

/etc/X11/Xorg.conf
That is where XServer looks first for a Xorg configuration file. After i looks there, then it looks in the /usr/share/X11/xorg.conf.d directory...

XServer is just not the "basic" graphics layer... It's also how the keyboard, mouse, touchpad, gamecontroller, etc. interact in that layer... the /usr/share/X11/xorg.conf.d directory usually just contains files for those interactive pointing devices.

That directory also may contain custom files for a particular GPU, saying this is the how this GPU should be defined... But those would be files that the user defined and put in there him/herself.


I am done for the night, ..In my next session I will see if I can hunt up MAFoElffen's treatise on switching out xorg.conf files as it still sticks in my craw.

[INDENT][INDENT]ubuntu, all things are possible
[/INDENT][/INDENT]

---

### Post by dannyboy79 on 2013-11-25
i don't believe the radeon and fglrx drivers can be installed at the same time, so it's not merely a matter of changing the xorg.conf file. i don't know for sure since I am very leary about trying to install the open source radeon driver right now. I have a bunch of work to get done and don't want my computer inoperable. maybe will try soon though

---

### Post by Bashing-om on 2013-11-25
dannyboy79; Roger.

An interesting little project never the less.
I will try and keep it on my mind.

[INDENT][INDENT]still learning even after all these years
[/INDENT][/INDENT]

---

