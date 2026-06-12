---
title: "Looking Glass in Feisty"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by 213374U on 2007-06-18
I just installed Looking Glass and WOW!!! This is an amazing piece of programming. Definitely a memory hog though. Would like to see what someone with more than 512mb of ram gets out of it though. Just want to see a few opinions on it.

[https://lg3d-core.dev.java.net/](https://lg3d-core.dev.java.net/)

---

### Post by gvoima on 2007-06-18
Just did a download, gonna test it after work today.
Looks nice though :)
But what about the usability?


[EDIT]
Ok, had the time to test it. Looks nice, but it's quite a mess :)
[/EDIT]

---

### Post by brim4brim on 2007-06-18
I don't think Looking Glass will be useful for anything but ideas for other projects.

I quite like the notes on back of Windows idea.  Other than that, it is mostly stuff that gets in the way, more than it helps.

---

### Post by 213374U on 2007-06-18
My thoughts exactly, but I wasn't sure if it was the design of the program or my lack of RAM. Awesome eye candy, wish Compiz could incorporate just a few of the looking glass ideas (i.e.- notes on the back of windows and window view in the bottow task bar)

---

### Post by Motoxrdude on 2007-06-18
Downloading it now.
EDIT: Doesn't work for me.

---

### Post by andrewsomething on 2007-06-18
There's definitely some interesting potential there, but as of now it's basically unusable.

---

### Post by pardesi on 2007-06-18
well i am downloading it so that i can run it on a live cd can people for whom it is working:) tell me is it easy or as complicated as my beryl installation on ATI card...and those it didn't work what was your problem...:(

---

### Post by 213374U on 2007-06-18
There were only a few problems with the install as far as file paths listed in the install instructions. Not to hard to work around them. As for the program though, as it's been said before, it's mostly just a bunch of useless eye candy (especially with 512mb RAM :P )

---

### Post by pardesi on 2007-06-18
did u have any problems running in live CD
what's ur graphics card mine is ATI 200X series
1GB RAM
is it ok to run...or i have to do something

---

### Post by andrewsomething on 2007-06-18
I haven't tried it from a LiveCD, but my advise would be to follow the same steps for setting up your graphics drivers as you did for Beryl. With Beryl already working I was able to simplely install through Synaptic, and it worked. 

You have to log into a new session inorder to use it.

Here are the instructions from [Project Looking Glass](https://lg3d.dev.java.net/lg3d-getting-started.html).

```
 Install using apt or the Synaptic Package Manager (on Ubuntu) by doing the following (you will need root permissions to do this, so sudo bash first) :

    * There are 3 LG3D repositories. The stable repository has the latest stable releases (0.8.1, 1.0 etc.). The testing repository has the pre-release builds (alpha, beta etc.) for the latest version and the unstable repsoitory has the nightly builds. To access these repositories, add the following lines to /etc/apt/sources.list and then comment/uncomment the appropriate line(s).

        	## LG3D repsoitories
        	deb http://javadesktop.org/lg3d/debian stable contrib
        	# deb http://javadesktop.org/lg3d/debian testing contrib
        	# deb http://javadesktop.org/lg3d/debian unstable contrib
              

    * Then you can

                % apt-get update
        	  % apt-get install lg3d-core
              

      OR, on Ubuntu systems,
          o run the Synaptic Package Manager from the System/Administration menu,
          o click on the Reload button and then
          o Search for lg3d and mark the lg3d-core package for installation.
          o click on the Apply button to download and install


Choosing lg3d-core for installation should automatically choose/mark lg3d-jdk and lg3d-java3d for installation. You will need to accept the 3 licenses for lg3d, jdk and java3d to complete the installation.
```

Here are the system requirements:
```

CPU 	1.4 GHz or faster recommended
RAM 	512MB recommended
Graphics Card 	

3D accelerated graphics card, with at least 32MB VRAM and driver support for OpenGL, version 1.3 or greater (LG3D may run with OpenGL 1.2, but 1.3 is highly recommended). 24bit display depth is required in order for the X11 integration work correctly.

```

---

### Post by 213374U on 2007-06-18
I have an ATI Radeon X1600 Pro and had absolutely no problems running the live cd. It actually ran better than the installed version :P

---

### Post by digital_exhaust on 2007-06-18
> **andrewsomething said:**
> With Beryl already working I was able to simplely install through Synaptic, and it worked. 

I can't find it in Synaptic....looked several times and it's not there.....at least for me it's not. Any advice??

---

### Post by andrewsomething on 2007-06-19
> **digital_exhaust said:**
> I can't find it in Synaptic....looked several times and it's not there.....at least for me it's not. Any advice??

Type "sudo gedit /etc/apt/sources.list" in the terminal. Then add these lines to the to the file.

```

## LG3D repsoitories
deb http://javadesktop.org/lg3d/debian stable contrib
# deb http://javadesktop.org/lg3d/debian testing contrib
# deb http://javadesktop.org/lg3d/debian unstable contrib
```

Save, then enter: "apt-get update"

After that, you should be able to get it from Synaptic or by running "sudo apt-get install lg3d-core"

---

### Post by digital_exhaust on 2007-06-19
Thank you... that did it.

Thanks again!

---

### Post by rfurman24 on 2007-06-20
I have it running on my machine from inside beryl. It is very memory intensive. I think at this point it is worthless other than may some ideas to build on. My machine is a 2.4 p4 with bfg6600gt oc with 1.5gb ram. I also can get it and metisse to run inside beryl at the same time on opposite sides of the cube.

---

### Post by Fireblend on 2007-06-20
Wait, there's a liveCD that includes this? I wanted to install it to try it out, but if there's some way to just check it out, sign me up. Link?

---

### Post by jgcamp99 on 2007-06-20
> **brim4brim said:**
> I don't think Looking Glass will be useful for anything but ideas for other projects.

I quite like the notes on back of Windows idea.  Other than that, it is mostly stuff that gets in the way, more than it helps.

Apple OS X Leopard has already borrowed the idea of the reflective panel for Leopard (see Apple's video on "spaces" at their website) from PLG. I don't know what the memory overhead is for that in Leopard, but in "PLG", it's appears to be very MS Vista bloated.

---

