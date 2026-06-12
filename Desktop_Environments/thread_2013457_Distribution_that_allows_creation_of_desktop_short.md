---
title: "Distribution that allows creation of desktop shortcuts like Ubuntu 11.04"
date: 2012-06-30
forum: Desktop Environments
---

### Post by wpshooter on 2012-06-30
Is there **ANY** Linux distribution(s) that still have the capability to create desktop shortcuts to applications and web links by simply right-hand clicking on the desktop as it was done so well in Ubuntu version 11.04 or am I looking down an empty well ???

Thanks.

---

### Post by zombifier25 on 2012-07-01
Desktop shortcuts are dead. Pinning your most used apps on the Unity Launcher or GNOME Shell's bar is much much more convenient.

You can always use a non-GNOME distro.

---

### Post by 3Miro on 2012-07-01
Desktop shortcuts are a feature of the Desktop Environment, not the distribution. You need to install anything non-Gnome 3, that is KDE, XFCE, LXDE or Gnome 2 (i.e. Cinnamon). You can install those over an existing Ubuntu installation.

---

### Post by wpshooter on 2012-07-01
> **3Miro said:**
> Desktop shortcuts are a feature of the Desktop Environment, not the distribution. You need to install anything non-Gnome 3, that is KDE, XFCE, LXDE or Gnome 2 (i.e. Cinnamon). You can install those over an existing Ubuntu installation.

I just installed BOTH Cinnamon and KDE on an installation of Linux Mint 12 and I don't see where this allows me to add shortcuts to the desktop.  Am I missing something ?

Thanks.

---

### Post by Bucky Ball on 2012-07-01
Works fine in Xfce. Install xfce4, logout, choose 'xfce session' from the session pop-up, login.

---

### Post by 3Miro on 2012-07-01
> **wpshooter said:**
> I just installed BOTH Cinnamon and KDE on an installation of Linux Mint 12 and I don't see where this allows me to add shortcuts to the desktop.  Am I missing something ?

Thanks.

Actually I have never used Cinnamon, but it should be just like Gnome 2.

