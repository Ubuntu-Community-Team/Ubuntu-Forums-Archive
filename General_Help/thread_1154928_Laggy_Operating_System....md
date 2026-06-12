---
title: "Laggy Operating System..."
date: 2009-05-10
forum: General Help
---

### Post by FIONEX on 2009-05-10
Hello

My new installation of jaunty is acting up.  When I double click a window title bar to maximize it, there's about a 1 second lag before the window maximizes.  Also, if I have music playing and run firefox, the sound stutters while firefox is opening.  I tried upgrading to the proposed kernel, but that didn't change anything.  I'm running Ubuntu 9.04 x64 with the latest Catalyst 9.4 for my Radeon HD2600.  I've never had this happen on my previous installations such as intrepid (it's definitely not a performance issue because my system is fairly powerful).

Any ideas?

---

### Post by danwood76 on 2009-05-10
The stuttering is caused by pulseaudio.
There were lots of problems with it in the pre releases.

One thing you could try is make sure you are added to the pulse-rt group, that will then allow pulse to run with a higher priority.

And also you could edit the /etc/pulse/daemon.conf and change the fragments to 5 and the fragment size to 25 (at the bottom of the file) once you have made these changes have a quick reboot and see if anything has changed.

---

### Post by baseface on 2009-05-10
pulse audio is just one giant problem. i dont know of its possible, i dont use linux, but try to get OSS on your ubuntu.

---

### Post by danwood76 on 2009-05-10
Pulseaudio is good, its just the latest version requires some kernel modifications that the kernel team didnt want to implement so we are left with a slightly buggy implementation of pulse.
These things can be worked around though, currently I have it working very smoothly.

---

### Post by FIONEX on 2009-05-11
Ok so besides the choppy audio, what about the delay in maximizing and minimizing windows? There's a good 1 second delay after I double click before a window is maximized.  Does this have to do with Radeon HD drivers?

---

### Post by Kiliankoe on 2009-05-11
I have a very similar problem.

I just installed Jaunty with Wubi (I unfortunately have to keep Windows) on my machine and it seems to be lagging quite a bit. I have also not experienced this with previous Ubuntu installations.

However for me everything lags. Audio, Video, the mouse itself when I move it around. It's just not fun using Ubuntu like that.

---

### Post by danwood76 on 2009-05-11
Yeah it will be to do with compiz.
What graphics card do you have?

The RadeonHD drivers are a bit behind the radeon or ati open source drivers in terms of graphics acceleration.
Depending on your card I would go with either the radeon driver or fglrx.

---

### Post by Kiliankoe on 2009-05-11
I'm using a Nvidia Geforce 7600 GT. The newest drivers have also been installed in Ubuntu.

What else is there to do?

---

### Post by danwood76 on 2009-05-11
Please start a new thread and don't hijack this one.
Your problem is completely unrelated by the sounds of it.

---

### Post by BZF on 2009-05-11
[FONT=Arial][SIZE=1][COLOR=Blue]It's either your graphics, or maybe RAM. and make sure you have all the drivers and updates downloaded
[/COLOR][/SIZE][/FONT]

---

### Post by Kiliankoe on 2009-05-11
Ok I'm sorry, I thought it was somewhat related. I'll start a new thread.

---

### Post by FIONEX on 2009-05-11
Sorry for the confusion.  I'm using fglrx for a radeon HD2600XT, which is a fairly decent card.  I dont experience any choppyness when rotating the desktop cube.  Compiz is running at over 250 frames per second.  I just dont understand why when I install the fglrx drivers on Ubuntu 9.04, it starts lagging when I maximize or minimize windows.  It's just happening on my desktop, but my laptop which has a radeon hd3200 is fine.

---

### Post by FIONEX on 2009-05-12
For the sake of the people running into this very problem, there's a very simple solution.  it turned out that the ubuntu team removed a patch from xorg because the crappy intel cards were having problems as a result.  Anyways, the patch basically disables "backfill" in xorg.

```

1. Open synaptic
2. Menu: Settings -> Repositories
3. Click the tab: Third Party Software
4. Click the button "Add" then enter "deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
5. Click the button "Add" again then enter "deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
6. Click "Close"
7. Click "Reload"
8. Click "Mark All Upgrades"
9. Click "Apply"
10. Logout and log back in.

```

---

### Post by Vipersfate on 2009-05-13
> **FIONEX said:**
> For the sake of the people running into this very problem, there's a very simple solution.  it turned out that the ubuntu team removed a patch from xorg because the crappy intel cards were having problems as a result.  Anyways, the patch basically disables "backfill" in xorg.

```

1. Open synaptic
2. Menu: Settings -> Repositories
3. Click the tab: Third Party Software
4. Click the button "Add" then enter "deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
5. Click the button "Add" again then enter "deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
6. Click "Close"
7. Click "Reload"
8. Click "Mark All Upgrades"
9. Click "Apply"
10. Logout and log back in.

```

This worked perfectly for my system! It was a bit laggy with minimization and unmaximization, this fixed that problem. Thanks!

---

### Post by petrus4 on 2009-05-13
> **FIONEX said:**
> Hello

My new installation of jaunty is acting up.  When I double click a window title bar to maximize it, there's about a 1 second lag before the window maximizes.

I'd possibly try and find out what running services you've got, and remove any which you don't need for your specific system.  Ubuntu defaults with bluetooth, cups, and a couple of other things which not everybody needs.

Another thing you might want to consider doing is installing a marginally less bloated window manager than GNOME.  Crunchbang Linux is Ubuntu based, but it uses OpenBox, a window environment which is lighter in terms of system resources.

---

### Post by FIONEX on 2009-05-15
> **petrus4 said:**
> I'd possibly try and find out what running services you've got, and remove any which you don't need for your specific system.  Ubuntu defaults with bluetooth, cups, and a couple of other things which not everybody needs.

Another thing you might want to consider doing is installing a marginally less bloated window manager than GNOME.  Crunchbang Linux is Ubuntu based, but it uses OpenBox, a window environment which is lighter in terms of system resources.

Thanks for the suggestion man, but my post above shows the solution to the lagging video problem (Vipersfate verified my solution on his system as well).  The first thing I did was remove services, but that didn't fix anything.  Then I asked my self "what am I doing?  I'm running a dual core 2.4 GHz with 4 Gb ram @ 1066 MHz with CAS 5.  I got enough speed to blow ubuntu out of the water."

---

### Post by gumblina on 2009-05-16
> **FIONEX said:**
> For the sake of the people running into this very problem, there's a very simple solution.  it turned out that the ubuntu team removed a patch from xorg because the crappy intel cards were having problems as a result.  Anyways, the patch basically disables "backfill" in xorg.

```

1. Open synaptic
2. Menu: Settings -> Repositories
3. Click the tab: Third Party Software
4. Click the button "Add" then enter "deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
5. Click the button "Add" again then enter "deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
6. Click "Close"
7. Click "Reload"
8. Click "Mark All Upgrades"
9. Click "Apply"
10. Logout and log back in.

```

thank you! i had this same problem, videos wouldn't play properly and when i put firefox on fullscreen it went all flickery (i've got a netbook, so i need to use as much screenspace as possible). i did what you advised and everything seems to be running much better. i just watched a youtube vid on full screen and it worked fine :KS

