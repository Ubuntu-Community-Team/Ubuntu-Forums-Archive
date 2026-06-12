---
title: "[SOLVED] NVIDIA 177.83 drivers for Hardy Heron"
date: 2009-01-01
forum: Desktop Environments
---

### Post by Indubitableness on 2009-01-01
Okay, this has been driving me insane, and I'm not the only one. I've seen several threads about this, none of which help except to show me that I'm not the only one with this problem.

  I don't know quite which forum this particular complain belongs in, but after much frustrating work, I've finally decided to post.

  Ibex allows you to install the newest Nvidia drivers using the usual method (i.e. System->Administration->Hardware Drivers). My particular system has an NVidia Geforce 6150SE nForce 430 integrated graphics card, which means i'm trying to use the latest driver (177.83) for the GeForce 6 series. Of course, i'm not using Ibex, and i didn't like it when i did use it.

  The point is this, when I use the self extracting installer file (in tty1, after stopping x server) followed by the nvidia-xconfig configuration tool I am able to restart X server (sudo /etc/init.d/gdm restart) and use the latest driver. This particular driver messes up Gnome's windows (the little bar at the top of each window tries to disappear, which is annoying) but it improves video playback immensely (i no longer have to disable compiz-cube when i want to watch videos) This trade off is more than worth it to me.

  The problem that I and everyone else who's ever used the internet (overstatement) seems to be having is that after a restart the system forgets how to use the new drivers. It tries to start gdm, crashes three times, and starts in Low Graphics Mode. You get the option to configure your graphics card here, but it doesn't do anything.

 I've tried all sorts of stuff mentioned in the official Readme here  [http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/index.html) 
none of it helped.

  I have a feeling this has something to do with the kernel modules generated during the install, and that something needs to be done to make sure the system loads the proper kernel modules during boot, but i'm not experienced enough to know how to do this correctly. The readme file posted above mentions how to make sure the correct .so files are used, and i tinkered with them a little bit, but most of it's honestly above my head, and of course the authors of the documentation seem to assume we're all experts. I'm good with computers, but it'll be some years before i can claim to be an expert. I think that's probably true for most of us on these forums.

  Speaking of forums I've also tried several things mentioned in forums, but most of the solutions discussed involve older Drivers or older distros of Ubuntu. Some of them seem to just not apply here, and no matter what i do in xorg.conf it changes nothing (i'm still able to use the new driver each time i reinstall it, but ONLY when i go out of my way to reinstall it.)

  If anyone has enough experience to troubleshoot this, or perhaps if there's a way to obtain this particular driver from the repository (it seems like there MUST be, if they provide it for 8.10) please post here.

  If I've posted this in the wrong section (i didn't see any specific sections for drivers) let me know and i'll move it or something.

  Thanks for your time guys, although I half expect no one will really have a solution (no one online ever seems to have a solution unless it's for problems i don't need solved.)

  I'm off to write to the NVidia guys now.

---

### Post by Sin@Sin-Sacrifice on 2009-01-01
I also have the 6150 chipset and had the same problem... just go to system>admin>software sources>update and activate the "hardy proposed" repositories and sudo apt-get update. Ubuntu is "not supporting OLDER cards" anymore but someone was inspired to support ours and added the drivers there. I didn't think these were older (mine PC only being less than 2 years old) but I guess someone is trying to push sales for nvidia.

---

### Post by Indubitableness on 2009-01-11
Hey thanks Sin@Sin I know it's been a while, and you even messeged me personally to let me know, but i've been physically taking apart and rearranging this computer (into a new case).

    Anyway, this seemed to do the trick for a second there, but i'm still running under 162.12 as the graphics driver. NVIDIA has already release 180.something and i'm still trying to install 177.83.

    Thanks anyway man, i've pretty much given up hope on getting these drivers installed on any linux system. 

    Here's a list of distros i've tried for the sole purpose of installing this set of drivers.

    Gentoo 2008.0
    Slackware 12
    Debian 4.0
    OpenSuSE 11.0
    PClinuxOS 2007
    Fedora Core 9
    Arch Linux 2008.06

    The only problem with a couple of these is the fact that they did not come with the source specific to the kernel i end up installing, and thus would require me obtain and compile my own kernel simply in order to compile the kernel module required by NVIDIA's installer.

     This is a bit too much since all i'm trying to do is test which OSes are ready to handle a manual install of Nvidia drivers.

    With gentoo, i didn't even end up trying to do a manual install since the emerged graphics drivers were more than adequate, but i forgot to configure my kernel with the correct sound support, so i ended up scratching that install.

    I'm beginning to suspect that NVIDIA needs to take their thumb out of their asses and provide some ubuntu specific install instructions, because i KNOW the installer works, it's making ubuntu use the installed driver at each boot up that's the problem.

   It's simple to make ubuntu use the driver when it's first installed (or reinstalled) but if you turn off your machine afterwards expect to see low graphics mode.

---

### Post by Indubitableness on 2009-01-11
Solved it... SORT OF

  Ubuntu provides the .DEB packages to install these drivers at the mirror lists:

[http://packages.ubuntu.com/intrepid/i386/nvidia-177-kernel-source/download](http://packages.ubuntu.com/intrepid/i386/nvidia-177-kernel-source/download)   
<-- Necessary kernel module

[http://packages.ubuntu.com/intrepid/i386/nvidia-glx-177/download](http://packages.ubuntu.com/intrepid/i386/nvidia-glx-177/download)
<-- The actual driver

  Now, the ubuntu pages seem to make it clear that they will not add this driver, and probably not any others into Hardy (as you can see these links are both intended to used with intrepid.)

 I don't understand this seeing as how Hardy Heron is the Long Term Support version. Intrepid always assumes that i have a bunch of USB devices connected just because i have the ports for them, then clutters my screen with them anytime i'm working in my home directory, so i'm sticking to hardy until a new LTS version is released.

 Now that i have the drivers working, i would like to say GOD DAMN IT THAT WAS ******' DIFFICULT!

 I understand why these drivers aren't support, at least i think i do, assuming that the problem the driver has displaying the window border's properly on any given window is just ONE problem the driver has, i get it. But the currently supported 162.12 driver simply can not handle compiz cube with rotation at the same time you're trying to play flash videos or even DVD's, and it drastically reduces frame rates, whereas this particular driver seems to have no problem with that.

  Anyway, i hope this thread actually helps someone.

---

