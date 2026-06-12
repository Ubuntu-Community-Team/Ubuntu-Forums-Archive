---
title: "No screen in XFCE after monitor power down and up"
date: 2015-05-03
forum: Desktop Environments
---

### Post by reannual on 2015-05-03
**The problem:** When I turn off my TV (connected to the computer with a displayport->hdmi cable) and immediately after turn it on again, the TV informs me there is no output on the HDMI cable. 

**Things to note:**
* No amount of input (keyboard/mouse activity) brings anything up. It is clearly not just a screen blanking thing.
* This only happens in a XFCE/Xubuntu session. I have checked in Unity ("Ubuntu session") and Lubuntu. These DEs still have an image on screen when the TVs is fully turned on again. The same is true if I am not logged into a DE but simply on the lightdm login page.
* This happens for my primary user account. It also happens for a guest sessions. I have therefore not tried purging configuration files or resetting anything. 
* Changing the input source on the TV does not produce the effect. Going  to watch TV and then going back to Xubuntu, the screen image is still  there.

**Things I have tried:**
* I first set all power saving options to off in XFCE power manager and later completely removed xfce-power-manager. Neither changed anything. 
* After removing xfce-power-manager I have tried turning off as many settings ("Never" turn off/blank anything, basically) in lightdm screen lock settings (light locker) but it will not let me apply them. When I close and reopen the GUI in the same session my settings are still there but they do not carry over to the next session when they have been reset to the defaults (display should turn off after ten minutes. Needless to say, ten minutes have not passed in my tests before the XFCE output is gone. 
* I can bring back an image to the screen by logging in by SSH and restarting the lightdm service. This obviously ends my XFCE/Xubuntu session and brings me back to the login page. The computer has not shut down or gone to sleep in any way as being able to work in SSH sessions demonstrates. 
* Tapping the power button while in this state turns off the computer. Pressing and holding does the same.
* This is not time triggered. It happens regardless of how short a time passes between turning off the TV and turning it back on again.
* I have tried watching for any changes in htop when I turn the TV off/on. Nothing remarkable happens AFAICT. Also dmesg reports nothing of interest.
* I am unable to test if this happens with other screens as I do not have the appropriate cables.

The computer is a new (Broadwell) Intel NUC with Intel HD5500 graphics. The TV is a completely new Samsung smartTV. (X)Ubuntu version is 15.04.
The computer works as my home HTPC server so it should be running constantly while I obviously prefer my TV to turned off most of the time.

I don't really have much of a clue as to why this happens and seems to be XFCE-specific. I am grateful for any suggestions.

---

### Post by I3roknI3ottle on 2015-05-18
Hi,

Are you using Xubuntu 15.04?  Running 'xrandr -d :0 --auto' via ssh should bring the video output back. I am trying to figure out a solution to auto run this via script when my TV turns on. Unfortunately I am not seeing the udev event for TV turning on, only turning off. I believe this is related to this bug, [https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1308105)

---

