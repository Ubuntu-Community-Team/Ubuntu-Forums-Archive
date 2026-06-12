---
title: "Dell Latitude 2100 Question on WiFi feature"
date: 2010-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oldpath on 2010-02-26
I just bought the 2100 netbook from Dell Outlet loaded with Ubuntu 9.04.  The question: Does this netbook normally come with WiFi enabled?  How do I go about checking this out?  This is all new to me.

Thx

---

### Post by bobcollard on 2010-02-27
> **oldpath said:**
> I just bought the 2100 netbook from Dell Outlet loaded with Ubuntu 9.04.  The question: Does this netbook normally come with WiFi enabled?  How do I go about checking this out?  This is all new to me.

Thx
It may not be the computer that is not connected but your lack of drivers, etc.  Try this Link:
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by oldpath on 2010-02-27
Thanks Bob,
   I am confused on one thing....among many....are Broadcom wireless and Wi
Fi the same thing?  Use the same drivers...and etc?   How little I know.  But I think you got me headed in the right direction.  I will unplug the network cable from my desktop and boot up the 2100 with network cable and see if I can get it to 'connect'.

Thanks

srd

---

### Post by bobcollard on 2010-02-27
> **oldpath said:**
> Thanks Bob,
   I am confused on one thing....among many....are Broadcom wireless and Wi
Fi the same thing?  Use the same drivers...and etc?   How little I know.  But I think you got me headed in the right direction.  I will unplug the network cable from my desktop and boot up the 2100 with network cable and see if I can get it to 'connect'.

Thanks

srd
Most of the Dell computers have Broadcom wireless cards inside, it's a brand name.  If you google it you will find all kinds of links and even updates.  For me, it was a shot in the dark the first time, reading forum after forum and I quit giving individual advice preferring to give out links instead.  Even my signature is wrong at present, I'm using the Fluxbox version of Linux Mint 8, it is still a Ubuntu based distribution and I have tried over thirty distributions to find one that works for me.  I'm a Distro Hopper, I even had a look at the recent Ubuntu Lucid Lynx, waiting on the final to make an informed decision.  Incidently, if this solved your problem then Edit your first entry and in the Title add [Solved] so others may benefit.

---

### Post by oldpath on 2010-02-27
Bob,
  I followed the link. One poster advised running update manager first which did.....305 megs of updates were needed to bring the netbook up to date.  Then I used apt-get to find the drivers and install them.  Until I take this netbook to a WiFi spot I will not know if it works or not.  One curious observation is that the wireless light is on all time when the netbook is on.  Also, when I did the apt-get search by entering BCM in the search field the results did not look like the ones in your ref. link.  But it did relate to Broadcom drivers. I guess I can undo this change if it does not work.  Maybe I should have tried the WiFi feature first after all the updates before doing this BCM install.  But too late now.
Anyway,  Many thanks'

Oldpath

---

### Post by oldpath on 2010-02-27
Bob,
  I am not a distro hopper....yet, but I am interested in the Flux-Box version of Mint 8.  Wouldn't that be a better fit for my 2100 netbook?  I ordered the extra one gig memory card and the bigger six cell battery versus the 3 cell battery it came with. It came with an 80 gig hard drive.  I hope to take this computer with me to Turkey to use for email while on tour.  Also to off load photos from camera memory cards.  I hope to get many years use out this little netbook.  It looks well made and other than a hard drive failure what else could wear out?  It might last for ages.  

Thanks

Oldpath

---

### Post by bobcollard on 2010-02-27
> **oldpath said:**
> Bob,
  I am not a distro hopper....yet, but I am interested in the Flux-Box version of Mint 8.  Wouldn't that be a better fit for my 2100 netbook?  I ordered the extra one gig memory card and the bigger six cell battery versus the 3 cell battery it came with. It came with an 80 gig hard drive.  I hope to take this computer with me to Turkey to use for email while on tour.  Also to off load photos from camera memory cards.  I hope to get many years use out this little netbook.  It looks well made and other than a hard drive failure what else could wear out?  It might last for ages.  

Thanks

Oldpath
If you want light and fast without changing too much, try Xubuntu 9.10, it's close to gnome desktop working from a menu in the task bar.  Fluxbox's menu is briefer and the number of applications tuned to it's desktop.  You access it by right clicking the desktop itself.  There are fewer settings to play with and it is not easy to  adapt to unless you are just wanting something quick and easy.  Few themes, no changing cursor and some things just don't work in it.  It is as close to one application per usage as you can get, and that is limiting.  I have very little need for "Pretty"  I use the Command line all the time.  You have to set your own wallpaper one at a time.  Not trying to discourage you but make an informed decision.  Try a Live CD first, you'll see what I mean.
P.S. In Synaptic Package Manager type Radar in the search bar.  Install WIFI RADAR, it will tell you if you are near a WIFI open channel.  Once installed find it in your Network Menu.  Good luck.

---

### Post by oldpath on 2010-02-27
Bob,
  Thanks for the hint on using Radar for finding hot spots.

No luck with wireless after installing the fix.  I now wonder if I should have checked for wireless after installing all the updates.  I was blown away by the 300 megs of undates.  Made me think that Dell must have reinstalled a minimal Ubuntu 9.04 if that is possible.  I will go back and look at the other site to see if I missed something.  I noticed the BCM install removed some newer software.  Now, if I try to remove it how can I get my original install with updates back to the prior state.  That should be interesting.  I am shakey with command line work, but I understand how it is so much better than some other ways.  I am 68 years old and not a tech minded person, but I am always game to try something new.  But my learning potential is not what it once was....and rapidly getting worse.

Thanks for the advice on Flux Box.  I'll stay with what I've got.  Since I have 9.04 on both the desktop and the netbook....better to stay that way.

Oldpath

---

### Post by superm1 on 2010-02-27
> **oldpath said:**
> I just bought the 2100 netbook from Dell Outlet loaded with Ubuntu 9.04.  The question: Does this netbook normally come with WiFi enabled?  How do I go about checking this out?  This is all new to me.

Thx

Yes, if it's not working, try pressing the key combination to enable it (generally FN-F2 I think).

You'll see the light on the bottom corner light up when it's enabled.

---

### Post by bobcollard on 2010-02-27
> **oldpath said:**
> Bob,
  .  I am 68 years old and not a tech minded person, but I am always game to try something new.  But my learning potential is not what it once was....and rapidly getting worse.

Thanks for the advice on Flux Box.  I'll stay with what I've got.  Since I have 9.04 on both the desktop and the netbook....better to stay that way.

Oldpath
I'm 65 and use the computer to keep my mind sharp.  Took a course 20 years ago in computer repair and done stuff ever since.  Tech minded?  Nah, just ambitious and love to learn new stuff.   As for learning potential, take a look at the kids with their electronic games and learn from them.  If you die you restart the game.  If your computer crashes you install a new system and start over, just remember to back up your important files that are irreplaceable.

---

### Post by oldpath on 2010-02-27
I am closing this thread, but not solved.  Will take the netbook into a shop and have techicians firgure it out while I watch.

Thanks for everyone's  help.

Oldpath

---

### Post by bobcollard on 2010-12-25
> **coleyladik said:**
> Thanks for your explanation! Now I got it.

Great, sorry if everything sounded so cryptic, but, I'm glad you got it.

---

