---
title: "gvfsd-trash and Nautilus causing 100% cpu usage, unusable system"
date: 2010-06-17
forum: Desktop Environments
---

### Post by turqoisehex on 2010-06-17
I have a 2 week old install of Lucid, and for no reason that I've been able to discern, Nautilus has broken creating an unusable system. I've done all recent updates, including the latest version of Nautilus in the repositories.

The behavior is similar to an ongoing bug that's been present since at least 9.04 ([https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/325973?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/325973?comments=all)) ([https://bugzilla.gnome.org/show_bug.cgi?id=571417#c31](https://bugzilla.gnome.org/show_bug.cgi?id=571417#c31))

Except that /apps/nautilus/preferences/show_desktop and /apps/nautilus/preferences/exit_with_last_window are both true. In the above bug, setting them to true is supposed to fix the problem. 

Back story:
Immediately before everything broke, I had been using VirtualBox 3.2. I deleted a disk image from the &#8220;known media&#8221; and rebooted. When I came back into Ubuntu, the purple screen with &#8220;ubuntu&#8221; didn't disappear, the working circle would appear whenever I moused over the desktop. I couldn't right click on the desktop, and infinite &#8220;starting file manager&#8221; windows were opening. In system monitor, gvfsd-trash was taking up 80-90% of cpu, and Nautilus was 10-20%. my semi-transparent terminal window always shows the desktop background instead of what's behind it. 

What I've tried:
[LIST]
[*]EDIT: I've created a new user, when logged in as that user *everything is perfectly normal*, **can anyone tell me how to reset my user settings?**
[*]failsafe gnome &#8211; stops the windows from popping up, show_desktop works (I have icons and can right click) cpu usage is normal. If I minimize windows they disappear. EDIT: it turns out most of my panel applets, such as window list, had disappeared. I re-added them and now I can switch windows that way, though alt-tab still has no effect.
[*]reinstall Nautilus from synaptic (no effect)
[*]Switching from metacity to compiz, and from GTKWM to Emerald (no effect)
[*]switching  show_desktop and  exit_with_last_window in gconfedit (no effect)
[*]swearing and pulling my hair out (no effect)
[/LIST]

The other idea I've had is to delete the .nautilus directory which might (hopefully) reset it's settings. It works for wine, but in the case of nautilus I'm afraid it would just break my system.

**[SIZE="4"]Any and all suggestions are very much appreciated.[/SIZE]**:confused:

Side note: I've been raving about how far Ubuntu has come since I first used 6.06, and how stable it's become. I sincerely hope this is something I screwed up, and not a bug in Lucid.

---

### Post by turqoisehex on 2010-06-18
Bumpdate:

I tried:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .nautilus
```

and rebooted. My settings all appear to be default, but the problem persists. 

I'd rather not do a clean install, but that seems to be the direction I'm heading in. Any suggestions?

---

### Post by nxumdon on 2010-06-23
I can confirm I'm having the exact same issues with this gvfsd-trash process taking about 80% CPU and a nautilus process listed as (defunct) if I watch top long enough...it will spawn a new nautilus and then it goes defunct.  This was a brand new install of 10.04 and it was working totally fine until I installed XBMC from ppa and rebooted.  Upon reboot, all my auto mounted ntfs drives were not showing up and gvfsd-trash was wacky!

I've repeated the exact same process twice trying to get this new system built....nothing more was done than the following, in order;

-install 10.04 desktop
-update and reboot
-install restricted nvidia drivers and setup hdtv as second display and reboot to kick x over...
-installed docky unstable, all still fine
-installed gnome-do, still good
-installed nautilus elementary and rebooted, still ok!
-installed xbmc and rebooted, BARRRHHHGGG!! Broken!
-remove and purge xbmc, reboot and still broken!

Ok, I'm taking a break from this! 

J

---

### Post by Krikke_wl on 2010-09-23
Hi,

since yesterday my system got unusable too. I installed the latest updates, which required me to reboot. after that, my system never got back up... It comes up and then gvfsd-* processes start hogging the cpu for 9999%. I've got XBMC installed too, on a Lucid Lynx. Anyone else got this problem or even a fix?

regards and thanks in advance

---

### Post by Sealbhach on 2010-09-26
I'm getting this issue now in Lucid, if I delete anything from trash (empty trash) the CPU slowly goes up to 100%, caused by gvfsd-trash.

I don't recall updating anything to have caused this.:confused:
.

---

### Post by Krikke_wl on 2010-09-29
well apparently my swap wasn't mounted. so I double-checked my /etc/fstab, rebooted and for now everything seems OK...

---

### Post by nxumdon on 2010-10-04
Just installed a brand new ubuntu 10.04 system, all was fine until I installed nautilus elementary...as soon as I did, gvfsd went to >80% CPU...as soon as I ppa-purged it, back to normal.  So it's clearly some issue with elementary.  Dang!

---

### Post by starrygordon on 2010-10-16
So, is this solved or not?  I can quiesce gvfsd by rebooting, but once something sets it off, isn't it going to eat all memory again?

---

### Post by notjingo on 2010-12-20
I am having the same exact issue. After logging in Nautilus spawns thousands of instances for a couple minutes. They fill the panel and then finally disappear. After that periodically I'll see a "Starting File Manager" appear in the panel, then disappear. My desktop icons are gone, but funny enough Nautilus occasionally will still work and I am able to browse files. 

The top three processes running by memory usage are gvfsd-trash, dbus-daemon, and nautilus.
Gvfsd-trash is taking up almost 100% of system resources. Also my swap reports 0% usage, and I guess right now is not automounting. I have mounted the swap and the problem persists. 

What is going on???

I am using gnome 1.2.28+1ubuntu3 and Nautilus 1:2.31.1-ubuntu2~ppa92

This problem seems to have come out of nowhere but I'm not sure if it started occurring after an update. I've read all the threads I can on this but no solutions have worked.

I have uninstalled Ubuntu One client, as per this thread 
[http://www.browse24h.com/index.php?q...Y2MDM0Mg%3D%3D](http://www.browse24h.com/index.php?q...Y2MDM0Mg%3D%3D)
Did not help.

I have made the following changes to /usr/share/applications/nautilus.desktop

X-GNOME-AutoRestart=false # changed from =true
AutostartCondition=GNOME /apps/nautilus/preferences/show_desktop # added this line

As per this thread:
([http://ubuntuforums.org/showthread.p...+spawns&page=2](http://ubuntuforums.org/showthread.p...+spawns&page=2))
Also did not help.

I do not have the line mentioned at the end of this thread either (in the xorg.conf)
[https://bbs.archlinux.org/viewtopic.php?id=69282](https://bbs.archlinux.org/viewtopic.php?id=69282)

This thread describes the Gvfsd-trash issue
[https://bugzilla.gnome.org/show_bug.cgi?id=553776](https://bugzilla.gnome.org/show_bug.cgi?id=553776)

Please help!

I have been able to close all the Nautilus spawns on login by using killall nautilus, and after that the system seems to be back to normal. But when I restart or login again, the madness starts over. 

Has anyone figured out the definite cause of these issues?

Does it have anything to do with the "errors=remount-ro" option set in my fstab?

---

