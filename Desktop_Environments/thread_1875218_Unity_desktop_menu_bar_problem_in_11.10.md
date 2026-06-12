---
title: "Unity desktop menu bar problem in 11.10"
date: 2011-11-04
forum: Desktop Environments
---

### Post by RobertSwipe on 2011-11-04
I've lost the global menu bar from my desktop, so applications like Thunderbird no longer have any way of accessing the menu now that it's been integrated with the (ridiculous) global menu.

I would use Gnome Shell, but the nvidia drivers don't work with my dual monitor setup, so I've reverted to the rather flakey nouveau drivers (2D only and loads of screen garbling as windows are moved around).

I've attached a screenshot so you can see how the base desktop looks - the "Dash home" button sits right at the top edge of the display, and the top panel bar is gone. There is a top panel bar on the second monitor, so I can still log out (phew!), but no menus appear in this one, so I'm stuck if I want to do anything which requires a menu action. I've used the suggestions for disabling the global menu, which has helped for some apps, but the 11.10 version of Thunderbird has obviously integrated its menu sufficiently that it no longer appears.

(My disappointment with 11.10 has been noted elsewhere in this site, and once I can get a stable release with stable drivers I shall be moving away from Unity - it's not for me!)

In the meantime, any help greatly appreciated!

---

### Post by RobertSwipe on 2011-11-04
A slight update on this: If the second monitor is removed and my session restarted, the panel is restored on the primary display.

Switch on the second monitor, log out/in and the panel disappears.

Curiouser and curiouser....

---

### Post by dieutan on 2011-11-05
Have the same problem. Unity Bar gone after un-success install fglrx for ATI Firepro x5600.  Don't know how to get Unity Dash bar back, the desk top boot up not completely finish. Cannot run any application except "file manager". the log out/in, shut down, and the panel disappears

---

### Post by LMendy on 2011-11-06
I have been experiencing this problem intermittently as well. Sometimes the top panel and Unity just disappear! I'm in Ubuntu 11.10

---

### Post by psykotic25b on 2011-11-06
What type of computer are you using?  I've seen your posts describe your graphics cards/drivers.  Also, the OP said there is a bar on the second screen, and when he takes that second screen off and reloads everything works fine.  Could it possibly be an issue within your display settings?  I'm new to Ubuntu but I'm assuming the display selections work similar to W7, using a primary and a secondary.  Am I correct in assuming this?

---

### Post by washington luiz on 2011-11-06
Got the same problem here. All of a sudden all menu disappeared and now I can only access nautilus from desktop. Need to open a terminal with ctrl alt t and run commands in order to use other softwares ... Wtf .. It really doesnt make any sense to build such a beautiful interface and lauch it with thousands of bugs. And say everywhere its stable .. Cause its really not.

---

### Post by larrypg on 2011-11-07
I am not positive which you have but if you have global menu and do not want it you can uninstall indicator-appmenu and vice-versa if you want it

---

### Post by BillyBoa on 2011-11-07
Maybe you have to check here:
[http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by RobertSwipe on 2011-11-09
> **psykotic25b said:**
> What type of computer are you using?  I've seen your posts describe your graphics cards/drivers.  Also, the OP said there is a bar on the second screen, and when he takes that second screen off and reloads everything works fine.  Could it possibly be an issue within your display settings?  I'm new to Ubuntu but I'm assuming the display selections work similar to W7, using a primary and a secondary.  Am I correct in assuming this?

Sorry for late reply. It's a Dell XPS M1210, using nvidia Geforce Go 7400.

You're correct that display selections are similar to those of W7, with primary/secondary selections (from the Dash home, search for "display" and you'll find the application which is familiar to W7 users).

The nouveau drivers allow me to use Unity, and on a single monitor (the laptop's own), it's fairly stable. As soon as the second is connected, the nouveau drivers become less stable - dragging windows around often leaves trails which can be cleared by using one window as an eraser, or by making one app run in full screen.

Several apps open in full screen, with no option to change this behaviour (e.g. creating a new mail in Thunderbird, Firefox), and when the top panel is absent, it's no longer possible to select many of the functions.

---

### Post by RobertSwipe on 2011-11-09
> **larrypg said:**
> I am not positive which you have but if you have global menu and do not want it you can uninstall indicator-appmenu and vice-versa if you want it

This doesn't seem to restore window menus for some of the supplied apps - Thunderbird and Firefox for instance.

I'd like a formal and properly supported feature in a Unity Control Panel that allows me to choose. As it is, the removal of two packages is a bit of a kludge which may not be possible in future releases.

---

### Post by RobertSwipe on 2011-11-09
> **BillyBoa said:**
> Maybe you have to check here:
[http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

Thanks - I'll give this a whirl!

---

### Post by cduplantis on 2012-01-09
Same problem here. Running on AMD64 with Nvidia GeForce 8800 GTS and NVidia proprietary driver version 280.13.

Linux <hostname> 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

I have a dual-monitor setup like some of the other posters. My global menu (I think that's the right term for it - the menu bar at the top that displays menu items specific to the app) goes away from the main (left-most display).

The thing I notice is that if I drag the app in question to the right-most display, the menu shows up there. So the menu doesn't disappear, it just ends up anchored to the right display instead of the left display, which I feel is my main display as it's larger and I'm left-to-right-centric, culturally.

I also have noticed that sometimes my initial desktop login is on the right display and sometimes on the left while the other display remains dark until login completes. This is not really a problem, though I would prefer the login to always be on the left-most display. However, I do wonder if there's a correlation between the display nominated for the login and the display on which the menu bar ends up setting up shop.

---

### Post by Pilot6 on 2012-01-09
I had similar problems with dual x screen with nvidia. It will be fixed soon in unity. I built one from trunk today and all problews gone.
It was cused by sending wrong parameters to nautilus, which could not correctly define workspace. So panel went upper than visible screen, or not drawn at all.
In some cases the panel is there but windows open with titles under panel. It may happen randomly. All fixed in trunk.

---

### Post by Maineac54 on 2012-01-25
I'm not sure what Trunk is, but I assume it's updates/fixes in the works.  I don't know when this trunk will be out, but I only got this problem a few days ago following a kernel update (default updates from Ubuntu) which caused me to reboot.

I now have no global menu on my right hand monitor, which is my laptop.  Not only that, the screen size goes about 4 mm above the edge of the monitor.  So if I make an application full screen on that monitor I have to use Ctrl-F4 to close it and cannot move it or resize it.

I have installed 2 sets of updates since the problem began.  One set yesterday had 93 Updates, but still no fix to this bug.

Is there any ETA on when a fix for this will be distributed?

Other than that, I vote for Unity.  And I think the global menu is a good idea as it saves real estate... when it works right.

---

### Post by Geezanansa on 2012-03-26
I too am using a nvidia graphics card and amd64 cpu with 11.10 and having dual monitor probs as listed by users in this thread.  I do not have money but do have time so have been seeing it as a challenge to get this ironed out but my knowledge is very basic....
The more i learn the less i understand:lolflag:
This has been problematic since 11.10's release and it is good to hear a fix; for us nvidia and amd64 users, is on the way.

> I now have no global menu on my right hand monitor, which is my laptop.   Not only that, the screen size goes about 4 mm above the edge of the  monitor.  So if I make an application full screen on that monitor I have  to use Ctrl-F4 to close it and cannot move it or resize it.
Keyboard shortcuts are an important tool to have at hand.
 i.e. alt+F9 will minimize,
 Alt+TAB will switch windows/open apps,
 Alt+F5 will unmaximise
Alt+left mouse click will allow you to move window(even to your other monitor:lolflag: when it worky)

I have found system restart brings back the menu bar for apps etc

---

