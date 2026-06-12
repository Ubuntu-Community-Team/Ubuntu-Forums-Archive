---
title: "Ubuntu crashes when i start cairo dock"
date: 2009-07-05
forum: Desktop Environments
---

### Post by dark.generic on 2009-07-05
I have a compaq [HP Compaq nc800]("http://h18000.www1.hp.com/products/quickspecs/11786_div/11786_div.HTML") running a fresh installation of Jaunty.

If i start cairo dock the whole pc just freezes i can do nothing not even ctrl+alt+F1.

Any advise as to why this is happening?

---

### Post by fabounet on 2009-07-05
did you try to launch it with cairo-dock -c ?
your graphic drivers are maybe totally broken.

---

### Post by dark.generic on 2009-07-05
Couldnt find a cairo-dock -c command but did try cairo-dock -f with no luck.

So i assume no Cairo-dock for me then? what would be the next best? AWN?

---

### Post by Favux on 2009-07-05
Hi dark.generic,

In System>Preferences>Sessions click on Cairo Dock.  Click on Edit.  In the Command box change:
```
cairo-dock -o
```
to
```
cairo-dock -c
```

Hope this helps.

Edit:  Oops, in Jaunty it's System->Preferences->Startup Applications.  But you caught that.

---

### Post by dark.generic on 2009-07-06
Hey Favux
 
Ok so i managed to get Cairo Dock runnig but this is how it looks

[IMG]http://inlinethumb45.webshots.com/45036/2789287640105330670S500x500Q85.jpg[/IMG]

I suspect it might be drivers?

My card is
```
generic@tuxie:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```under System > Administration > Hardware Drivers the only drivers listed is the wifi drivers..

How do i install the drivers?

Thnx four your support thusfar

---

### Post by Favux on 2009-07-06
Hi dark.generic,

It's very hard to focus on your dock in that image.  Something kept distracting me.  Maybe the lighting?

You can play around configuring the applets and change the background transparency etc.

Given what you are saying it sounds like your video chipset may be one of the older ones dropped by ATI in the recent Catalysts.  Which is why there is no proprietary driver "fglrx" offered for install in Hardware Drivers.  That will take some research to find out for sure.

If so you'll want to find out which is the best Xorg ATI driver for you video chipset.  There's "radeon" and "radeonhd" I think.  You'll also want to see if there are tips to best configure the driver for you chipset.

I think I've got some bookmarks somewhere.  I'll take a look.

---

### Post by Favux on 2009-07-06
Hi dark.generic,

As promised:

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

[http://ubuntuforums.org/showpost.php?p=7130846&postcount=14](http://ubuntuforums.org/showpost.php?p=7130846&postcount=14)

[http://blogs.computerworld.com/the_ubuntu_and_ati_blues](http://blogs.computerworld.com/the_ubuntu_and_ati_blues)

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

[http://www.linux-magazine.com/Online/News/Proprietary-Driver-for-Ubuntu-9.04-Fglrx-for-X-Server-1.6](http://www.linux-magazine.com/Online/News/Proprietary-Driver-for-Ubuntu-9.04-Fglrx-for-X-Server-1.6)

[https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html](https://lists.ubuntu.com/archives/ubuntu-x/2009-March/000442.html)

[http://ubuntuforums.org/showthread.php?t=1100160](http://ubuntuforums.org/showthread.php?t=1100160)

Hopefully this will save you some time and once you've looked this over you'll know how to proceed.

Good luck!

---

### Post by dark.generic on 2009-07-06
Thanx allot guys...

looks like support for my card has been dropped...

I just installed the latest version of Cairo :oops: and it now works with the -c command

Everything is up and running now..

thanx again for the inputs

---

### Post by Favux on 2009-07-06
Hi dark.generic,

Your welcome.

Don't be too discouraged.  While ATI may have stopped supporting older cards with their proprietary drivers Xorg hasn't.  And ATI finally released a lot of information recently.  So look for rapid improvement in the Xorg OSS drivers like "radeon".

---

