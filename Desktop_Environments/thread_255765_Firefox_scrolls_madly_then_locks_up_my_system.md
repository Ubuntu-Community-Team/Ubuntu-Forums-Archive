---
title: "Firefox scrolls madly then locks up my system"
date: 2006-09-11
forum: Desktop Environments
---

### Post by DarkStarDeity on 2006-09-11
This has just started happening to me in the last few days/week or so. One of two weirdnesses (sometimes both) happen in Firefox - 1) the "find in this page" bar pops up at the bottom of the window, takes focus and can't be shut; 2) pages just start scrolling madly, especially yahoo webmail, sometimes if I have other pages open with drop-down menus, I can't select items in the menu as it closes as soon as I open it. It often (always?) occurs when going back to a Firefox window after doing something else. Then my system almost freezes (the mouse still responds but windows responds extremely slowly to mouseclicks, or sometimes not at all). I have a system monitor applet docked on one of my panels, and it maxes out at 100% CPU usage at this point. Sometimes I am able to open the system monitor to kill the Firefox process, other times I can't. Sometimes I need to restart the computer, sometimes I can do this properly, other times I need to hard reboot. This has been occuring a couple of times a day now. 

There is one other process that might have something to do with this - juk. It may be a coincidence, but this only started happening after I started using juk, and seems to mostly happen after I've had juk open for a long time, or have just closed it after having it open for some time. My juk is using aKode for its sound as I couldn't get it to work with arts and it didn't offer gstreamer as an option (despite the blurb saying it did). 

Has anyone else had a similar problem or have any idea of what might be causing this?

Edit: It seems like it might be the same as problems in [this thread]("http://ubuntuforums.org/showthread.php?t=193283"), but that thread is 30-something pages long :( and skimming through it I can't see any resolution, although lots of conjecture about xorg, alsa, drivers, and god-knows what else and suggestions of poking at things I'm really not comfortable poking at :(

---

### Post by szf on 2006-09-12
Are the 'use autoscrolling' or 'smooth scrolling' options checked in Firefox?
Go to menubar --> Edit --> Preferences --> Advanced --> General tab.

I think I checked the 'smooth scrolling' in pre-1.0.4 Firefox and she became unstable immediately...

---

### Post by DarkStarDeity on 2006-09-12
Neither of those options are set. After skimming through the thread I linked, I think I'm seeing a varaint of the same problem (other people are mentioning multiple refreshes) and it looks like it's not actually Firefox but Xorg that's the culprit, but as far as I can see, there is no resolution as yet.

---

