---
title: "Gnome vs XFCE for these needs"
date: 2009-03-06
forum: Desktop Environments
---

### Post by sippyCUP on 2009-03-06
I am going to reinstall Ubuntu tomorrow on the following laptop:

HP DV400
Pentium M 1.73
1 gb ram (soon to be 2gb)
160 gig 5400rpm HD

I am attracted to Xubuntu based on potential speed improvements, especially considering I am about to start dabbling in virtualization. It's my impressive that the main differences in Linux between the different desktop environments is just the UI and the default application set, so that doing things like installing programs will be seamless on Gnome, KDE, XFCE, etc, with maybe different libraries required depending on the desktop. Is this correct, and should I expect any particular difficulties in migrating from gnome to XFCE?

Thanks for your advice,
Eric

---

### Post by slumbergod on 2009-03-06
Xubuntu's Xfce environment is definitely faster, with a focus on fast functionality rather than resource-intense eye-candy. It uses the same Ubuntu repositories so you have access to everything you can install on Ubuntu. You'll notice that Xubuntu has a differing set of applications included when you install it, but, again, it is as simple as firing up synaptic and adding whatever you need.

Xfce4.6 has just been released but it won't be included in Xubuntu until the next release in a couple of months.

My advice would be to install Ubuntu 8.10 then grab the two graphical installers from the Xfce website (one for Xfce4.6 and one for the Goodies). The installers will tell you what libraries you need to get via Synaptic before you can complete the installation of Xfce4.6 (mostly a pile of development libraries).

The advantage of doing it this way is that you will get Ubuntu to fall back on if you have problems with installing Xfce4.6, and, of course, the latest Xfce which is very good indeed. You simply choose the environment you want to boot into at the login screen. Also, doing it this way means you get the default Ubuntu application set - all that changes in the environment you use.

You could get Xubuntu 8.10 which uses Xfce4.4 but 4.6 really improves on it. Installing 4.6 alongside 4.4 via the graphical installer has caused some people some issues. So it is better to set it up as outlined above.

Hope that helps

---

### Post by sippyCUP on 2009-03-07
Actually that sounds like it will save me many moments of headache and agony :D . Thanks very much for the advice!

---

### Post by slumbergod on 2009-03-07
You're welcome. If you get stuck or have questions, just post back on this thread and I might be able to help you.

---

### Post by jjpcexpert on 2009-03-08
Man: You want to combine Metacity with Vista Basic theme (I am no fanboy of either OS LM or Win), Compiz, and Xfce. Also extract the aero-clone theme into /usr/share/themes:
```
gksu thunar /usr/share/themes
```
Attached is the Aero Clone theme and the Vista Basic themes: extract them to your /usr/share/themes directory and run <<sudo apt-get install gnome-control-center>> it will pull the base desktop in. I will make these themes available under their own license: GPLv2. (Current GPL is v3.x)

---

### Post by tyk on 2009-03-10
Can I use the xfce 4.6 installer scripts on 8.04 Hardy?

---

### Post by jjpcexpert on 2009-03-17
Dunno. Find out if someone built a DEB of it that is on a repository.

---

### Post by cb951303 on 2009-03-17
I don't find xubuntu faster than ubuntu.
I think it's bloated for a xfce desktop. lots of gnome parts are installed etc...

You can try minimal ubuntu + xfce 4.6 from PPA though. that would be fast.

---

### Post by tyk on 2009-03-22
hmm.. i tried a virtualbox machine with 8.04 minimal and then installed xfce 4.6 
All in all, excellent I thought. had to satisfy some dependencies from 8.10 repos. Which later did conflict with some of the 8.04 thingies, i don't remember what exactly though. Not critical coz the machine is still up and about.
Mefeels intrepid minimal + xfce 4.6 will be ubercool. Will be trying that on the old laptop soon.
Cheers.

---

