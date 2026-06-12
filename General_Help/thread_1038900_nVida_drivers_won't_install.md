---
title: "nVida drivers won't install"
date: 2009-01-14
forum: General Help
---

### Post by greylander on 2009-01-14
I'm using fresh install of 64 bit Ibex, 8.10, on an HP Pavillion dv900 series laptop (dv9334us).

Can't seem to get either the open-source or proprietary nVidia drivers to come play on my machine.

If I try 

[INDENT]sudo apt-get install nvidia-glx-177[/INDENT]

I get 

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-177[/INDENT]

If I search "nvidia" in Synaptic package manager, I find packages named nvidia-177-modaliases (also 71 96 and 173), nvidia-common, and a few package with no nvidia in name.  Does not find nvidia-glx-177 or anything similar.  All these packages are already installed and up to date, whatever they are.  I do have all the repositories checked.

The nvidia-settings and nvidia-config commands are not found:

[INDENT]greylander@Wraith:~$ sudo nvidia-config
[sudo] password for greylander: 
sudo: nvidia-config: command not found
greylander@Wraith:~$ sudo nvidia-settings
sudo: nvidia-settings: command not found[/INDENT]

If I try to get the proprietary drivers with *System>Administrator>Hardware Drivers* then it lists the nividia 173 and 177 drivers.  If I click "Activate", it flashes up a download window which disappears immediately, and it still says "This driver is not activated".

I downloaded the drivers from nvidia.com and attempted to install, but it has to compile the kernel interface and bails out saying that I need a kernel without "Xen support".

So, it seems I am denied a driver for the nVida video in my laptop -- both the open source and proprietary drivers not installing.

Anyone know anything that might help?  Thanks!

---

### Post by theWrkncacnter on 2009-01-14
I don't know if this will help, but when the nvidia drivers didn't work on my machine, the problem turned out to be because I had the -proposed repositories active on my machine, which was breaking the Hardware Drivers manager thing. There's not much chance this is also your problem, but it is worth investigating.

Also seeing as you're having trouble locating some packages, maybe you should take a moment and make sure your software sources are in order. Good luck!

---

### Post by greylander on 2009-01-14
Thanks for the response!

The problem with Hardware Drivers happen immediately after installing.. so I don't see how I could have any inappropriate repositories active.

Not sure what you mean by software sources, unless that is a synonym for repository.  In the settings for Synaptic, I have the first four checked.  Not sure what else I would do to make sure my sources are in order.

---

### Post by cb34 on 2009-01-14
im sorry if this is no real help.. but you have to follow what the compiling process said.. i dont know anything about xen support... but that's where your investigations on what to do should start. follow the error messages.

and do all your sources all over again looking over everything.. even unchecking, then checking them again..
and run 
sudo aptitude update afterwards...

also.. try using aptitude instead of apt-get.. it might give you more info.

if it says package not found... you have to look into your sources.. or directly the /etc/sources.list file... make sure everything is proper in there...

---

### Post by cb34 on 2009-01-14
i just looked what is Xen... [http://wiki.xensource.com/xenwiki/XenFaq](http://wiki.xensource.com/xenwiki/XenFaq)

maybe you dont need this, and you can recompile your kernel without Xen support like it says. i have no clue really.

or

i would check on nvidia's site, maybe they have an exact fix or way to get around this.. or at least some instructions how to deal with this..

---

### Post by jocko on 2009-01-14
> **greylander said:**
> I downloaded the drivers from nvidia.com and attempted to install, but it has to compile the kernel interface and bails out saying that I [COLOR=Red]need a kernel without "Xen support"[/COLOR].

Which kernel do you use? the nvidia drivers (both the ones in the repo and the latest from nvidia.com) installs fine on the stock ubuntu kernel (the -generic flavour).
Sounds like you may have installed some other kernel flavour?

---

### Post by Ahadiel on 2009-01-14
Make sure your system is up to date
```
sudo apt-get update && sudo apt-get dist-upgrade
```
then try System => Administration => Hardware Drivers.

---

### Post by greylander on 2009-01-14
> **Ahadiel said:**
> Make sure your system is up to date
```
sudo apt-get update && sudo apt-get dist-upgrade
```
then try System => Administration => Hardware Drivers.

Solved!!  Thanks Ahadiel, and everyone else who answered.  After update/upgrade, the Hardware Drivers was able to download and install the nVidia driver no problem.  And my ultimate goal of getting external monitor to work was a snap with the System > Admin > nVidia Server Settings.

I'm new to Linux/Ubuntu -- I should have paid closer attention to install guides suggesting first thing to do after install is do the update/upgrade.

Thanks again for the help!

---

