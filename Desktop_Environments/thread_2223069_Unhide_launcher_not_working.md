---
title: "Unhide launcher not working"
date: 2014-05-09
forum: Desktop Environments
---

### Post by drm200 on 2014-05-09
I've installed 14.04 64bit on a Dell Vostro 3460 laptop. I've set the launcher to autohide with "reveal" set for the left side.  It will "hide" without problem ... But then I can not bring it back in a reliable way with the mouse.  If I move the mouse to the left side of the screen ... nothing happens.   If I "scratch" the mouse up/down on the left hand side of the monitor, the launcher *may* reveal itself sometimes.  I'm really frustrated that such a simple action does not work reliably ... and I'm forced to scratching the mouse around to *hope" that it might work after 4 or 5 seconds of this motion ... How can I get the launcher to reveal itself reliably with the mouse?

---

### Post by buzzingrobot on 2014-05-09
In System Settings, in the same section where you set the Launcher to autohode, there is an option to adjust its sensitivity to the mouse. Set it on "High" and see if that improves things.

---

### Post by drm200 on 2014-05-09
I should have stated originally that I tried both extremes of the sensitivity setting.   There was no impact at either extreme.  I could not see that the sensitivity setting had any impact whatsoever.

---

### Post by deadflowr on 2014-05-09
first, I would open "Displays" and run detect displays.
I would do this to make sure the display is centered correctly.
Once in a while, I've seen the display set not quite right.
This will reset it, most likely.

Second, Look in compizconfig-settings-manager.
(Install it if you don't have it)
click on the Ubuntu Unity Plugin.
There a section called, Launcher, and in it, there's a few extra options to set the hide launcher functions.
Like fine-tuning the pressure, and so forth.

See if either of those help.

---

### Post by drm200 on 2014-05-10
I tried the "detect" displays before ... and again after your suggestion.  I see no impact after doing this.

I installed [COLOR=#000000]compizconfig-settings-manager and set the launcher reveal pressure to "1" ....   The launcher unhide now works as expected when moving the mouse to the left screen border.

I'm very uncomfortable with this solution.  Installing compizconfig seems to automatically implement many other "fixes" upon installation ... And there is risk that I'm creating more unknown problems with its installation.  I would hope that Ubuntu would accept this problem as a "bug" and fix this problem that has been around thru various releases for years.

There are many strange problems in 14.04 .... like my mouse cursor flickering and disappearing ... the solution for this (for me) was to go into "All Settings/Displays"  where I would find not only the "built in display" but also an "unknown display.  Turning off the "unknown display" in all user accounts solved the mouse flicker problem. I have a laptop ... and have never attached it to any other screens ... so this "unknown display" is strange ... albeit not an uncommon Ubuntu problem.

I could suppose that the launcher "unhide" problem is somehow related to "unknown display" detection ... I don't know.

than.ks





[/COLOR]

---

### Post by buzzingrobot on 2014-05-10
> **drm200 said:**
> [COLOR=#000000]
There are many strange problems in 14.04 .... like my mouse cursor flickering and disappearing ... the solution for this (for me) was to go into "All Settings/Displays"  where I would find not only the "built in display" but also an "unknown display.  Turning off the "unknown display" in all user accounts solved the mouse flicker problem. I have a laptop ... and have never attached it to any other screens ... so this "unknown display" is strange ... albeit not an uncommon Ubuntu problem.
[/COLOR]
Does your laptop have the very common hybrid graphic support?  I.e. dual video capability, typically one embedded in the Intel CPU and another "discrete" AMD or Nvidia card?  If so, disabling one or the other in BIOS might be worth a try to see if it eliminates the machine's inability to identify the display correctly.

I recall seeing the same issue some time ago while trying to put Linux on a Macbook Pro, which also has hybrid video.

---

### Post by drm200 on 2014-05-10
This laptop has the built in Intel Graphics and also the Nvidia card.    This was a big problem during my initial install .... With the nvidia card enabled and the x.org driver the screen would lock up (not blackout ... just lock up) anytime that I would try to switch accounts or shut down without logging out.  I then installed the stable nvidia driver and it was even less stable ... 

So I then did this:

	sudo apt-get purge bumblebee*
	sudo apt-get install nvidia-prime
	sudo add-apt-repository ppa:nilarimogard/webupd8
	sudo apt-get update
	sudo apt-get install prime-indicator

This provided me with a tool to shut-off the nvidia hardware.  I'm now running only the intel graphics hardware and the x.org driver.  This configuration has been 100% stable except for the fact that I must always log-out of my account before shutting down (sometimes it will still lock up if I don't log-out first).  

However, even with the nvidia shut-off, the system still shows an "unidentified" display .... 

There is another problem I have not mentioned in that on two occasions the "unidentified" display has self "turned on".  I don't know what initiated this but it was apparent to me because the mouse flicker returned .... Turning the "unidentified display" off again in all user accounts solved the problem. ... This is only a nuisance in that it has only happened twice in about 3 weeks.

---

### Post by drm200 on 2014-05-10
I would also clarify that the Dell provided bios has no ability to select/enable/disable between the two graphic cpu's.  However the nvidia-prime app does the job.

---

