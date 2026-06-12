---
title: "Fluxbox / Fluxbuntu Anyone?"
date: 2007-10-15
forum: Desktop Environments
---

### Post by kirkquitar on 2007-10-15
I started out with Ubuntu a while ago, but recently tried Kubuntu (Gutsy RC) and still think that the DE is messy/clunky/unpolished. I mean it can look really good, but it's not very functional compared to Gnome in my opinion. So I'm back to Gnome, but I was wondering about Fluxbox. XFCE looks a little plain to me, but the fluxbuntu screenshots that are up ([http://fluxbuntu.org/](http://fluxbuntu.org/)) look pretty good. Anyone had any experience with Fluxbox, positive or negative? What I'm looking for is probably customizability, and cleanliness/stability, haha I think. Anyway, if you've tried Fluxbox out, how was it?

---

### Post by kellemes on 2007-10-15
Listen.. you can simply install fluxbox and see for yourself if it's made for you..
Fluxbuntu *may* be a little less bloated as Ubuntu when you install the hole package but the main difference is the wm.

---

### Post by DaveB on 2007-10-15
I tried an install of antiX 6.5 (mepis). It has choice of fluxbox or icewm. Both are very fast and very plain desktops. Fluxbux menus are right-click and are well-organized. Icewm menu seems to be preset with expected applications that may not be installed, but it's fairly easy to edit icewm toolbar setup to include favorite applications.

---

### Post by cknight on 2007-10-15
I recently switched from KDE to Fluxbox and couldn't be happier.  Fluxbox is minimalistic, simple (once configured) and oh so fast (wait till you see how quickly the session is usable after login.  I first thought something went wrong as it loaded so quickly!).  It's made me realize how much bloat is in KDE/Gnome that I never used/didn't need.  Fluxbox never gets in my way.  It does what it says on the tin (manages windows) without trying to do everything else in the planet too.

But, there is a small price.  You must be comfortable editing configuration files.  My external USB drive doesn't automount and I'll likely find other small anoyances, but then I'm learning so much more about Linux that I did with KDE and in the process building a user experience more customized to me and my computer's resources.   Honestly, its given me a whole new outlook as to how I use my operating system now.  

Of course, this works for me, but may not be best for you.  Try it out.  There's tons of support out there in IRC and here in the Ubuntu forums.  I've had snappy answers to all my issues so far and couldn't be happier.  Good luck and have fun!

---

### Post by Crooksey on 2007-10-15
Before i make my post

> 
But, there is a small price. You must be comfortable editing configuration files. My external USB drive doesn't automount 

Are you sure hal as started/
```

sudo /etc/init.d/hal start
```

Fluxbuntu is fairly pointless, you may aswell just isntall fluxbox within ubuntu, without the hassle of a re install.

If you are wanting to try new WM's, give openbox a go, you can run it alongside gnome fairly easily.

---

### Post by kerry_s on 2007-10-15
> **kirkquitar said:**
> I started out with Ubuntu a while ago, but recently tried Kubuntu (Gutsy RC) and still think that the DE is messy/clunky/unpolished. I mean it can look really good, but it's not very functional compared to Gnome in my opinion. So I'm back to Gnome, but I was wondering about Fluxbox. XFCE looks a little plain to me, but the fluxbuntu screenshots that are up ([http://fluxbuntu.org/](http://fluxbuntu.org/)) look pretty good. Anyone had any experience with Fluxbox, positive or negative? What I'm looking for is probably customizability, and cleanliness/stability, haha I think. Anyway, if you've tried Fluxbox out, how was it?

if you want fast, fluxbox is the way to go, but if you thought xfce4 was plain, than i don't think you'll dig fluxbox. most WM's are very configurable, the end look depends on the effort you put into it. myself i moved from fluxbox to jwm, as i don't need much and don't care about theming and all that.

---

### Post by TeaSwigger on 2007-10-16
I've been a desktop testing fiend lately, and I'm quite partial to Fluxbox. Once you get it set up to suit, it's great. It is what you make it, so to speak.

Check these threads:
HOWTO: get a Fluxbox menu (and customization)
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)
Fluxbox fast and cool!
[http://ubuntuforums.org/showthread.php?t=483613](http://ubuntuforums.org/showthread.php?t=483613)
fluxbox how-to (compiling from source the latest version) plus tips & tricks
[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

I also suggest IceWM for speed - but I can't stand many of its default settings; you'll find this thread invaluable if you try Ice:
Anyone else dig IceWM? 
[http://ubuntuforums.org/showthread.php?t=263710](http://ubuntuforums.org/showthread.php?t=263710)

Avail yourself of the choices we're gifted with. :)

---

### Post by kirkquitar on 2007-10-16
Thanks for the tips, I think I'm going to try xfce. I was looking around and it seems that it's pretty configurable, and I think I'm going to go with Compiz as my WM. Haha, I know that it's basically the opposite of IceWM or Fluxbox... but my computer can easily handle it.

---

### Post by jviscosi on 2007-10-16
> **cknight said:**
> My external USB drive doesn't automount

I have Fluxbox run gnome-volume-manager at startup to handle USB and FireWire (oops, sorry, IEEE 1394  *<looking around for Apple attorneys>*) devices like cameras and thumbdrives. Of course, you still don't get a desktop icon when you connect an external drive, but I don't want one.  ;-)

---

### Post by RedSquirrel on 2007-10-16
> **kirkquitar said:**
> Thanks for the tips, I think I'm going to try xfce. I was looking around and it seems that it's pretty configurable

It is. It is also very *easy* to configure. Most of the stuff is point & click. 



> **cknight said:**
> My external USB drive doesn't automount

ivman might be worth looking into. 

thunar has a volume manager plugin as well: thunar-volman-plugin.

(Note: If you use Thunar, you'll be pulling in some xfce dependencies, which might not be what you're after.)

I don't use any of these myself because I prefer to mount things manually, but I just thought I'd mention them. ;)

---

### Post by jimmywu013 on 2007-10-17
Ha ha - love the desktop :lol:
EDIT: the thumbnail that kerry_s posted

---

### Post by markp1989 on 2007-10-17
i have tried using fluxbox , and i was wondering how i could manage the network, in gnome i have that network thing in the notification area, is the a similar thing to this in flux, because im using a laptop. so being able to easily configure the network is a must have

---

### Post by cknight on 2007-10-17
> **RedSquirrel said:**
> 
(Note: If you use Thunar, you'll be pulling in some xfce dependencies, which might not be what you're after.)

What's the disadvantage of pulling in some xfce dependencies?  Is it higher cpu/memory load when running Thunar because its using xfce libraries while I've already got gnome or kde libraries loaded (in memory)?

---

### Post by RedSquirrel on 2007-10-17
> **cknight said:**
> What's the disadvantage of pulling in some xfce dependencies?  Is it higher cpu/memory load when running Thunar because its using xfce libraries while I've already got gnome or kde libraries loaded (in memory)?
Yes, that's correct. If you have a really powerful system, you might not notice any difference from having these sorts of things installed and running. In my case, I like to tinker on an old computer so I keep the amount of stuff I install on the hard disk and the stuff I have running to a minimum.

As mentioned earlier by jviscosi, if you have GNOME installed (or some of its components) you can run **gnome-volume-manager** with Fluxbox. That should automount your devices. Just put it in your ~/.fluxbox/startup file, near the bottom, but before the line 'exec /usr/bin/fluxbox'.

```
gnome-volume-manager &
```

---

### Post by x1101 on 2008-03-19
This is incorrect. I have tried both options, and fluxbuntu runs MUCH faster than a default install of ubuntu with fluxbox installed over top of it. This is because when you install fluxbuntu, you dont install any part of GNOME or KDE or even XFCE unless you do that manually. It does require more work to customize, but if the end goal is speed, fluxbuntu is better. At least this is the case when using the two on old hardware. On my PIII 750 with 193mb ram, fluxbuntu is failry snappy (for anything on a system this old) whereas ubuntu+fluxbox is less so...


Hope this helps someone

---

### Post by Rhubarb on 2008-03-19
Yes indeed.  I've got fluxbuntu installed on my old Celeron 566MHz with 512MB of RAM.  It does take a while to start up, but once it's up, it runs nice and fast :)

---

### Post by tad1073 on 2008-03-19
How do I turn off the little window that shows x-y position, and what is the code to add the date to the toolbar?

---

### Post by RedSquirrel on 2008-03-19
> **x1101 said:**
> **[COLOR=Blue]This[/COLOR]** is incorrect. ...

What do you mean by "This"? :confused:

Edit: Looking over the thread, it appears you are referring to post #5 (?).

---

### Post by Patb on 2008-03-19
I started using Fluxbox about a year ago and I'm very pleased with it. Can't imagine going back, even though my system is quite fast.  I must admit though that I am not one for "eye-candy".  

Advantages (imo): 
- Fast to load
- Minimal use of background processes
- Gnome and KDE programs can be used if needed without necessarily having them running all the time
- Simple and complete menu editing via Fluxmenu
- Easy to edit key bindings (but beware of Fluxkeys! - see below)
- I actually like **not** having a conventional "Desktop" to clutter (but you can make one if you want :))

Disadvantages:
- A major snag with Fluxkeys which corrupts the keys file.  (Solution = copy the mouse key bindings from the original default keys file. [More details here]("http://ubuntuforums.org/showthread.php?t=617812")). This bug must deter many potential Fluxbox users - what a shame!

Other comments:
- "Fluxbuntu" is better suited to an old or limited system because it uses only GTK compatible programs instead of the "heavier" Gnome or KDE programs.  For a fast system though, it seems okay to install Fluxbox over an existing Gnome or KDE setup - that way, there are less dependency complications if you later want to install some of the Gnome/KDE software.  I've tried it both ways.
- In this thread, RedSquirrel suggests gnome-volume-manager to automount devices.  I have found thunar-volman okay for the devices I have (camera, usb storage, nothing complicated)

Hope this is helpful.  Corrections welcome of course.  Cheers, Pat.

---

### Post by PurposeOfReason on 2008-03-19
> **tad1073 said:**
> How do I turn off the little window that shows x-y position, and what is the code to add the date to the toolbar?
All of that is in the ~/.fluxbox/init file. Just read it and you'll know what to do.


After using both a lot, I say openbox is lighter and better once you have pipe menus. ;)

---

### Post by RedSquirrel on 2008-03-19
> **tad1073 said:**
> How do I turn off the little window that shows x-y position, and what is the code to add the date to the toolbar?

Not sure about the first part.

For the clock, in ~/.fluxbox/init, there should be a line similar to:

```
session.screen0.toolbar.tools:  workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow,         nextwindow, [COLOR=Blue]**clock**[/COLOR]

```As far as changing the format of the clock, take a look at the man page for the 'date' command 

```
man date
```

and see the available formats there.

I use:

```
%a %b %e, %l:%M %P
```

---

### Post by tad1073 on 2008-03-19
> **PurposeOfReason said:**
> All of that is in the ~/.fluxbox/init file. Just read it and you'll know what to do.


After using both a lot, I say openbox is lighter and better once you have pipe menus. ;)

