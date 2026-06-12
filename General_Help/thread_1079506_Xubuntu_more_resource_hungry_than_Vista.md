---
title: "Xubuntu more resource hungry than Vista?"
date: 2009-02-24
forum: General Help
---

### Post by PhoHammer on 2009-02-24
The title to this thread isn't necessarily true, but I'm starting to wonder. I installed xubuntu on my laptop:

[B]CPU Type AMD Turion 64 X2 TL-60 2.0G
Screen 15.4" WXGA
Memory Size 3GB DDR2
Hard Disk 120GB
Optical Drive DVD Super Multi
Graphics Card NVIDIA GeForce 7150M
Video Memory shared memory
Communication Modem, LAN and WLAN
Wireless Atheros AR5009 802.11 a/b/g[/B]

And I have noticed that the machine runs much hotter (produces more heat) and the fan is on much more often than with Vista. I specifically chose xubuntu (of the Ubuntu variants) for its small footprint and lower requirements. Are the settings that I can change to make this beast cool down or should I look into an even lower-requirements distro?

I just thought it was odd that **xubuntu is stressing the system more than Vista**. In xubuntu, when I open 5 firefox windows it acts as the world might end and cranks up the fan to full speed. I did exactly the same thing in Vista (I'm dual-booting) and it didn't even turn the fan on. Same amount of time running before hand too. 

Any thoughts?

---

### Post by makisupa123 on 2009-02-24
Your laptop running warm =! stressing the system more than Vista

Are you using the CPU frequency scaling apps/utilities?  My guess is that Vista is throttling your CPU based on various power management schemes and xubuntu is not.  Just a guess based on the information provided...


The package is called 'cpufrequtils'. 
 
--Mak

---

### Post by PhoHammer on 2009-02-24
I will try that, I wonder if it will help battery life? I expected better battery life on xubuntu, but there has been no noticable change at all. Maybe even longer on Vista...?

---

### Post by Simian Man on 2009-02-24
Your laptop is nicer than mine and I run Fedora with Gnome and Compiz and the fans never come on.  Look into the CPU frequency scaling apps because Xubuntu should fly on that thing :).

---

### Post by PhoHammer on 2009-02-24
I installed the cpufrequtils and set it to conservative, but when I just sit here and watch my cpu usage in system monitor (running only monitor and firefox) it will use 18-25% of my CPU and randomly spike up to 75%+ for no apparent reason. It's also using 450 MB of my RAM. I thought the min. requirements for xubuntu included just 192 MB of RAM...Why is it using so much just sitting here?

---

### Post by PhoHammer on 2009-02-24
Okay I found out that the system monitor increases CPU usage due to monitoring CPU usage(graphically, I guess?). So I'm going to see how the powersaver setting treats me, but I am still perplexed by the heat and RAM usage...

---