For KDE, you need to set this up. By default, you have the plasma desktop workspace and you can add "Folder View" widget, which is an area on your desktop that displays the content of a certain folder. You an easily have several of those open. You can also go back to the classic style (like Gnome 2), by right-click on the desktop and change the settings for Folder View or Desktop View or something like that (I forgot the exact setting, I haven't used KDE in a while).

I am using XFCE and then things just work as you would expect.

---

### Post by anaconda on 2012-07-01
+1 for xubuntu

Xubuntu has this feature. And most features gnome2 had.

---

### Post by wpshooter on 2012-07-01
> **Bucky Ball said:**
> Works fine in Xfce. Install xfce4, logout, choose 'xfce session' from the session pop-up, login.

I installed this xfce from software center under 12.04 and then I logged out and switched to the xfce session.  I did NOT particularily like it, so I then went back into regular Ubuntu session under 12.04 and went back to software center and UNINSTALLED the xfce BUT when I logout out again low & behold, the xfce session choice was still on the list of login choices.  

Ain't that just fabulious !!!

---

### Post by 3Miro on 2012-07-01
> **wpshooter said:**
> I installed this xfce from software center under 12.04 and then I logged out and switched to the xfce session.  I did NOT particularily like it, so I then went back into regular Ubuntu session under 12.04 and went back to software center and UNINSTALLED the xfce BUT when I logout out again low & behold, the xfce session choice was still on the list of login choices.  

Ain't that just fabulious !!!

xfce is a meta package, it doesn't install anything by itself, it only installs other programs as dependencies. If you go to the terminal and type:
```
sudo apt-get autoremove
```
you will see a list of all packages that were installed as dependencies and are no longer needed. If you say "yes" it will uninstall XFCE.

You can also go to the psychocats web-page:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

and find commands for adding and removing different DE.

---

### Post by wpshooter on 2012-07-01
> **3Miro said:**
> xfce is a meta package, it doesn't install anything by itself, it only installs other programs as dependencies. If you go to the terminal and type:
```
sudo apt-get autoremove
```
you will see a list of all packages that were installed as dependencies and are no longer needed. If you say "yes" it will uninstall XFCE.

You can also go to the psychocats web-page:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

and find commands for adding and removing different DE.

Thanks but my point is that if I can install this feature thru the Ubuntu 12.04 "SOFTWARE CENTER" then I should be able to UNINSTALL it from that same place.  Just one more example of they know how to get it to install to your computer but they sure skip a lot when it comes to the UNINSTALLING it from your computer part !!!

---

### Post by diesch on 2012-07-01
[Arronax](http://www.florian-diesch.de/software/arronax/) is a plugin for Nautilus that brings back the "Create starter" option in the right-click menu. It currently only supports application shortcuts but not weblinks.

It should work with any desktop that uses Nautilus 3.4 to draw the desktop, likeUnity,  Gnome Shell and Gnome Classic Ubuntu 12.04

---

### Post by angry_johnnie on 2012-07-01
debian 6 (squeeze) is still using gnome 2.  the thing about debian, of course, is that it's stable and, thus, rather outdated.  as long as you don't mind not having the latest version of whichever software you happen to be running, it should be alright.  i have debian 6 on my secondary desktop.  everything works.

if you'd rather stick with the 'buntus, then, as some people have already suggested, xfce might be your best choice.  on this, my primary desktop, i'm running ubuntu 12.04 with xfce.  it's the closest thing to gnome 2, but it does take some adjusting.  it won't be just like gnome 2 just out of the box.  you'd need to mingle with it for a while.

as far as uninstalling xfce, it's not as easy as installing it.  the previously mentioned psychocats page has the correct instructions.  it's not really a matter of whether it's been made easy to install or uninstall.  it's more a matter of understanding how the debian package system works.  xfce is just a meta-package.

arronax sounds promising, but it's still got some bugs.

unity is what ubuntu has to offer.  gnome 3 is what gnome developers have to offer.  if you want something that's no longer officially available you may stil find it, but it'll take some tweaking and will probably come with a learning curve.

good luck, though.  gnome 2 was fantastic.  unity made me switch to xfce. :)

---

### Post by stinkeye on 2012-07-02
> **diesch said:**
> [Arronax](http://www.florian-diesch.de/software/arronax/) is a plugin for Nautilus that brings back the "Create starter" option in the right-click menu. It currently only supports application shortcuts but not weblinks.

It should work with any desktop that uses Nautilus 3.4 to draw the desktop, likeUnity,  Gnome Shell and Gnome Classic Ubuntu 12.04
Just tried arronax. Very useful.Thanks.
Allows me to right click on a script and create a .desktop file
to drag to the launcher.

---

### Post by wpshooter on 2012-07-02
> **angry_johnnie said:**
> debian 6 (squeeze) is still using gnome 2.  the thing about debian, of course, is that it's stable and, thus, rather outdated.  as long as you don't mind not having the latest version of whichever software you happen to be running, it should be alright.  i have debian 6 on my secondary desktop.  everything works.

if you'd rather stick with the 'buntus, then, as some people have already suggested, xfce might be your best choice.  on this, my primary desktop, i'm running ubuntu 12.04 with xfce.  it's the closest thing to gnome 2, but it does take some adjusting.  it won't be just like gnome 2 just out of the box.  you'd need to mingle with it for a while.

as far as uninstalling xfce, it's not as easy as installing it.  the previously mentioned psychocats page has the correct instructions.  it's not really a matter of whether it's been made easy to install or uninstall.  it's more a matter of understanding how the debian package system works.  xfce is just a meta-package.

arronax sounds promising, but it's still got some bugs.

unity is what ubuntu has to offer.  gnome 3 is what gnome developers have to offer.  if you want something that's no longer officially available you may stil find it, but it'll take some tweaking and will probably come with a learning curve.

good luck, though.  gnome 2 was fantastic.  unity made me switch to xfce. :)

After trying about 4 to 5 distributions over the weekend, I decided to go back to good old Natty 11.04.  As far as I am concerned, the Ubuntu distributions since Natty have been a less desirable choice.

Don't know what I will do when that expires, might have to think about going back to MS$ and put up with all those viruses and malware problems !!!

Thanks.

---

### Post by chocklet on 2012-07-02
It takes little effort to clutter up a Unity desktop with
- scripts that were created by right clicking, creating a new document, editing the document, and making executable.
- programs that were put there by copying .desktop files from /usr/share/applications to the desktop (using nautilus)
- links to an URL (created using gnome-desktop-item-edit)
- documents saved and/or copied there

One script/launcher on my desktop is simply...
gnome-desktop-item-edit --create-new ~/Desktop

In a perfect world, old functionality would not be reduced when new features are added.  But the FOSS community has clearly accepted the practice of reducing functionality without consideration of the impact upon home users.  That said, then speaking for myself and my family, given our particular use of computers (we spend far more time using applications than messing with the operating system), the impact is not so great that we can't compensate easily enough.

---

### Post by wpshooter on 2012-07-02
> **chocklet said:**
> It takes little effort to clutter up a Unity desktop with
- scripts that were created by right clicking, creating a new document, editing the document, and making executable.
- programs that were put there by copying .desktop files from /usr/share/applications to the desktop (using nautilus)
- links to an URL (created using gnome-desktop-item-edit)
- documents saved and/or copied there

One script/launcher on my desktop is simply...
gnome-desktop-item-edit --create-new ~/Desktop

In a perfect world, old functionality would not be reduced when new features are added.  But the FOSS community has clearly accepted the practice of reducing functionality without consideration of the impact upon home users.  That said, then speaking for myself and my family, given our particular use of computers (we spend far more time using applications than messing with the operating system), the impact is not so great that we can't compensate easily enough.

If you get too many items on the desktop, it is a simple task to just right-hand click on those items and move them to trash.

If you do an install of the older Ubuntu 11.04 version which gives you the capability to right-hand click and to add launcher/shortcuts to the desktop and then install the 12.04 version of Ubuntu that does not give you this capability and I will tell you every day of the week that I HIGHLY prefer the offerings of the older 11.04 version.

I think it is sort of stupid to eliminate this feature from Ubuntu and to force the users to access everything from a menu bar on the left side of the screen or by having to open a listing of the applications, etc. thru something called dash every time you need to run a program or to have to open browser every time you want to go to an often used website instead of having a link to that website directly located on the desktop !!!

Thanks.

---

### Post by S2UIRR3L on 2012-07-03
Heh... One of my computers was still running Jaunty Jackalope 9.04 up until December. I've never had one problem with it. I decided to give Lucid Lynx 10.04 a try and still never had a problem... If it weren't for a friend of mine persuading me to move on to Lucid, I'd STILL be on Jaunty.

Wanna know my biggest problem with Jaunty...? Having to click the little "X" in the notification that told me that my system was out of date and should be updated to the latest version. Other than that, never had a single problem, even when I was still using Jaunty back in December.

If you're interested in downloading a copy of an older version, and staying with that one like I did for the longest time... It's easy enough to just Google the words (for example) "Download Jaunty Jackalope" and you'll find the ISO in like the third or fourth result down from the top lol.

As for my self and Unity... I'm with the OP... I'm not very fond of the Unity DE and it's (in my opinion) very limited functionality, according to what I (and I'm sure a million others) are used to doing, and don't like the idea of having to learn this stuff again, like going back to kinder garden :-(