thanks

---

### Post by RedSquirrel on 2008-03-19
> **Patb said:**
>  ... Disadvantages:
- A major snag with Fluxkeys which corrupts the keys file.  (Solution = copy the mouse key bindings from the original default keys file. [More details here]("http://ubuntuforums.org/showthread.php?t=617812")). This bug must deter many potential Fluxbox users - what a shame! ... 

Possibly. It is important to bear in mind, however, that fluxconf is a separate project (not part of fluxbox), is old and buggy and is not maintained anymore.

I don't think it's that hard to edit the configuration files by hand. ;)



> **Patb said:**
> - In this thread, RedSquirrel suggests gnome-volume-manager to automount devices.  I have found thunar-volman okay for the devices I have (camera, usb storage, nothing complicated)

RedSquirrel also suggested ivman and thunar-volman-plugin. :p :grin:

---

### Post by tad1073 on 2008-03-19
> **RedSquirrel said:**
> Not sure about the first part.

For the clock, in ~/.fluxbox/init, there should be a line similar to:

```
session.screen0.toolbar.tools:  workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow,         nextwindow, [COLOR=Blue]**clock**[/COLOR]

```As far as changing the format of the clock, take a look at the man page for the 'date' command 

```
man date
```

and see the available formats there.

I use:

```
%a %b %e, %l:%M %P
```

