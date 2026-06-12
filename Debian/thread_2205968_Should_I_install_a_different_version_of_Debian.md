---
title: "Should I install a different version of Debian?"
date: 2014-02-16
forum: Debian
---

### Post by Meowcenary on 2014-02-16
Aloha!
I have an old desktop that I've always enjoyed messing around with for things like installing linux and what not. I installed 64 bit Debian 7 "Wheezy" and found that it was running a bit slow. Also later when I was working on a programming project it had a lot of issues handling programs I had ran in my lab section easily. Should I consider installing an older version of Debian, a different distro, change it to 32 bit, or something else? 

Some more info:
1 Gb ram. 2x512mb
Intel Celeron D 
previously ran windows xp
originally purchased around 2006-2007

---

### Post by Meowcenary on 2014-02-16
I think I may have solved my own problem, but I wont have time to test it out until later so I'll consider this an open question still for anyone who stumbles across it. 

[http://forums.anandtech.com/showthread.php?t=2120660](http://forums.anandtech.com/showthread.php?t=2120660)

In here it is mentioned that not all Celeron D processors are 64 bit, so I think I might be having issues because of this. Regardless im going to keep looking into things.

---

### Post by Don_Stahl on 2014-02-16
What desktop? If your installation runs KDE, then you might try switching to XCFE or LXDE. I dunno about the exact stats on Wheezy, but with some distros you might free a couple of hundred MB of RAM with a LXDE. If your lab applications are mem-hungry, that might help.

---

### Post by Meowcenary on 2014-02-16
I was using GNOME Classic mostly. I used KDE for a bit and did not see much different in speed quality between the two. It was pretty much sluggish either way. I think I'll end up sticking with the 32 bit installation, I have a feeling that most of the odd results I've been getting are from overflowing long integers in c++ which shouldnt be happening for the numbers I am using if it was 64 bit. I dont know anything about XCFE or LXDE but I have heard they are lighter weight. Is it worth considering a window manager like Openbox or anything of that sort instead as well?

---

### Post by Don_Stahl on 2014-02-16
I don't know how Gnome Classic compares. I'm no expert... :confused: I have noticed that XFCE is snappier than Gnome 3 or Unity on the same machine, though. 

Here's a table. Note that these desktops were tested on different systems, so it's not purely apples-to-apples. The source for this information is from [http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce) , which has more info. But as you say, the demands of the application may be the real deciding factor on a 1- or 2-GB system.


[TABLE="width: 1"]
[TR]
[TD] **Name of **[B]Desktop Environment / Window Manager 

In Parenthesis: Operating System Used for Testing[/B][/TD]
[TD="align: center"] [B]RAM used
[/B][/TD]
[TD="align: center"] [B]% of CPU (2.6 GHz total) used
[/B][/TD]
[TD="align: center"] **Type**[/TD]
[/TR]
[TR]
[TD] **GNOME 3.x shell** (Fedora 17)[/TD]
[TD="align: center"] 248 MB[/TD]
[TD="align: center"] 1-2 %[/TD]
[TD="align: center"] desktop shell (GNOME 3.x-based)[/TD]
[/TR]
[TR]
[TD] **Unity** (Ubuntu 12.04 LTS)[/TD]
[TD="align: center"] 218 MB[/TD]
[TD="align: center"] 1-4 %[/TD]
[TD="align: center"] desktop shell (GNOME 3.x-based)[/TD]
[/TR]
[TR]
[TD] **MATE** (Linux Mint 13)[/TD]
[TD="align: center"] 205 MB[/TD]
[TD="align: center"]9-10 %[/TD]
[TD="align: center"] desktop environment[/TD]
[/TR]
[TR]
[TD] **GNOME 2.x shell** (Lubuntu 11.04)[/TD]
[TD="align: center"] 191 MB[/TD]
[TD="align: center"] 1 %[/TD]
[TD="align: center"] desktop shell (GNOME 2.x-based)[/TD]
[/TR]
[TR]
[TD] **Cinnamon** (Linux Mint 13)[/TD]
[TD="align: center"] 175 MB[/TD]
[TD="align: center"] 11-12 %[/TD]
[TD="align: center"] desktop shell (GNOME 3.x-based)[/TD]
[/TR]
[TR]
[TD] **GNOME 3.x Classic (Fallback Mode)** (Lubuntu 12.04)[/TD]
[TD="align: center"] 141 MB[/TD]
[TD="align: center"] 1-2 %[/TD]
[TD="align: center"] desktop shell (GNOME 3.x-based)[/TD]
[/TR]
[TR]
[TD] **KDE 4.8.2** (Lubuntu 12.04)[/TD]
[TD="align: center"] 131 MB[/TD]
[TD="align: center"] 1-3 %[/TD]
[TD="align: center"] desktop environment[/TD]
[/TR]
[TR]
[TD] **Razor-qt** (Lubuntu 12.04)[/TD]
[TD="align: center"] 117 MB[/TD]
[TD="align: center"] 1-2 %[/TD]
[TD="align: center"] desktop environment[/TD]
[/TR]
[TR]
[TD] [COLOR=#000000]**Xfce 4.8** (Lubuntu 12.04)[/COLOR][/TD]
[TD="align: center"] [COLOR=#000000]106 MB[/COLOR][/TD]
[TD="align: center"] 1-2 %[/TD]
[TD="align: center"] [COLOR=#000000]desktop environment[/COLOR][/TD]
[/TR]
[TR]
[TD] [COLOR=#000000]**LXDE** (Lubuntu 12.04)[/COLOR][/TD]
[TD="align: center"][COLOR=#0000FF] [COLOR=#000000]82 MB[/COLOR][/COLOR][/TD]
[TD="align: center"]1-2 %[/TD]
[TD="align: center"]desktop environment[/TD]
[/TR]
[TR]
[TD] **OpenBox** (Lubuntu 12.04)[/TD]
[TD="align: center"] 76 MB[/TD]
[TD="align: center"] 1-2 %[/TD]
[TD="align: center"] window manager[/TD]
[/TR]
[TR]
[TD] **Enlightenment (E17 Standard)** (Lubuntu 12.04)[/TD]
[TD="align: center"] 72 MB[/TD]
[TD="align: center"] 1-14 %[/TD]
[TD="align: center"] desktop environment[/TD]
[/TR]
[TR]
[TD] **JWM** (Lubuntu 11.04)[/TD]
[TD="align: center"] 58 MB[/TD]
[TD="align: center"] 1 %[/TD]
[TD="align: center"] window manager[/TD]
[/TR]
[TR]
[TD] **Fluxbox** (Lubuntu 12.04)[/TD]
[TD="align: center"] 55 MB[/TD]
[TD="align: center"] 1-3 %[/TD]
[TD="align: center"] window manager[/TD]
[/TR]
[TR]
[TD] **IceWM** (Lubuntu 12.04)[/TD]
[TD="align: center"] 53 MB[/TD]
[TD="align: center"] 3 %[/TD]
[TD="align: center"] window manager
[/TD]
[/TR]
[/TABLE]

---

### Post by lykwydchykyn on 2014-02-16
If your processor wasn't 64 bit, the 64bit installer wouldn't have booted, much less installed.

Changing your desktop environment is probably the simplest and most effective way to make the system more performant.  Switching to XFCE or LXDE will result in a *huge* difference from GNOME or KDE.  Openbox will be even faster, but you'll lose some friendly functionality that you might like (desktop icons, e.g.).

Making sure your graphics hardware has the best possible driver is another issue.  If you have NVidia, the propreitary nvidia-glx driver will probably perform much better.  If it's Intel, not much you can do except try a kernel upgrade.  If it's AMD/ATI, it's kind of a tossup.  Sometimes proprietary works better, sometimes not.

---

### Post by mips on 2014-02-17
> **eric28 said:**
> Aloha!
Some more info:
1 Gb ram. 2x512mb
Intel Celeron D 
previously ran windows xp
originally purchased around 2006-2007

That's not a very powerful system. Which DE are you using? Gnome, KDE, Unity will not run great on that setup. With 1GB of RAM it's probably using your swap as well which would make things very slow.

Change your DE to XFCE or LXDE, alternatively you can go even lighter by only using a WM like Openbox etc (Chrunchbang etc). More RAM would really help so if you could get 2GB of RAM things would greatly improve (RAM is cheap or even free if you ask around).

If you installed a 64-bit OS then your CPU is 64-bit capable else it would not have installed in the first place.

---

### Post by mastablasta on 2014-02-18
Actually Gnome and KDE will run ok as long as all special desktop effects are turned off. was just checkign for other reaosns ram usage and it was little over 200 MB on Kubuntu 12.04. the PC has 1.25 GB and is faster (or at leats feels faster and snapier) than the other 4GB single core WinXP mashicne

---

### Post by mips on 2014-02-18
> **mastablasta said:**
> Actually Gnome and KDE will run ok as long as all special desktop effects are turned off. was just checkign for other reaosns ram usage and it was little over 200 MB on Kubuntu 12.04. the PC has 1.25 GB and is faster (or at leats feels faster and snapier) than the other 4GB single core WinXP mashicne

You can put lipstick on a pig but it's still a pig...

---

### Post by mastablasta on 2014-02-19
ha, ha....! yes that is correct. KDE is still the most resoruce heavy of them all, but then again it has plenty of features... and i think, it will still run nicely on that maschine i believe.

---

### Post by Meowcenary on 2014-02-19
Sorry for the delay in response I've been busy lately with classes and forgot to check back. I appreciate all the information here! I have been using KDE and Gnome Classic, but I'll look into getting more RAM for the machine and for the moment switch to openbox. I have a little experience with Openbox so it will probably be a relatively easy change to make.

---

### Post by Meowcenary on 2014-02-19
This was a duplicate post, please remove.

---

### Post by orb9220 on 2014-02-19
> **mastablasta said:**
> ha, ha....! yes that is correct. KDE is still the most resoruce heavy of them all 

Not in my world Unity,Gnome & Cinnamon used more ram and not as snappy or smooth as KDE.

I continually see this FUD about KDE being a resource hog and just isn't true. 
I know people that run KDE smooth & snappy on a 1gb netbook. Try that with Unity,Gnome or Cinnamon.

Sorry but with me even running a simple conky and yaWP weather app my desktop.
And chimes in at 287mb to desktop on dual core dual display desktop.
Running SolydK KDE which is a Debian semi-rolling based on Testing.
On other distro's like Ubuntu Unity or Cinnamon or Gnome that goes to 350-450mb to desktop.
.

---

### Post by mips on 2014-02-20
> **Meowcenary said:**
> I have a little experience with Openbox so it will probably be a relatively easy change to make.

Best Openbox distros
[http://sourceforge.net/projects/manjarotest/files/0.8.9/rc4/openbox/](http://sourceforge.net/projects/manjarotest/files/0.8.9/rc4/openbox/) this will be released on Sunday as the stable release.
[http://manjaro.org/2013/12/31/manjaro-openbox-0-8-9-preview-available/](http://manjaro.org/2013/12/31/manjaro-openbox-0-8-9-preview-available/)

[http://crunchbang.org/download](http://crunchbang.org/download)

The Manjaro one is my favourite, it's less bloated, has it's own tools to install gpu drivers, kernels etc, it's a very polished distro and easy to use, the community is also great.

---

### Post by Meowcenary on 2014-02-20
> **mips said:**
> Best Openbox distros
[http://sourceforge.net/projects/manjarotest/files/0.8.9/rc4/openbox/](http://sourceforge.net/projects/manjarotest/files/0.8.9/rc4/openbox/) this will be released on Sunday as the stable release.
[http://manjaro.org/2013/12/31/manjaro-openbox-0-8-9-preview-available/](http://manjaro.org/2013/12/31/manjaro-openbox-0-8-9-preview-available/)

[http://crunchbang.org/download](http://crunchbang.org/download)

The Manjaro one is my favourite, it's less bloated, has it's own tools to install gpu drivers, kernels etc, it's a very polished distro and easy to use, the community is also great.

Does the Manjaro distro have solid community support? My intention for the moment was to just run debian with only a window manager or install crunchbang. I've never heard of Manjaro before. 

EDIT: Didnt realize that Crunchbang was built from Debian to be minimal. So I guess that will be my current course of action. Question on Manjaro distro remains though.

---

### Post by mips on 2014-02-20
> **Meowcenary said:**
> Does the Manjaro distro have solid community support?

Yes, it has a very strong & friendly community. I've seen quite a few familiar faces there from other communities.

It has official English & German forums and then it has unofficial forums for brazil, belgium, french, polish, spanish & turkish. Very active IRC community. Also have LOTS of repository mirrors around the world. Community are often consulted by the devs wrt to features they want and are open to suggestions.

0.8.9 will be released this coming Sunday but it's basically 0.8.9RC4 as we have it now.

---

