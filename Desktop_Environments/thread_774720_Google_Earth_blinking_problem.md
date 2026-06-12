---
title: "Google Earth blinking problem"
date: 2008-04-29
forum: Desktop Environments
---

### Post by jurco on 2008-04-29
Hi, I installed GoogleEarth. When I run it, I can see the earth - the whole canvas blinking. Like refreshing. I had my closed ATI drivers, so I installed ENVY to solve this. But its blinking even with ENVY. Does anybody have similar issue? Thanks

---

### Post by ColJep on 2008-05-19
I am having the same problem. It seems like dialog boxes are fighting to be the active one. I am going to investigate along those lines. It is certainly ATI related. I had GoogleEarth working with this computer under 7.06, now using 8.04. (Automatix broke my upgrade to 7.10. Now using clean install 8.04)

---

### Post by GrandpaLeaman on 2008-05-19
I don't think it's an ATI problem. I have a Dell E1505/6400 with a Intel Corporation Mobile 945GM chipset and I have the same problem. It seems that GoogleEarth doesn't play well with desktop effects. See this link: [http://ubuntuforums.org/showthread.php?t=505068](http://ubuntuforums.org/showthread.php?t=505068).

Well, just found out ATI and Intel drivers both have this problem. See this link: [http://forum.compiz-fusion.org/showthread.php?t=3367](http://forum.compiz-fusion.org/showthread.php?t=3367).

I'll try disabling Compiz and see if that solves the problem.

---

### Post by GrandpaLeaman on 2008-05-20
Yep, that seems to be the cure. If I stop compositing it definitely solves my blinking problems with GoogleEarth. Since I have Compiz Fusion Icon installed, all I need to do is change the window manager to Metacity, and then back to Compiz once I'm done.

---

### Post by John The Bad on 2008-05-20
Hi.  I'm a total Ubuntu newbie but so far I'm having a blast.

In relation to Google Earth blinking, I'm having that problem too.  However, I'm pretty sure I don't have Compiz running on my machine.  How do I check if Compiz is installed or not?

---

### Post by GrandpaLeaman on 2008-05-22
> **John The Bad said:**
> Hi.  I'm a total Ubuntu newbie but so far I'm having a blast.

In relation to Google Earth blinking, I'm having that problem too.  However, I'm pretty sure I don't have Compiz running on my machine.  How do I check if Compiz is installed or not?

Here is the best way you can check to see if you're running Compiz, and also how to disable compositing. Go to your menu and select System --> Preferences --> Appearance. Then select the Visual Affects tab. If anything is selected other than "None", then you are probably running Compiz. To disable compositing, select "None". If it is already selected, then the problem may be that you don't have enough system resources to properly run GoogleEarth. Of course, this is just speculation on my part as I don't have any information about your system.

I hope this helps!

By the way, I've been running Ubuntu for about 9 months and this is the most fun I've had with an operating system since Windows 98. As you are, I also am having a blast!

---

### Post by Diego_R on 2008-06-01
Hi all,

when launching GoogleEarth 4.3.7204.0836 (beta) in Ubuntu 8.04 the default settings have "Atmospheric" layer on (in 'View'), resulting in a "graying-out" of parts of the window at every mouse-click anywhere. After unchecking "Atmospheric" layer the GUI behaves almost normal, although there is a short blinking left

When clicking and holding mouse button the Earth disappears, so i guess its a problem with the mouse, not the video card

cheers

---

### Post by BUSHYBOB on 2008-06-01
I have this problem with google earth and vlc and it's definately a compiz related problem. It doesn't happen with compiz disabled. I've also discovered that when running either in full screen mode the problem disappears.

---

### Post by Dorotheos on 2009-04-04
I have the new intrepid install. And have disabled compiz, yet still have the blinking screen! What am i mising guys, i do have an ATI Mobility Radeon card, is that it??

---

### Post by waster on 2009-04-05
It appears that opengl applications don't work well with DRI (direct rendering infrastructure v1) - this is quite a major hurdle, apparently, and requires reworking all the drivers to use DRI2. I understand that Intel driver do this, but only for a more recent kernel than will be in jaunty.

Conclusions:
1) for the time being, Intel has the best open source graphics driver supprt. Buy intel graphics, for now.
2) ubuntu will have this problem until the next release.
3) try a really recent alpha fedora live cd/dvd, which has a 2.6.29 kernel and bleeding edge drivers.
4) the compiz/metacity switcher applet is the best workaround.

---

### Post by BrMBr on 2009-07-13
The topic is kinda old, but I'll post a solution here anyway, as some users could still have this issue.

This solution is **ONLY** tested with **INTEL** graphic cards, but might work with other vendors too, but ATI. If you have an ATI card you can pray, as their drives are crap.

First, we will update graphics card drivers. These drivers are not fully tested and might  break your system, so _use at your own risk_.

1) Go to System > Administration > Software Sources, click on the second tab and add:

```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main

```2) Add the key: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4F191A5A8844C542](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4F191A5A8844C542)

3) Go to System > Administration > Synaptic Package Manager and click "Reload".

4) After reloading, click "Mark All Upgrades" button.

4) Click apply and install the new drivers.

5) Restart.

More info can be found [here]("http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html").

For _**INTEL**_ only:

After restarting, everything should be working, but it would be nice to add this:

```
$ sudo gedit /etc/X11/xorg.conf
```and make Section Monitor part look exactly like this:

```
Section "Monitor" 
 Identifier "Configured Monitor" 
 Option "AccelMethod" "UXA" 
EndSection
```It worked here and with many friends.

---

### Post by sroland81 on 2009-08-31
I have an HP 6735s with ATI Radeon HD3200 and Google Earth flickers all the time... the issue is compositing because both Metacity (with compositing extension enabled) and Compiz make the earth window to flicker all the time... switching to metacity with NO composite extension it fix the issue... refresh rate? i remember in a previous GE installation in the same machine didn't have this issue... just this time... any ideas? ATI Radeon drivers were installed from ATI binary installer both times...

regards,

Santiago.

---

