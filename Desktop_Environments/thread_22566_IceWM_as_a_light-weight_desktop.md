---
title: "IceWM as a light-weight desktop?"
date: 2005-03-28
forum: Desktop Environments
---

### Post by Colin.A on 2005-03-28
As you all know Ubuntu uses the Gnome desktop by default.. the look and feel of it is pretty aesthetically pleasing however, machines with 128mb of RAM or less choke using Gnome (Nautilus steals a fair amount of RAM too!). IceWM is remarkably light-weight in terms of RAM usage and CPU consumption. In an environment such as the Yorktown High Computer Science Lab -- a Linux Terminal Server Project Lab, RAM/CPU conservation is a must. On a gigabit ethernet connection to 16 LTSP clients the lab feels rather responsive to all users. All of the "gruntwork" is done by the LTSP server itself (dual P4 2.4ghz, 4gb RAM) and piped over the LAN to the thin-clients. My point.. IceWM is fast and efficient. Would IceWM be a good candidate to add to Ubuntu? My thoughts are have the Ubuntu installer run a script at install-time and check the machine specifications and if deemed unworthy of Gnome, offer to install IceWM in place of Gnome as the default desktop. Suggestions/Constructive Criticism Welcome :-)

~Colin A.

---

### Post by bored2k on 2005-03-28
Rather than the whole "detect" your system-and-pick-the-Environment, I think it would be better to do a server install and install the desired Environment afterwards. The detect stuff will bring a lot of "Ubuntu detected a crappy system when I have a Killer box" kind of problems for some . Better for Ubuntu to stick with one environment, tweaked to perfection, instead of adding a bland iceWM with no real support -and no one wanting to give it- .

*drops two cents*

---

### Post by cdhotfire on 2005-03-28
dont know i think ubuntu should come with at least one other environment.  Lets say you get the ubuntu cd but you lost your internet, you install it and all you can use is gnome, how in the world will you go about install icewm.  You might say get it from a friend burn it to a cd....

well thats pretty stupid.  I agree with adding icewm as a choice, or maybe making an icebuntu?  Like ubuntu and kubuntu could both have icewm as a 2nd choice for people who think their machine isnt up for it. 

But with the whole system detection thing i must go with bored2k.  This little stunt could bring about a revolution.:-k

---

### Post by garyng on 2005-03-28
I don't think IceWM is a desktop but just a WM. For most users, a desktop nowadays contains at least the following :

web browser
file manager
printer support
some for of basic office applications

The only other two alternatives I can think of is either KDE or XFCE4. In fact, kdebase is a very good shrinked down KDE that provides basic web/file/print support and is less hungry in resources than GNOME. I use it as my default installation for server.

However, too many choice would only confuse people(KNOPPIX includes may be 5 - 6 desktop/WM but most only use the default KDE). For those want lightweight stuff, there are lots of distro for that purpose. I believe GNOME and KDE is more than enough for the target ubuntu audiences. For those who want more there is always debian sarge.

---

### Post by cdhotfire on 2005-03-28
perhaps you are right, ubuntu has gnome let the others have whats left.:razz:

---

### Post by az on 2005-03-28
As it is, it is trivial to enable universe and install icemw.  

I think that for the most part, debian will server the public as a general-purpose distro.


I however, use Ubuntu with Icewm, xfe and firefox on slow machines.

---

### Post by Colin.A on 2005-03-29
Thank you all for your responses. You all highlighted some critical points. I suppose what I would at least like to see happen is have IceWM made available on the base installation CD if possible for the low-end machines.  [-o< I'll help maintain the package if I'm not the only one that deems IceWM worthy of residing on the installation CD.

~Colin A.

edit: plus.. I will be happy to provide support for IceWM on the forums if needbe. the low-end machines that I deal with do not have a net connection unfortunately, thats why I'm lobbying for IceWM to be on the installation CD.

---

### Post by keisashankara on 2005-06-18
Excuse the newbie here. I am trying to develop a Ubuntu Light system for your low end specifications. See [http://groups.google.com.au/group/ubuntu_lite/](http://groups.google.com.au/group/ubuntu_lite/) for more details

To me the question needed to be better defined. 
Should Ubuntu Support ICEWM as a Package with Automatic customisation?
Should Ubuntu Come with Icewm as a standard package in it's standard disribution?
Should Ubuntu add Icewm, Idesk, Rox-filer, and Abiword to form a new lightweight desktop package?

To two of these questions I think the answer is YES!

Ubuntu needs a light weight package to add support for lower end systems. We have packages for Power PC's, 64 bit processors, live CD's etc. Why don't we have a package for my pentium 2 pc with 32mb of ram (yes Ubuntu would theoretically work on it, but patience makes it unusable). 

I think that Ubuntu should support a basic version that has all it's bug fixes and enhancements but one that uses lighter programs so that it runs eficently on earlier machines (they don't like being called old  ;-) ). Also since we have the concept of linux for human beings such a distro should be useable and not just a DSL where it's a competition to develop the lightest distro around. 

So I say Ubuntu should Support ICEWM and others as a part of a different version targeted for light weight machines. With a little customisation I personally think that ICEWM is the easiest Window manager for Windoze users to adjust to. This customisation should be preconfigured. Should it be chucked on the standard Ubuntu CD? only if there is room, I would like Ubuntu Lite to be installable from the i386 CD but obivously it is desirable to keep the distro to 1 cd in length. 

By the way when I say that Ubuntu should support it. I mean that it should be included with ubuntu modifications and looked after like the Kubuntu Packages are. Our developers are great people that are already overworked and I do not make more work for them. The Ubuntu Community would be responsible for finding problems and suggesting customisation's and themes. As a part of that community I am more then happy to share my efforts and to put in the work to get this going.

---

