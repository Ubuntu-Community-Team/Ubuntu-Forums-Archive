---
title: "DIY Desktop Environment?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by noriek on 2010-10-24
Hello all,


Just installed Ubuntu 10.04 on my Sony Vaio laptop which sports a still healthy spec of 1GHz Duron and 512MB ram; enough for daily applications. However, the default installation is dog slow! I realise the Ubuntu I replaced windows with is much more feature-full and relatively modern but it's slowed the machine to beyond useless. Therefore I hope to 'build' my own desktop environment.

I'm starting from a position of ignorance, as ever, so I need first some indication of beyond the window manager what else makes up a DE. File manager; taskbar/panel app etc. And secondly, what equivalent pieces of software are available; which are faster; what features do they have; what are their file/lib dependencies etc?

I'm thinking openbox for window management; what might complement it?

---

### Post by kerry_s on 2010-10-24
try xubuntu, if thats still to much try lubuntu.
no need to go custom just yet, get some experience under your belt first.

[http://www.xubuntu.org/](http://www.xubuntu.org/)

[http://lubuntu.net/about](http://lubuntu.net/about)

---

### Post by mcduck on 2010-10-24
Openbox would be a good choice.

I have one Ubuntu system running a minimal Ubuntu install, with Openbox as the window manager and it uses about 40MB of RAM. Pretty lghtweight but takes a bit of work to set up.

I use tint2 as my tasklist/pager/notification area, PCManFM for file manager, Nitrogen to handle desktop background, xcompmgr for window shadows & transparency and gnome-terminal for a terminal. Since it's a laptop I use Network Manager, on a desktop machine I'd probably just configure a wired network by hand.

I'm not using any DM, instead I simply configured Ubuntu to automatically start X for me when I log in to TTY1. Other TTY's of course work as usually. I tried couple of lightweight GUI login methods and in the end decided that I can just as well type my user name & password without a GUI. :)

If you go for Openbox you'll be able to pick plenty of usefull GUI apps and other stuff from LXDE. It uses Openbox as well, and has nice lightweight GTK2 apps with very little dependencies. Of course you could also just give Lubuntu a try or install LXDE on your current setup to see if helps with your performance issues.

---

### Post by mr_luksom on 2010-10-24
Lubuntu would be super on your machine.

```
 sudo apt-get install lubuntu-desktop 
```

If you like it, you can ditch GNOME by doing this (thanks psychocats):

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by noriek on 2010-10-24
Hey, thanks all!

I've was previously running a Gnome/Openbox session, which I run on my desktop as a matter of course as it seems to offer a slight advantage over the metacity default. This is only an anecdotal/by-feel assessment but I'm confident of a real performance benefit. However, I'd like a streamlining of the surrounding apps.

On the suggestion of all of you I've 'apted' LXDE (just the DE, not lubuntu) and again the feel is definitely of increased speed. A measure I like to use is the time taken to open Open Office writer. The smaller DE overheads do seem to free up memory and cpu cycles. I have, however, been unable to locate the LXDE network manager and so have used nm-applet (GNOME manager?) to connect my wireless. This is kind of defeating the point unless I can be assured it's the superior app for this task? MC Duck?? (You continue to use it even with your custom system?)

On first impressions I could definitely live with LXDE; I'll make it the laptop default. However, more optimisation seems possible, potentially stripping out functionality which I don't need on this particular machine. Hopefully I can use what I learn to fire-up my G3 iMac to use able speed.

Would appreciate more examples of custom setups in this vein.

Cheers

---

### Post by dougalkerr on 2010-10-24
I wander, when you installed your system - how much Swap area did you allocate?

I always allocate twice the amount of system RAM that I have and I have Ubuntu 10.10 running on a nine year old Dell Inspiron 2400 and it goes like the clappers with almost every program opening in a flash.

Openoffice runs like a dream too.

Have a look at your Swap size. 512Mb RAM should allow your Vaio to run well even with the 1GHz chip.
The only thing that might be slowing you down otherwise may be your graphics card. If you leave the Appearance Visual Effects at None or Normal this may help also.

Good luck.

---

### Post by mcduck on 2010-10-24
> **noriek said:**
> I have, however, been unable to locate the LXDE network manager and so have used nm-applet (GNOME manager?) to connect my wireless. This is kind of defeating the point unless I can be assured it's the superior app for this task? MC Duck?? (You continue to use it even with your custom system?)

Network Manager has very little extra dependencies I wouldn't already need/have, so I use it. You can use Wicd instead if you prefer.

It's not about avoiding programs from Gnome or some other DE, it's about picking the programs that do the job for you and add little extra dependencies or resource usage.

I also use Gnome-terminal and Gedit, even though Leafpad and lxde-terminal would be more resource friendly. I just decided that the difference in resource usage is insignificant (it really is, as I'd already have most of their dependencies anyway) and that those have features that make them more usefull to me than the alternatives.

In the end the biggest difference still comes from getting rid of all the services and other stuff you don't use, not from changing individual components of your desktop. So if you want to go for a really lightweight setup, then it's not a question of what things you run on your computer, but what you *don't* run. And the simplest way to do that is to start with the minimal install and then add whatever you need.

On the other hand, based on the specs you really shouldn't need to go that far. Are you sure your performance issues aren't caused by graphics card drivers (or lack of them, really)? What kind of CPU load & memory use you have when the system is idle, and have you tried checking what processes are using most of those resources?

---

### Post by noriek on 2010-10-25
As you both point out, I too am surprised that the the unresponsiveness of the laptop given it's specs. Regarding swap, I had tried to install Ubuntu with 500MB swap and the installation failed. It's not at all clear that this was a swap issue to be fair but I then enlarged the swap to 750MB and installation was successful. When I first experimented with linux (in the days of RedHat 5 I think) I allowed for 1.5 or maybe 2 times swap:ram. Maybe I'll go back to this, as you have done, although I've been successful with equal swap/ram values before this.

Re: visuals. The laptop has discreet grphics memory, which at the time was a bonus in terms of speed but in this time of huge and fantastic visual effects and settings the 8MB it provides is somewhat restricting. Unfortunately there is no bios option for a main memory sharing either. As such compiz and other visual effects are largely minimised.

We're in complete agreement on processes and I do attempt to minimise unused services/applications however, I think my approach was more along the lines of maximal memory footprint, during which I assess the processes too. Last time I 'toped' XOrg was a big memory drain, as one might expect. This could be partly a result of the limited graphics memory and my choice to run in 32bit when I should have really choosen 24bit or 16K. Anyway, I can't remember the other memory hogs. I'll have a look at next opportunity and report back. Thanks again for ideas and suggestions.

Cheers

---