### Post by PhoHammer on 2009-02-25
Okay, so I killed the firefox (which was using 119 MB of my RAM, opposed to Konqueror's 39 MB on the same webpage...odd) and watched the system monitor for a bit.

With "powersave" enable through cpufrequtil, my CPU usage ping-ponged back and forth between ~25% and ~75%.

Why in the world would my CPUs be going crazy when I'm not running a single program?

And now that I pay more attention to it, I have realized that my laptop becomes quite warm to the touch from just surfing the internet (one or two tabs at a time with the fox) for about 45 min.

I just expected xubuntu to run cool and quiet with 3 GB of RAM, since it is targeted towards lower-end machines...

---

### Post by ryan.nabinger on 2009-02-25
Make sure you have the latest video card drivers (may want to try Envy to install them).  Poor video drivers lead to more heat.

Have you tried using 'top' to see specifically what is consuming your cpu?

My opinion is to forget Xubuntu.  What you should do if you want a cleaner box is look into Ubuntu Server install (it will be stripped down with no graphical support at first).  Then add only what you need from there.  If you want to be more lazy then, I think that running Ubuntu Desktop with Openbox wm instead of Metacity would do that trick, more functional and possibly faster than xfce in my experience.

---

### Post by ryan.nabinger on 2009-02-25
> **PhoHammer said:**
> Okay, so I killed the firefox (which was using 119 MB of my RAM, opposed to Konqueror's 39 MB on the same webpage...odd) and watched the system monitor for a bit.


Yeah, something terrible happened to firefox over the years and it is now a huge resource hog.  Look into Opera maybe using firefox as backup.


> **PhoHammer said:**
> With "powersave" enable through cpufrequtil, my CPU usage ping-ponged back and forth between ~25% and ~75%.


Are you sure you are looking at CPU usage and not using the CPU frequency scaling monitor?  Again, try using 'top' to check it out.

---

### Post by QCompson on 2009-02-25
In my experience (admittedly I haven't tried intrepid with this), ubuntu makes my laptops run hotter than in vista/xp, and battery life is shorter.  This is true regardless of what desktop environment I use.  I don't think switching to openbox/flubox/ratpoison will change the heat/battery situation.

I thought it was fairly common knowledge that xp/vista (or at least xp) provided longer battery life compared to ubuntu.

Of course a lot of this may vary with different models and manufacturers.

---

### Post by ryan.nabinger on 2009-02-26
> **QCompson said:**
> In my experience (admittedly I haven't tried intrepid with this), ubuntu makes my laptops run hotter than in vista/xp, and battery life is shorter.  This is true regardless of what desktop environment I use.  I don't think switching to openbox/flubox/ratpoison will change the heat/battery situation.

I thought it was fairly common knowledge that xp/vista (or at least xp) provided longer battery life compared to ubuntu.

Of course a lot of this may vary with different models and manufacturers.


Agree 100% with this from a heat standpoint as it has to do with the actual linux driver support and not so much with the Desktop/Window Manager.  I don't think CPU usage and definitely not memory usage should increase between Vista and this is affected by your choice of desktop.

---

### Post by PhoHammer on 2009-02-27
I think I'm going to start with a fresh ubuntu install with intrepid (I'm using Hardy now).

I've messed around with my xubuntu install so much now there's no telling what is going on. It was my first GNU/linux experience...:P

I think a fresh install will be good and I was needing to downsize my vista partition anyways. 

I wasn't aware of the shorter battery life vs Vista/Xp though... we should get someone working on that hahaha!

Thanks for the help guys!

---

### Post by bford16 on 2009-03-01
Dunno if you are done with this thread, but I thought it might be useful to include this note:

I just discovered that the "cpufrequtils" package was not installed on my machine, despite the fact that I have an AMD Turion 64, which is definitely capable of scaling.  The machine was randomly operating either at the top speed (1.8GHz) or the lowest speed (800MHz). No doubt this accounts for some battery-life issues as well.

I have installed the package, and I am pleased to report improved performace (and a cooler machine to boot).

---

### Post by Xiong Chiamiov on 2009-03-01
> **QCompson said:**
> In my experience (admittedly I haven't tried intrepid with this), ubuntu makes my laptops run hotter than in vista/xp, and battery life is shorter.  This is true regardless of what desktop environment I use.  I don't think switching to openbox/flubox/ratpoison will change the heat/battery situation.

I thought it was fairly common knowledge that xp/vista (or at least xp) provided longer battery life compared to ubuntu.

Of course a lot of this may vary with different models and manufacturers.
My roommate gets at least double the battery life in Linux (not Ubuntu atm) than in Vista.

Linux will try to use as much of your RAM as possible, for performance reasons.  It's a good thing, not a bad thing, until you start going into swap space.

---

### Post by Vince4Amy on 2009-03-01
Ubuntu always makes my laptop run really hot. It's not a problem with Linux as other distros are fine, but as stated before in this post Ubuntu does for some reason do something CPU intensive as I do not experience heat like that with Fedora.

---

### Post by handy on 2009-03-01
I've noticed that some Xubuntu users are going for a minimal Ubuntu install & then installing Xfce.

Crunch Bang, is also a possibility for a lighter faster Ubuntu based system.

---

### Post by PhoHammer on 2009-03-01
So installed ubuntu intrepid and initial impressions are that it is running a bit cooler (haven't put it through any marathons yet).

Is there a way to make cpufrequtils go into powersave mode upon startup? It always switches back to ondemand...

> I do not experience heat like that with Fedora.

So, Fedora, huh? Maybe I will look into that...

---

### Post by PhoHammer on 2009-05-22
Not to drag this thread back from the underworld, but this is still a problem for me.

I have installed all the cpu throttling utilities that have been suggested and such with no luck.

Ubuntu 8.10- too hot to sit my laptop on my lap after 1 hour of web browsing *only* (no other apps running)
Xubuntu 8.10 and Xubuntu 9.04 have the same problem.

Should I just distro hop until I find a "cool" running OS?

---

### Post by cyberscribe on 2009-05-22
Right now my Jaunty system shows 147 named processes running in System Monitor, even though the only program that's actually currently running at the moment is Firefox.

There are so many mysterious things running and sucking up memory and CPU cycles - for example, I can see something having to do with Bluetooth support running, even though this machine doesn't have any Bluetooth capability at all.

There seems to be quite  a LOT of totally unnecessary "bloatware" in what's being installed and enabled in Jaunty by default.

---

### Post by DavidTangye on 2009-05-24
Check out [this excellent article on Distrowatch]("http://distrowatch.com/weekly.php?issue=20090504#feature"). Essentially it says that there are good alternatives to a standard Xubuntu install, including installing the command line (my usual choice) then adding minimal GUI stuff, or even using a Debian version. I have installed command-line Xubuntu and Ubuntu several times, then just added the minimal GUI packages I wanted. If you later want the full system, you just add the xubuntu-desktop (or ubuntu-desktop) meta-package and it draws in everything. However this includes a LOT of background services that chew into memory, tax the CPU, and presumably add heat to the hardware and also slow the machine down. The choices are yours, so play around and see what suits your needs.

On one machine last week, I installed Xubuntu, then minimal gui stuff. I did not even use Synaptic to add packages. I just use aptitude. It is a very nice character-based front-end to the debian package management system that Ubuntu and others all use. Its good for viewing packages adn their descriptions, and following chains of dependent packages to see what any will draw in, if installed. In the gui desktop, you just open a 'Terminal' window and run it in there.

---

### Post by 3rdalbum on 2009-05-24
You didn't answer the crucial question: What does the "top" program say is using your CPU time?

If your CPU is being used as much as you say it is, then there must be a runaway process. Maybe a search indexing program, maybe Thunar thumbnailing, maybe something else that's buggy.

Once you've run top and found the misbehaving program, you can kill it.

I'd also advise running "Powertop" - this needs to be run as root. Apply its suggestions and you should have more battery life.

Xubuntu isn't really very lightweight. The main bulk of Ubuntu is the part that sits underneath the desktop, and this doesn't change very much from Ubuntu to Kubuntu to Xubuntu.

---

### Post by PhoHammer on 2009-05-24
> **3rdalbum said:**
> You didn't answer the crucial question: What does the "top" program say is using your CPU time?

If your CPU is being used as much as you say it is, then there must be a runaway process. Maybe a search indexing program, maybe Thunar thumbnailing, maybe something else that's buggy.

Once you've run top and found the misbehaving program, you can kill it.

I'd also advise running "Powertop" - this needs to be run as root. Apply its suggestions and you should have more battery life.

Xubuntu isn't really very lightweight. The main bulk of Ubuntu is the part that sits underneath the desktop, and this doesn't change very much from Ubuntu to Kubuntu to Xubuntu.

Top 3 CPU processes:
1 Firefox
2. Xorg
3 Conky

My CPU sits 2-7% usage while reading a webpage and anywhere from 20% to 60% 
when loading a new one. There is no "runaway" process that I can see (since it idles
down to 2% or less when I don't do anything)

I am now running !# CrunchBang Linux and my laptop's bottom becomes quite hot within 1 hour of of startup, with me just browing the web. I'm even using a different 
laptop now ([_Gateway MT6729_]("http://support.gateway.com/s/Mobile/2008/OasisSR/1015095R/1015095Rsp2.shtml") <---hit the link for specs) and it gets hot just the same as 
the one in the original post.

I tried using debian, but it got quite hot as well and I got tired of hunting down nicities 
that come "stock" with ubuntu. I don't feel like this is a distro problem anymore, at least
not one that can be solved by switching to any other fully featured distro (i.e. Fedora,
openSUSE- which I tried and it ran so hot after a fresh install that I couldn't sit my 
laptop on my lap)

I wouldn't mind "slimming" down my install, but I don't see how it could help, with firefox 
(also tried opera with same result) being the main "offender". It's not like I can just
stop using a web browser... Any suggestions as to what processes I could eliminate
and still have a usable ubuntu are welcome.

It just seems to me that my laptop and processor shouldn't run this hot so quickyly 
(the cpu can 43 C within 20 minutes of startup just browsing the web and 52 C if
I run songbird).

---

### Post by raminaghrobis on 2009-06-28
Hi, about that minimal installation article, I'm kinda interested but which packages should I install for security (or are they already installed)?

(Not that I'm obsessed with safety, it's just that if there is a problem I won't know about it until I get pwnd...)

---

