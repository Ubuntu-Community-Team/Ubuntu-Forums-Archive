---
title: "Monitor turning off after 10 minutes"
date: 2010-03-12
forum: Desktop Environments
---

### Post by pcfixitguy on 2010-03-12
I have three identical computers running Ubuntu 9.10, all recently updated, and all three of them are turning their monitors off after 10 minutes of inactivity.  I have tried the following:

*Gone into System/Preferences/Screensaver and disabled the screensaver

*Gone into System/Preferences/Power Management and set all "put computer sleep" settings to Never.

*Gone into gconf-editor /apps/gnome-power-manager/timeout and set all values to 0

*Run "xset -dmps" and "xset s noblank" from a terminal, created a script to run them at startup, and created a crontab entry to run them every 5 minutes.

*Disabled acpi-support service

*Disabled laptop-mode service

When I do a grep -i DPMS /var/log/Xorg.0.log, I get the following:
(II) Loading extension DPMS
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): DPMS enabled
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display

But, when I do a xset q, I get the following:
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled

How do I permanently stop my monitors from turning off.  These are kiosk type systems with no mice or keyboards connected, so installing an application like Caffeine won't work.

Any help would be greatly appreciated.

---

### Post by hhh on 2010-03-12
This one drove me nuts too, and I *think* what I had to do was to leave power management on, turn screensaver off (but leave the daemon running) and add the following to .xinitrc ...
```
setterm -blank 0 -powersave off -powerdown 0
xset s off
```

Sorry, short on time right now, I'll post back after the weekend if you can't figure it out and no one else helps you.

---

### Post by kerry_s on 2010-03-12
never mind.

---

### Post by pcfixitguy on 2010-03-15
> **hhh said:**
> This one drove me nuts too, and I *think* what I had to do was to leave power management on, turn screensaver off (but leave the daemon running) and add the following to .xinitrc ...
```
setterm -blank 0 -powersave off -powerdown 0
xset s off
```

Sorry, short on time right now, I'll post back after the weekend if you can't figure it out and no one else helps you.

I tried the commands you suggested, but when I run the setterm command I get the following:

cannot (un)set powersave mode

---

### Post by hhh on 2010-03-15
I told you this one was maddening. Had you reenabled Power Management /Screensaving first? I see now I also have this in /etc/X11/xorg.conf under Section "Monitor"...
```
Option         "DPMS" "false"
```

Also, look at these threads...
[http://www.randombugs.com/linux/disable-monitor-standby-xorg-xserver.html](http://www.randombugs.com/linux/disable-monitor-standby-xorg-xserver.html)
[http://ubuntuforums.org/showthread.php?t=347079](http://ubuntuforums.org/showthread.php?t=347079)

-edit- Also, I didn't run setterm from terminal, I just added those two lines to  /.xinitrc (which was blank or nonexistent before), just as I posted it.

---

### Post by pcfixitguy on 2010-03-15
> **hhh said:**
> I told you this one was maddening. Had you reenabled Power Management /Screensaving first? I see now I also have this in /etc/X11/xorg.conf under Section "Monitor"...
```
Option         "DPMS" "false"
```

Also, look at these threads...
[http://www.randombugs.com/linux/disable-monitor-standby-xorg-xserver.html](http://www.randombugs.com/linux/disable-monitor-standby-xorg-xserver.html)
[http://ubuntuforums.org/showthread.php?t=347079](http://ubuntuforums.org/showthread.php?t=347079)

-edit- Also, I didn't run setterm from terminal, I just added those two lines to  /.xinitrc (which was blank or nonexistent before), just as I posted it.

Yes, this is VERY frustrating.  Power Management and Screensaving have been re-enabled.  What version of Ubuntu are you running?  I'm asking because I'm running 9.10 and I can't find /etc/X11/xorg.conf or /.xinitrc on any of my 9.10 machines.  I'll take a look at the threads you listed.  Thanks for your help!

---

### Post by hhh on 2010-03-15
Also running Karmic Koala 9.10. .xinitrc goes in your home folder, create it if you don't have it (the dot before the file name hides the file, in Nautilus go to View>Show Hidden Files), xorg.conf is a file that should definitely exist, navigate to Places>Computer>Filesystem>etc>X11 .

---

### Post by pcfixitguy on 2010-03-16
> **hhh said:**
> Also running Karmic Koala 9.10. .xinitrc goes in your home folder, create it if you don't have it (the dot before the file name hides the file, in Nautilus go to View>Show Hidden Files), xorg.conf is a file that should definitely exist, navigate to Places>Computer>Filesystem>etc>X11 .

I did some research and discovered if you do a clean install of 9.10, you won't have an xorg.conf file.  If you did an upgrade, you will.  I'm guessing the same goes for the .xinitrc file.

However, I FINALLY fixed the problem by generating an xorg.conf file and adding some lines to it.  I followed the steps here to generate the xorg.conf file:

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

And then in the Monitor section of the xorg.conf file add this line:

Option "DPMS"

And in the ServerLayout section add these lines:

Option          "BlankTime"     "0"
Option          "StandbyTime"   "0"
Option          "SuspendTime"   "0"
Option          "OffTime"       "0"

I made these changes to all three machines and the monitors have been on for a couple hours now.

Thanks for your help! :D

---

### Post by hhh on 2010-03-16
Coolness, cheers!

---