thanks

for the window postion
```
session.screen0.showwindowposition:
```

my clock format
```
%m/%d/%y %x
```

---

### Post by RedSquirrel on 2008-03-19
> **tad1073 said:**
> 
for the window postion
```
session.screen0.showwindowposition:
```

Thanks for the info. I never bothered to turn that off, but now I know how, should I ever want to. :)



> **tad1073 said:**
> my clock format
```
%m/%d/%y %x
```

I assume you meant:
 ```
%m/%d/%y %[COLOR=Blue]X[/COLOR]
```$ date +'%m/%d/%y %x'
03/19/08 19/03/08

$ date +'%m/%d/%y %X'
03/19/08 09:39:21 PM

:grin:

---

### Post by tad1073 on 2008-03-19
> **RedSquirrel said:**
> Thanks for the info. I never bothered to turn that off, but now I know how, should I ever want to. :)





I assume you meant:
 ```
%m/%d/%y %[COLOR=Blue]X[/COLOR]
```$ date +'%m/%d/%y %x'
03/19/08 19/03/08

$ date +'%m/%d/%y %X'
03/19/08 09:39:21 PM

:grin:

yep, %X is what I meant:grin:

I removed the workspace arrows, I see no need for them if you can scroll on the toolbar to switch between workspaces.