I'm staying with Lucid until one of three things happens (and I have a fantastic idea of which one it will most likely be):

#1 - They bring back something close to (or exactly like) the Gnome 2.
#2 - I keep using my Lucid until way past it's expiration date, it'll be fine.
#3 - I get up off my lazy azz and try LXDE and see if that works for me.

(99.9999999999 chance I'm sticking with #2)

One thing that I'm a thousand percent sure of... I'll never voluntarily go back to anything micro s#!t or wind blows as long as I can help it... Sure, there's my old xbox, but even that has Phoenix on it and plays MAME lmao. If I land a job that forces me to use ms, it won't be pretty, but it will pay the bills... Unlike cherry blossoms, money does NOT grow on trees.

-Leo in Massachusetts (us)

---

### Post by chocklet on 2012-07-03
wpshooter, sorry if I pressed your buttons.  Actually, I'm just as annoyed as many, but I've found that I can make no impact...  although I haven't tried insults :). 

> **wpshooter said:**
> 

I think it is sort of stupid to eliminate this feature from Ubuntu and to force the users to access everything from a menu bar on the left side of the screen or by having to open a listing of the applications, etc. thru something called dash every time you need to run a program or to have to open browser every time you want to go to an often used website instead of having a link to that website directly located on the desktop !!!


You might create a desktop launcher creator like this...

- right click the desktop
- select Create New Document > Empty Document
- edit the new document by entering this line:
```
gnome-desktop-item-edit --create-new ~/Desktop
```- rename the new document "Launcher Creator"
- using Nautilus, make the file executable

Now, whenever you want to create a launcher on the desktop, can you left click the "Launcher Creator" icon launcher and get the same laucher/shortcut creation capability that you had before?  (except that now you have to left click a launcher instead of right click anywhere)

---

### Post by wpshooter on 2012-07-03
> **chocklet said:**
> wpshooter, sorry if I pressed your buttons.  Actually, I'm just as annoyed as many, but I've found that I can make no impact...  although I haven't tried insults :). 



You might create a desktop launcher creator like this...

- right click the desktop
- select Create New Document > Empty Document
- edit the new document by entering this line:
```
gnome-desktop-item-edit --create-new ~/Desktop
```- rename the new document "Launcher Creator"
- using Nautilus, make the file executable

Now, whenever you want to create a launcher on the desktop, can you left click the "Launcher Creator" icon launcher and get the same laucher/shortcut creation capability that you had before?  (except that now you have to left click a launcher instead of right click anywhere)

Chocklet:

Thanks for those instructions.  I had already found those elsewhere.  But my question is, am I going to have to remember how to do this every time I the future that I decide to change/upgrade my OS or have to go hunting for this thread or these instructions elsewhere.   My opinion is that I am just a person that is using the OS to accomplish my daily task and I don't want to have to be researching how to do all of this, when this can very easily be a feature of Ubuntu from the get go, just like it always has been in the past.

Thanks.

---

### Post by kansasnoob on 2012-07-03
Going all the way back to your original question:

> Is there ANY Linux distribution(s) that still have the capability to create desktop shortcuts to applications and web links by simply right-hand clicking on the desktop as it was done so well in Ubuntu version 11.04 or am I looking down an empty well ???


Using the Gnome classic (no effects) DE as described here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

allows me to easily just left-click and drag any apps launcher to the Gnome classic desktop, with the exception of Libre office launchers, but ajgreeny posted about a work-around in post #22 and #24 there.

So please be specific about what desktop environment you wish to use and we'll try to figure things out better.

Someone needs to pursue this libreoffice bug in Launchpad but I just don't have time :(

Well, maybe I could make time if no one else will do it.

---

### Post by David Andersson on 2012-07-03
> **wpshooter said:**
> I installed this xfce from software center under 12.04 and then I logged out and switched to the xfce session.  I did NOT particularily like it, so I then went back into regular Ubuntu session under 12.04 and went back to software center and UNINSTALLED the xfce ...

Are you sure you didn't dismiss Xfce too quickly? It is very configurable. You can add and remove panels, change their position, shape, and transparency. You can move the placement of the Programs and Places menus (and everything else). During login you should have the option to choose between "xubuntu session" and "xfce session". They have the Programs menu organized differently, if you are picky about that. Of course there is the usual customization with themes, backgrounds, fonts, keyboard shortcuts, etc. All with easy to use settings tools.

---

### Post by mark bower on 2012-07-03
Not liking Unity, I played with 12.04 and installed Gnome Classic, which I believe worked as per previous post, ie, can rt-click from the drop down Applications menu and choose to add app icons to desktop.  Then I went a step further and installed Mate 1.2.  Definitely can add apps to desktop under Mate.  Mate seems to make for a very nice desktop with both a top and bottom of screen task bar(panel).  

I also tried and installed LinuxMint 13(my introduction to Mate). I believe apps in Mint can be moved to desktop, just too lazy here to drag out the laptop to verify - but I must be able to do it or I wouldn't like it.

For the time being, I am continuing with Ubu 10.10 on my PCs and LinuxMint on the laptop.  It is really handy to test options using the PC whereby I temporarily disable the on board HDs and temporarily use a 20GB HD to try the options.

---

### Post by wpshooter on 2012-07-03
> **David Andersson said:**
> Are you sure you didn't dismiss Xfce too quickly? It is very configurable. You can add and remove panels, change their position, shape, and transparency. You can move the placement of the Programs and Places menus (and everything else). During login you should have the option to choose between "xubuntu session" and "xfce session". They have the Programs menu organized differently, if you are picky about that. Of course there is the usual customization with themes, backgrounds, fonts, keyboard shortcuts, etc. All with easy to use settings tools.

Yes, I may have dismissed it too quickly.

I had sort of thought in the back of my mind, that I might go back and do a little bit more experimenting with it, so I left enough open hard drive space after MS$ & Ubuntu 11.04, to play around with it when I get a bit more time.

To my recall, the thing that I did not like about it was the just inordinately large number of (read that as overkill) items on the menus.  I would think that they can be pared down (items deleted from menus), so I may give that a try.

Thanks.

---

