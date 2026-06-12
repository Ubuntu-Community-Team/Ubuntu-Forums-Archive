---
title: "Backlight stays on - Latitude CPxJ"
date: 2008-07-06
forum: Desktop Environments
---

### Post by JohnnyVW on 2008-07-06
Hey Folks,

I've scoured the 'Net and the Ubuntu forums and I can't seem to figure this one out.

It seems that ever since I loaded Hardy on our Latitude CPx-J650, the back light on the monitor stays on all the time.  I have the screen saver set to blank (which it does) at 5 minutes and the power management set to turn off at 6 minutes.  

I seem to remember this happening after the Edgy to Feisty upgrade.  After a few updates, it fixed itself.  It worked from Feisty to Gutsy.  Now...  It just stays on.  

Funny thing...  The screen does turn off when the lid is closed and suspend works great.

Any ideas?  We use the laptop in the bedroom and I suppose it makes an okay night light...

---

### Post by JohnnyVW on 2008-08-19
Anyone?

---

### Post by blattengel on 2009-07-19
*bump*  I have the same issue.  The original poster was running an older version of Xubuntu though, Xubuntu 8.10.

I guess the "backlight" remains on when the screen saver activates, while no screen saver appears.  Right now I have the screen saver set to Random.  The set screen saver does NOT turn on and the monitor does NOT turn off after XYZ minutes, it does not turn off ever.  Note the monitor will turn off when I press the button :-)

I noticed that the following command causes desktop to disappear/blacken, while the backlight remains (The normal screen saver?):
```
sleep 1; xset s activate
```
(The sleep is needed.  If there is input right before, the monitor will not remain off, it will flicker on and off.)

This turns off the monitor (yay!):
```
sleep 1; xset dpms force off
```

Also, I noticed that this script turns off the monitor (yay!):
```
/etc/acpi/screenblank.sh
```

So, if there is no other fix, how could I get one of those commands to execute XYZ minutes after the last input?


Here is a bunch of info that might be useful in diagnostics:
```
andrew@andrew-desktop:~$ uname -a
Linux andrew-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

It is Xubuntu Jaunty 9.04.

Monitor is a Rosewill R912E.

I don't think I have compiz, gnome, or kde installed for anything other than dependencies.

Proprietary NVIDIA driver version: 180.44

Xfce 4 Desktop Environment
version 4.6.0 (Xfce 4.6)

---

### Post by blattengel on 2009-07-19
Maybe check your settings in BIOS related to ACPI (power saving settings).  I tried a few different settings in there, all had resulted the same (monitor not turning off).  Maybe someone with this backlight problem can find a fix in their BIOS settings.

Now, I think I found two separate ways around the "backlight" problem.
[INDENT]Solution 1 seems to work conditionally- the conditions are unknown to me.  This method should result in your monitor turning off when the screensaver would activate.
Solution 2 works better.  It requires more space as you are installing another screensaver thingie.  You also get the screensavers to work! (as they should)[/INDENT]

-----------------------
**1)**
-----------------------
[INDENT]Since this line shuts off the screen:
```
sleep 1; xset dpms force off
```

I thought I'd make my own script as a screensaver that turned the monitor off.  I ran this to find the directory that the screensavers were in (antspotlight is a screensaver I have):
```
find / -iname "*antspotlight*" 2>/dev/null
```
I'd recommend you run this and ensure that the two directories that the following two files will go into exist.

I made two files.
**File 1** (The screensaver):
[INDENT]/usr/lib/xscreensaver/monitoroff.sh
```
#~/usr/bin/env bash
#/usr/lib/xscreensaver/monitoroff.sh
# Sleep for a second, just in case.
sleep 1
# I guess this line turns off the monitor somehow...
xset dpms force off

```
The monitoroff.sh needs to be executable:
```
sudo chmod ugo+x /usr/lib/xscreensaver/monitoroff.sh
```[/INDENT]

**File 2** (Tells the xubuntu screensaver thingie that the screensaver exists):
[INDENT]/usr/share/applications/screensavers/monitoroff.desktop
```

[Desktop Entry]
Encoding=UTF-8
Name=MonitorOff
Comment=Turns off the monitor. Written by Andrew Smart; 2009.
TryExec=monitoroff.sh
Exec=monitoroff.sh -root
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
```
Attached is the xubuntu screensaver box showing the new screensaver.  You will need to select it in order for it to work.[/INDENT][/INDENT]

-----------------------
**2)**
-----------------------
[INDENT]I installed xscreensaver from a repository (not the one that came with xubuntu).  Looking at the 'System Monitor', the executable name of the screen saver that comes with xubuntu is "gnome-screensaver-preferences"?  I believe I installed some gnome stuff for dependencies.  If it came with xubuntu- I think that odd.  So, anyways:
```
sudo aptitude install xscreensaver
```
After doing that, I had two items labeled "screensaver" in the settings item of the xfce4-panel menu.  One will configure the xscreensaver just installed.  The other will configure the screensaver thingie that came with xubuntu.  Upon running the screensaver installed by "apt-get xscreensaver", it says something along the lines of "The xscreensaver daemon is not running.  Would you like to start it on display 0:0?".  If you hit yes, it should start.  Unfortunately, it doesn't automatically start with each system boot.  A way to get it to start on each boot, is to execute the command "xscreensaver &" on boot.  Three ways I can think of to do this:
[LIST=1]
[*]You can add that command in your system menu -- the application on XUbuntu's menu is named "Session and startup".
[*]You could add it is by using "update-rc.d" but that would be way crafty -- I couldn't get it to work.
[*]I think there is a file somewhere you can add that line to, I don't recall it's name though.
[/LIST]   

Don't forget to activate the "Power Management" and set when the monitor should turn off (See third attached image).[/INDENT]


I used both solutions 1 and 2.  I think both screensaver thingies are working on my system.  I guess whatever one is set to the least time will take precedence.  Although solution 1 seems a bit flaky.

---

### Post by daqron on 2010-12-09
blattengel's very last screenshot is what I came up with as well. Those super-secret Power Management options did the trick on my Dell D600.

I don't know why the Power Management control panel's "turn off monitor" option doesn't just do what it says.

---