---

### Post by Buttons840 on 2009-05-29
> **FIONEX said:**
> For the sake of the people running into this very problem, there's a very simple solution.  it turned out that the ubuntu team removed a patch from xorg because the crappy intel cards were having problems as a result.  Anyways, the patch basically disables "backfill" in xorg.

```

1. Open synaptic
2. Menu: Settings -> Repositories
3. Click the tab: Third Party Software
4. Click the button "Add" then enter "deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
5. Click the button "Add" again then enter "deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main", then click ok
6. Click "Close"
7. Click "Reload"
8. Click "Mark All Upgrades"
9. Click "Apply"
10. Logout and log back in.

```

Another thanks.  I intend to submit this workaround (I don't consider it a solution) to the bug report tracking this issue.  
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)

---

### Post by sam-c on 2009-05-29
> **FIONEX said:**
> Hello

My new installation of jaunty is acting up.  When I double click a window title bar to maximize it, there's about a 1 second lag before the window maximizes.  Also, if I have music playing and run firefox, the sound stutters while firefox is opening.  I tried upgrading to the proposed kernel, but that didn't change anything.  I'm running Ubuntu 9.04 x64 with the latest Catalyst 9.4 for my Radeon HD2600.  I've never had this happen on my previous installations such as intrepid (it's definitely not a performance issue because my system is fairly powerful).

Any ideas?
I have similar[COLOR="Blue"][SIZE="3"] jaunty[/SIZE][/COLOR] problems and I am not sure if it is a Firefox 3.0.10 is to blame,**[SIZE="4"][COLOR="Blue"] Firefox freezes[/COLOR][/SIZE]**, The URL address does not show on the Toolbars,
I am not sure if it is a Ubuntu or Firefox Problem??
Thanks
Sam

---

