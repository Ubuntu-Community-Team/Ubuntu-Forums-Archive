---
title: "Lucid - radeonhd: cursor invisible after resume from suspend"
date: 2010-05-03
forum: Desktop Environments
---

### Post by Anthony on 2010-05-03
I'm posting here to see if anyone is seeing the same problem as me,

Mobility Radeon HD 3650

Using the much-improved radeon driver(Works fine and is fast).
However, there is the following problem:

After resuming from suspend (press power button), display is correct except cursor is not displayed. Mouse responds and I am able to highlight widgets etc. on display and X responds to mouse-clicks correctly.

Confirmed it was definitely Xorg-related (radeonhd):

Logged out of GNOME then logged back in using 'xterm' desktop.
ran pm-suspend(8).
pressed power button and cursor was not displayed.

Currently using the setting where I use the ctrl key to show the cursor position.

2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

[STOP PRESS!!] While I was clicking around, typing this forum post, the cursor has suddenly appeared, about 19 minutes after 'resume' completed.

---

### Post by Anthony on 2010-05-03
Update:

Lost the cursor after also reactivating the screen after it blanked (30 minutes inactivity).

I have a bug report ready to go, want some feedback, shared experiences before firing it off.

---

### Post by Anthony on 2010-05-03
Note: Driver misidentified in Initial Thread Title, See attached Xorg log file.
Actually is 'radeon' driver, not 'radeonhd'.

---

### Post by Anthony on 2010-05-03
This behaviour reported in different distro/driver
Can't say if this is related, but a datapoint of interest

[http://www.rage3d.com/board/showthread.php?p=1336204876](http://www.rage3d.com/board/showthread.php?p=1336204876)

---

### Post by Anthony on 2010-05-04
I can reliably restore the cursor after it becomes invisible by clicking an alternate panel in the "Workspace Switcher"

---

### Post by libertao on 2010-05-04
I'm having the exact same issue using an ATI X1400 on Lucid.  With a little alt+tab and mouse clicking fiddling (haven't narrowed down exactly what fixes it), it reappears after ~10 seconds.

There's also [this thread]("http://ubuntuforums.org/showthread.php?p=9231385") -- like that OP, I too have the lock screen disabled so I don't have to enter the password each time, do you?

---

### Post by Anthony on 2010-05-04
Good to see some more datapoints out there outlining this issue.

No lock screen configured here. OTOH, I don't have a problem with putting my password in on resume. For now, my "Click Workspace switcher" workaround is enough to keep me going for the moment. Got a looming BIG deadline, so as much as would normally collect some detailed diags for a bug report, it is not going to happen in the next two weeks.

---

### Post by Ubuntiac on 2010-05-15
I have this on both my desktop running radeon on an ATI HD4850 and on a Dell Inspiron 1501 running radeon with an ATI Xpress 200M.

It happens 100% of the time after doing suspend to ram and then resume.

ctrl alt + f1, cltrl alt +f7 fixes it every time (until the next suspend). So does typing in a text editor and moving ke mouse a couple of times.

I don't have any screen lock configured and am running Kubuntu Lucid.

I'd suggest adding any info you have to this bug on Launchpad:
[Mouse cursor disappears after restarting screen (xrandr / resume)](https://bugs.launchpad.net/xf86-video-ati/+bug/492782)

---

### Post by phil.lxnet on 2010-05-17
I have the same problem also:- missing mouse cursor after resume with radion driver in Lucid.
Acer Aspire 3050 with ATI RS482 [Radeon Xpress 200M]

Work arounds as above that worked for me:-
Ctrl - Alt - F1 then back to X with Ctrl - Alt - F8
also switching to another virtual desktop via Ctrl - Alt - right cursor key, then back if need be with left cursor key.

There appears to already be a bug report for this:- I have provided the link so that those here who haven't already can take a look and see if there is anything more they can chip in with there.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/552246](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/552246)

---

### Post by Anthony on 2010-06-04
Another data point - Problem persists after kernel upgrade

 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:18:25 UTC 2010 x86_64 GNU/Linux

---

### Post by Babstar on 2010-06-21
Datapoint: IBM T41 (ATI Mobility 7500) no mouse cursor after resume on stock standard Xubuntu Lucid (backports enabled), however Ctrl-Alt-F1 and back to X windows fixes the problem.

---

### Post by keithmcc on 2010-06-23
motherboard:
ASUS M2A-VM ACPI BIOS Revision 1604 (12/19/2007)
RS690 [Radeon X1200 Series]
configuration: driver=radeon

Updated from 9.10 to 10.04

My pointer disappears after I suspend using the power menu or the sleep button on my keyboard but not after it suspends after a time interval set in Power Management.

---

### Post by john.bester on 2010-06-23
I have a similar problem on my Acer Laptop, but without suspending. After the screensaver is deactivated (return back to desktop), the cursor is missing and even though a window may be active, I cannot type any characters into it. I can switch to another window and then switch back as a work around, but it is very annoying.

---

### Post by inverseroom on 2010-07-01
Any progress on this bug?  Still experiencing it every time.  f1 + f7 for now but would love a real fix.

---

### Post by libertao on 2010-07-04
> **inverseroom said:**
> Any progress on this bug?  Still experiencing it every time.  f1 + f7 for now but would love a real fix.

You can at least automate that with this workaround:

> A poor man's solution is saving this script as /etc/pm/sleep.d/99_chvts

#!/bin/bash
case $1 in
    resume | thaw)
        chvt 1
        chvt 7
        ;;
esac

and then doing "sudo chmod +x /etc/pm/sleep.d/99_chvts"

---

### Post by wintermute000 on 2010-07-08
YOU ROCK with that script!

---

### Post by libertao on 2010-07-08
Not mine, but thanks.

---

### Post by keithmcc on 2010-11-23
I do not have this vanishing cursor issue when I connect my monitor with a VGA cable - only with DVI.

Also, I do not have the problem in Meerkat with either VGA or DVI.

---

