---
title: "So many problems..."
date: 2009-01-03
forum: General Help
---

### Post by jmetric on 2009-01-03
So far my experience with Intrepid is very disappointing and frustrating.  Perhaps the problems are self-inflicted, but that makes it no less unpleasant.

Where to start?  Setting desktop effects according to different posts have all led to the same conclusion: nothing happens.

The screen resolution is wrong, but changing it using the options available only led to a blank screen.

Problems with dpkg.  Always asked to manually run a check, always unresolved.

When I've run recovery mode, I get a failure message that dependentry >=4. No explanation beyond this.

Forget the plasma dashboard.  It seems to constantly unlock itself and stack any widgets on top of each other in the upper left hand corner of the desktop.

Programs that ran well before, such as nicotine plus, are now having problems.  In nicotine, it says that the share folders are corrupted and to rescan them.  When I do the program freezes.  But I am still able to use this folder in Amarok for example.  I tried removing and reinstalling nicotine, but this made no difference.

Now I am getting a message that the disk is full!  I've only been using Intrepid for 1 week on a new computer, and have saved hardly any files!

Any suggestions as to how to get things working would be tremendously welcome.

Thanks.

---

### Post by cariboo on 2009-01-03
> Where to start? Setting desktop effects according to different posts have all led to the same conclusion: nothing happens.

The screen resolution is wrong, but changing it using the options available only led to a blank screen.


These two are part of the same problem, have you install the restricted driver for your video card. Go to System-->Administration-->Hardware Drivers and enable the driver.

> Problems with dpkg. Always asked to manually run a check, always unresolved.

Usually running in a terminal:

```
sudo dpkg-reconfigure a
```

will solve any problems, if you are still having problems with broken packages, go to System-->Administration-->Synaptic Package Manger-->Edit-->Fix Broken Packages, this should repair the problems

> When I've run recovery mode, I get a failure message that dependentry >=4. No explanation beyond this.

When you start up in recovery mode you should come to a menu that allows you do fix X, drop to a root prompt, or continue

> Now I am getting a message that the disk is full! I've only been using Intrepid for 1 week on a new computer, and have saved hardly any files!

Just because you haven't saved any data doesn't mean that Ubuntu hasn't, all the updated and installed packages that you have downloaded are cached in /var/cache/apt/archives. TO clear up some space on your hard drive, in a terminal type:

```
sudo apt-get autoremove
```

the above command wil remove archived packages and dependencies that are no longer needed. To be on the safe side also run:

```
sudo apt-get clean
```

I can't answer any of your kubuntu questions as I refuse to use KDE, it is just to cluttered up.

Jim

---

### Post by jmetric on 2009-01-04
Caribou907,

Thanks for the help.  Sorry I didn't get back to you sooner, but I had to go out for awhile.

Your suggestions seem to have cleared up a a lot of the problems.  However, still some things I don't know how to handle.

When I run sudo apt-get remove I get this message: 

dpkg: error processing java-common (--configure):
 package java-common is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.

Any idea what I should do about this?

---

### Post by jmetric on 2009-01-04
sorry, i meant sudo apt-get autoremove

---

