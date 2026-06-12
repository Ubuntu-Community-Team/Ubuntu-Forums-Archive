---
title: "Screensaver in fluxbox"
date: 2007-01-20
forum: Desktop Environments
---

### Post by WetWired on 2007-01-20
I'm wanting to turn off the screensaver/monitor standby in fluxbox. I've put the following code in my xinitrc file, but it didn't seem to work.

xset s off off

Am I missing something?

---

### Post by K.Mandla on 2007-01-20
The screen timeouts without xscreensaver are better set in your xorg.conf file.

Make sure this is under the "Monitor" section:

```
Option "DPMS"
```
And you can add these to your "ServerLayout" section:

```
Option "BlankTime" "3"
Option "OffTime" "5"
```
Those numbers are the time in minutes for the screen to blank (go black) and turn off (or go into power saving mode), respectively.

There's more here: [http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)

---

### Post by kerry_s on 2007-01-20
> **WetWired said:**
> I'm wanting to turn off the screensaver/monitor standby in fluxbox. I've put the following code in my xinitrc file, but it didn't seem to work.

xset s off off

Am I missing something?

Try-> xset -dpms &

You can check if it's disabled using > xset -q
you should see " DPMS is Disabled "

---

### Post by WetWired on 2007-01-20
Ok, so if I wanted to disable it completely, meaning the monitor would never go to screensaver and never turn off, I'd make my monitor section look like this?

Section "Monitor"
        Identifier      "986FS"
        Option          "DPMS"
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
        HorizSync       30-68
        VertRefresh     50-160
EndSection

Right?

---

### Post by kerry_s on 2007-01-20
That might work, but it would be easier just to remove " Option "DPMS" " so that it doesn't turn on in the first place.

or just add to the start up->

xset -dpms &

and it will always be turned off when ever you start your computer. You can check it with-> xset -q

---

