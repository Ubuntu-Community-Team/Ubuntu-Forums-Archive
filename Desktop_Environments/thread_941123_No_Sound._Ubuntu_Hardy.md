---
title: "No Sound. Ubuntu Hardy"
date: 2008-10-07
forum: Desktop Environments
---

### Post by wiggles-man on 2008-10-07
Ok, so i recently(3 days ago) installed Hardy. Only problem is, i only have limited sound. I dont get any sound from any of the applications inside of linux, but i do get sound when im usuing swine to play steam games. Any help would be appreciated. Also, im running a M2N-Sli Deluxe mobo, if that helps at all 	:???:

---

### Post by wiggles-man on 2008-10-07
Ok, update. I have found that asus comes with linux driver support, but i just dont know which driver to install. There are 5 chipsets and im not sure which one is mine, how could i find out? Also, to install the drivers, they are .rpm files. But it gives me the command:

rpm -ivh nv-rhas3.5-2.4.21-32.EL.x86_64.rpm 

So how could i download them? Because from what ive found out, ubuntu cant use these files or the command. Any ideas?

---

### Post by Cato2 on 2008-10-08
Those driver files will be painful to install in Ubuntu, and aren't needed.

See [http://www.backports.ubuntuforums.org/showthread.php?t=616845](http://www.backports.ubuntuforums.org/showthread.php?t=616845) for some tips on how to identify your sound hardware to determine which driver (module) to load.  Ubuntu is very likely to already support your hardware, it's just not automatically loading the right driver so you have to tell it what to load.

Also, googling for name of your motherboard plus 'ubuntu sound' may be useful:  [http://www.google.com/search?hl=en&client=opera&rls=en&hs=njm&q=m2n-sli+deluxe+sound+ubuntu&btnG=Search](http://www.google.com/search?hl=en&client=opera&rls=en&hs=njm&q=m2n-sli+deluxe+sound+ubuntu&btnG=Search) - you may find an active Ubuntuforums thread there that you can join.  If you don't find anything, replace ubuntu with Linux and try again - the module name will be same between other variants like SuSE, Fedora, etc and Ubuntu, and may help.

One other idea: explore the volume control/mixer tool, and go into Prefs etc to enable ALL the options - quite often sound is working but not configured properly i.e. some channels are muted.

---

