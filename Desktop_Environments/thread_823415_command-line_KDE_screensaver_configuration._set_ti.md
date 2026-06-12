---
title: "command-line KDE screensaver configuration. set timer?"
date: 2008-06-09
forum: Desktop Environments
---

### Post by Zorael on 2008-06-09
(Thread aim changed along the way, it'll be confusing until you reach the next post.)


I have a laptop. Earlier today, I had it on battery power and thought I'd compress a folder while I search for the AC adaptor. While doing this, I see my beatiful screensaver pop up, draining my precious battery strength with gorgeous graphics (Fractals -> Julia)! What gall!

So I thought I'd write a script and then find some way to have it run when it switches between power modes.
```
$ dcop kdesktop KScreensaverIface functions
QCStringList interfaces()
QCStringList functions()
void lock()
void save()
void quit()
bool isEnabled()
bool enable(bool e)
bool isBlanked()
void configure()
void setBlankOnly(bool blankOnly)
void saverLockReady()

```
The optimal solution would be to have it set it to suspend *the screen* for screensaving, when on battery, but kdesktop doesn't seem to handle that. If this is handled by another program (xset?), perhaps it'd be possible to use dcop to disable kdesktop's 'saver and then set that program to suspend the screen (early) in its place. But I can't figure out what that program might be.


A suboptimal but acceptable solution is to have it use the blank screen 'saver when on battery, which seems to be possible to toggle temporarily with this DCOP call:
```
$ dcop kdesktop setBlankOnly true
```
Likewise, setting it to false seems to restore it to once again use the defined screensaver. However, I still can't seem to change the timer value, which I'd really like to do. What the configure function does is beyond me; it doesn't accept arguments (void), and invoking it does nothing.

I'd also need to know where to hook this script to get it to run upon power mode switch.


Any ideas? I'm running on fumes now.

---

### Post by Zorael on 2008-06-09
It's apparently my curse to always make some progress after having given up and posted here for help. I've been tinkering around on a desktop system with an oldish Dell LCD screen, which may lack some DPMS features. I made sure I had the "DPMS" option enabled in xorg.conf's monitor section.
```
usage:  xset [-display host:dpy] option ...

    To control Energy Star (DPMS) features:
        -dpms      Energy Star features off
        +dpms      Energy Star features on
         dpms [standby [suspend [off]]]
              force standby
              force suspend
              force off
              force on
              (also implicitly enables DPMS features)
              a timeout value of zero disables the mode
```
```
$ dcop kdesktop KScreensaverIface setBlankOnly true
$ xset dpms 0 5 6
```
This makes it first set the screensaver to blank screen, then after five seconds it will start the process that eventually ends up with the screen powered off. I obviously don't want the timer to be 5 seconds later, but these were the values I used when tinkering about.

The process is a bit weird. When it first starts to "DPMS" - meaning, after the first timer entered (in this case 5, would be 3 if I used [FONT="Courier New"]xset dpms 3 5 6[/FONT]) - it'll start the screensaver. After about ~8 seconds, the screensaver will freeze. If I haven't enabled the '**off**' functionality (third digit), it will end there, with the screensaver frozen. If I *have* enabled the off functionality, it will at this point shut the monitor down. Setting [FONT="Courier New"]xset dpms[/FONT] to **0 0 5** (which would seem to be the obvious solution; to have it only power off after 5 seconds) didn't work, for some reason. So [FONT="Courier New"]xset 0 *n n+1*[/FONT] seems to be the logical choice. Again, this is an old screen, so perhaps it'll exhibit different behavior on my laptop.

```
#!/bin/bash

# battery mode

dcop kdesktop KScreensaverIface setBlankOnly true	# set to blank screen 'saver
xset 0 300 301
```
```
#!/bin/bash

# AC mode

dcop kdesktop KScreensaverIface setBlankOnly false	# reset to normal 'saver
xset 0 1800 1801					# unsure about this line's values
```
Remaining problem is to get them to run upon power mode changes. Ideas?

Updating title (if still possible). edit: Doesn't seem like it. :<

---

