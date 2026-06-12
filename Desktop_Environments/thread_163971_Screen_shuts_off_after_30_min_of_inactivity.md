---
title: "Screen shuts off after 30 min of inactivity"
date: 2006-04-21
forum: Desktop Environments
---

### Post by linuxa on 2006-04-21
Hi there

I currently run Kubuntu 5.10 along with WinXP on a Toshiba Satellite 2410. The Kubuntu install has a tendency to show a black screen after 30 or minutes of computer inactivity. 

At which point, the harddrive light still shows activity, fan is still going. CTRL-ALT-Backspace in order to restart X would generally fix the problem. But that also means that I lose whatever work that I had on the computer prior to the black screen.

This has really been driving me nuts as I can't pinpoint (probably lacking the know how) what the real problem is. The same issue doesn't seem to creep up in WinXP, which would lead me to believe that it's a configuration issue in Kubuntu.

So far I've checked/tried the following:
* In my Bios, there's an option to turn off the screen automatically after sometime, which I've disabled.
* turned off laptop mode for Ubuntu
* I use the Nvidia drivers, and have turn on the kernal options for SoftEDID and NVreg for my brand of laptop.
* Power Management in Kubuntu has been turned off.

Nothing seems to work. ](*,) 

I think the issue is due to X11, so if I could maybe get a sequence of logged events before, at and after the black screen, I might have a better idea of what the root of the problem is.

So does anyone know how I could do that, or have some idea how to best go about solving this issue?

I'm still a relative Linux newbie, so any help would in fact be appreicated.

Thanks in advance.

[edit: Power Management is off]

---

### Post by Jason_25 on 2006-04-21
Comment out any references to DPMS in your xorg.conf.

---

### Post by towsonu2003 on 2006-04-21
don't have kubuntu, so not sure if this will work for you. but the idea is the same: check out advanced options for screensaver:
System>Preferences>Screensaver>Advanced (tab)>tweak options on the up right / turn off power management.

---

### Post by linuxa on 2006-04-22
Thanks for the reply guys.

Power Management is already off in Kubuntu. The DMPS option is on in my X11. Will turn that off and give the monitor a try...

---

### Post by linuxa on 2006-04-22
Thanks a lot for all the replies guys.

Because this issue somewhat hard to test intentionally - as in having to leave the computer alone untouched for an extended period of time.

I ended up turning off DPMS and left the computer on for the last hour. The problem seem to have disappeared. I will try to do more rigorous testing in the coming weeks.

It does however look very promising though. So I'm abosolutely grateful for the input and what would probably turn out to the right solution.

Cheers guys, this has been bugging me for a while now :D

Live and learn eh?

---

### Post by linuxa on 2006-05-06
OK. laptop has been running superbly over the last week and bit. I've left it on for extended periods of time and had no screen issues. 

So I think this issue has finally been solved. 

Thanks for the great help guys!

---

### Post by Rhapsody on 2006-05-06
I actually had something of an issue with my monitor going into standby after about 30 minutes of inactivity. This totally baffled me as 'Enable display power management' was *not* selected in the Display options and all of the power management options were greyed-out (though they were not all set at 'Disabled'). After living with it a bit, I enabled display power management, set all of the options to disabled, and then disabled display power management. Bizarrely, this seems to have satisifed Kubuntu, and it no longer does it. Hardly intuitive though.

---

