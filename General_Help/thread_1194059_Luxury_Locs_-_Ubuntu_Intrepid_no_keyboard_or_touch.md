---
title: "Luxury Locs - Ubuntu Intrepid no keyboard or touchpad after suspend"
date: 2009-06-22
forum: General Help
---

### Post by stockbrain on 2009-06-22
I know this topic has come up many times, but I've done some digging and I think I've narrowed down the problem and have an idea where to begin, but my scripting skills aren't up to the task. But first, some background.

I recently got a Compaq Evo N1000v laptop and the first thing I did was install Ubuntu. Almost everything works properly and I'm very pleased, but I'd like to fix the remaining issues it has to make it a perfect OS - specifically, I have issues with WPA wireless and suspend/hibernate. I'll save the wireless for another thread.

At first, whenever I tried to suspend or hibernate I'd get a black terminal screen with a flashing cursor and it would take a hard reset to get the computer back to a working state. I tried a few things mentioned in the forums - I made a few minor additions to xorg.conf and acpi-support and installed Ubuntu Tweak and checked the box to stop network manager on suspend or resume, but nothing worked. I finally disconnected my wireless card - a Dell 1450 USB card - and to my surprise hibernate and suspend both worked, at least when it the computer went down.

The next problem happened on resume. I can resume (thaw) from hibernate with no problems, but when I resume from suspend, my touchpad and keyboard don't work and I can't unlock the screen. I have to do a hard reset to get the computer back up and running.

I checked the pm-suspend.log file after both a successful hibernate and an unsuccessful suspend and noticed that the 99video script was throwing an error when resuming from suspend but not when thawing from hibernate, so I know the problem is somewhere in that script or with parameters sent to that script from hal. I haven't troubleshooted the wireless card suspend issue, but I'm less concerned with that as I can just unplug it for now.

I'll post some log files in a little while (I'm not on the laptop now) but if anyone has any suggestions based on what I already mentioned please let me know. I'm not a bad programmer (I write .Net stuff for a living) but I have little to no experience with bash scripts, although I'm willing to help.

Luxury Locs

---