I also figured out/found out about the window grouping with the window tabs-Fluxbox Rox

Now all I need to do is turn Ubuntu into Fluxbuntu. Get rid of gnome for one, but I still use the gnome gui for alot of things. I have been thinking about swithing to Arch and using fluxbox as my window manager gut I am still too green

---

### Post by linuxlizard on 2008-03-20
If you want to see fluxbox done well, you should check out pcfluxboxos.
I've got it running on an older laptop and desktop that xubuntu was too sluggish for, and it zips along like lightning.
USB and all automounts, wireless networks are auto-detected on the laptop and my home network auto-connects, connecting on public wireless locations is a snap too.
 It's not as pretty as fluxbuntu, but it's more finished and zips along faster (run firefox no problem on my desktop)- I've got some lovely themes going too, plus there's tons of software in synaptic.

My laptop is a p3 700mhz with 192 mb ram.

My desktop is a p2 333 mhz with 128 mb ram.

Both boot really fast- the laptop in probably 20-25 seconds, the desktop only slightly longer.

---

### Post by Griff on 2008-03-20
I've used both fluxbuntu and ubuntu w/ fluxbox on the same machine and the difference is huge.  Fluxbuntu is NOT just ubuntu with fluxbox preinstalled/configured.  The fluxbuntu team has put a lot of work and thought into what default software is preinstalled and what services are started at boot time.  The artwork is also very [I]sexy][/I. :)  I almost quit using an old laptop of mine until I threw that on it.  It was smokin' after installation.  You could get a similar setup with an ubuntu server install and copying everything they did, but you still miss the sexy artwork.
I love it.
--Griff

---

### Post by tad1073 on 2008-03-20
What would I need to do to turn my ubuntu box into a fluxbuntu box w/o having to download the iso?

---

### Post by RedSquirrel on 2008-03-21
> **tad1073 said:**
> What would I need to do to turn my ubuntu box into a fluxbuntu box w/o having to download the iso?

As mentioned above by Griff, you could build up your system from a minimal installation but you won't get the fancy Fluxbuntu artwork. The following guide might give you some ideas:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

You can also use the alternate install CD to install the command-line system.

Alternatively, I suppose you could alter your existing system by removing packages and/or turning off unneeded services. I prefer the "build up from the minimal system" method over the "remove packages" method.

There was some talk a while ago about having a fluxbuntu-desktop metapackage in the repositories, but I'm not sure if that's going to happen. I don't follow Fluxbuntu development closely because I don't plan to use it. ;)


With regard to your comment about Arch Linux:

A little more linux experience might help if you decide to try out Arch. On the other hand, some people try it with very little experience and seem to do alright. The Arch documentation is quite good so if you're willing to read the instructions, look things up, and learn on your own you might be OK. But there's no rush. The Arch forums are quite helpful as well, but the expectation is that you will read the available documentation first and ask questions later. ;)

I was using Arch for a little while, but I switched to Debian (currently running unstable (AKA sid)). I think Arch needs more developers to keep on top of security updates. Arch has many good points, so I'll keep an eye on them to see how things progress over the next few months/years.

By the way, if you get some practice installing a minimal Ubuntu (or Debian!) system, it might be worthwhile experience if the day comes that you decide to try Arch. With Arch, once you have completed the installation, you boot into a command-line system and add packages from there.

---

