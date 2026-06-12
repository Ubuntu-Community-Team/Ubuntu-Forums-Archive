---
title: "Hibernate/Suspend missing from new desktop menu"
date: 2010-05-02
forum: Desktop Environments
---

### Post by fivebells on 2010-05-02
I recently upgraded to lynx from karmic on my Lenovo T61 laptop.  I had to switch from gdm to xdm to get X working smoothly.  No big deal.   In the menu under the power-button icon on the right-hand side of the top panel, I no longer have suspend or hibernate options.  pm-suspend and pm-suspend-hybrid both seem to work from the commandline, which is adequate.  However, is there a way to get those menu options back?  (Or have they moved somewhere else?)

---

### Post by okplayer02 on 2010-05-05
thank you i am having the same issue with fresh install of lucid. I do have all the acpi tools intalled on my dell gx270 Pentium 4 machine. So any help be appreciated



SOLVED

I went into my bios for my machine and changed the settings on power management and after restart the suspend button popped up now.

---

### Post by captwiggum on 2010-05-24
Same issue here. On 10.04 pm-suspend works fine from cmd line, but the suspend option missing from power menu. On a previous boot it was there. So there must be some criteria or event that decides whether it goes into the menu. Any ideas appreciated.

---

### Post by captwiggum on 2010-05-24
Things of note between the time suspend was present, and now: I changed from a swap file to a swap partition. But the new swap is definitely active, and visible in /proc/swaps. I verified that gnome-power-manager is running. Also, I notice when suspend was present in the menu, there was an "on battery" tab in system --> preferences --> power management. When suspend is missing from the menu, the "on battery" tab is also missing from the power management settings. What should I check in addition to gnome-power-manager? Or specifically, what procs or files affect the "on battery" tab of the power management settings?

---

### Post by captwiggum on 2010-05-25
This issue is being tracked in the following two bugs. These are all related. If gnome-power-manager has a problem, then three things happen: 1) battery icon does not display, 2) "on battery" tab does not display in system --> preferences --> power management, 3) suspend is missing from power-off menu.

"gnome-power-manager doesn't show icon as non-root user"
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/532005](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/532005)

"battery icon is not shown"
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/529911](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/529911)

The root cause of the gnome-power-manager trouble maybe different for different users. For me after running "killall gnome-power-manager && gnome-power-manager --verbose  2>&1 | tee gpm.log" I see that the issue is in devkit-power-gobject**:**

(gnome-power-manager:9264): devkit-power-gobject-WARNING **: Couldn't enumerate devices: Message did not receive a reply (timeout by message bus)

All I can do is follow the bugs and watch for the solution.

---

### Post by captwiggum on 2010-06-07
This topic is a duplicate of this thread:
[http://ubuntuforums.org/showthread.php?p=9357791](http://ubuntuforums.org/showthread.php?p=9357791)
Please post follow-ups in the above linked topic.

---

### Post by captwiggum on 2010-06-08
Yesterday, 7-Jun-2010, I ran update manager, which updated the kernel and a couple dozen other pkgs. 
I have been doing this about every five days hoping for a cure.
This time it solved the issue for me. Looks like they closed some of the related bugs. Yahoooo!

---

### Post by gar37bic on 2010-10-26
Following the first reboot for a couple of weeks, this problem has appeared for me.  It's a Lenovo z61m laptop.  I tried captwiggum's tactic to kill and restart gnome-power-manager, and the resulting log is attached.

The restart hung for quite a long time after line 179:
```
TI:07:41:01	TH:0x85166d8	FI:gpm-engine.c	FN:gpm_engine_get_warning_time,158
 - time zero, falling back to percentage for battery
```


Using pm-suspend from the command line works (but doesn't lock the screen).

I'm also running Compiz with the desktop cube.

---

### Post by gar37bic on 2010-10-26
I would just add that the only options that I get from the 'Log Out' button are 'Log Out' and 'Switch User' - I don't even have power off.

I forgot to mention I'm talking about the 'Log Out' button in Cairo-dock.  I will go look up problems with Cairo as well.

Reboot did not change anything.

---

### Post by gar37bic on 2010-10-26
Interesting.  I have a regular Gnome panel as well, and I added the Shutdown button to that panel.  That one comes up correctly, with all four buttons.

So this is apparently something to do with Cairo or its Logout plug-in.  I tried removing it and adding it back in, but no change.

This does not seem to be a Gnome-power-manager or gnome-panel problem.  I will pursue this in the Cairo direction.

---

