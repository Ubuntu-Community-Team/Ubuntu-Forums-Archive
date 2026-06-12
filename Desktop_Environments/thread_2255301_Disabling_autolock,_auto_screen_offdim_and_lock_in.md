---
title: "Disabling autolock, auto screen off/dim and lock in general"
date: 2014-12-04
forum: Desktop Environments
---

### Post by ubupro97 on 2014-12-04
Hi,

I have configured my battery settings to never alter the display and never autolock the device, yet for some reason while I am plugged in after a short amount of time the screen will turn off and I have to re-login.

This computer is very old, dead and has nothing important on it so I care nothing for security (I use it to display a shell of one of my servers). I want the screen to stay on always unless I manually turn it off and I don't want to have to log in ever.

Sorry if this is the wrong subforum, sorry I know this has been posted, but all the solutions were just around power management settings.

Thanks,
Josh.

---

### Post by coldcritter64 on 2014-12-04
Glad you noted in the other post the duplicate, I'll report it to the mods for you and have it closed. My draft for over there is now posted here ...

Please post back the output of the next command here between  [noparse]```

```[/noparse] tags if you need help with the next  instructions.
```
xset -q
```
This may show further settings, specifically DPMS settings used with the  monitor, which often system settings don't alter leaving the monitor to  turn off even with power saving settings turned off.

The next code box will turn off all DPMS settings if active; Run "xset  -q" again after using it and note the state of DPMS and its values  should be changed thus stopping the monitor turning off.
```
xset dpms 0 0 0 ; xset -dpms;
```

The above code can be set in a bash script in your  "/home/<username>/bin" folder (you may need to create it and log  out then back in to the DE to activate it if necessary) and executed  every startup when added as a "Startup Application"; this should then  keep the DPMS settings "off" all the time.

---

### Post by ubupro97 on 2014-12-04
> **coldcritter64 said:**
> 
```
xset dpms 0 0 0 ; xset -dpms;
```

I've marked the other thread as solved for now, sorry about that.

Does the system automatically lock the computer if the monitor turns it off and that's why I'm finding it locked?

Cheers for the help.

---

### Post by coldcritter64 on 2014-12-04
That sounds like you may have a standby or some other setting active if locking occurs. 

Post back that first code here in a code box, use the advanced editor here and the # button on the toolbar to get code tags inserted. Copy and paste the xset -q command output in between the code tags. That should give a better idea of the settings in use.

Edit: with xfce also go to the main menu > Settings > Settings Manager > Power Manager, Go to the "AC" an "On Battery" tabs and set all monitor settings to "Never" and other actions to "nothing" and detick the "Monitor power management control" option if you already haven't done so.

---

### Post by ajgreeny on 2014-12-04
**Light-locker** is separate from any screensaver or power-manager settings you have made, so you probably need to go to light-locker in the xfce4 settings-manager and either disable it completely, or set it up as you want it.

I have xscreensaver installed and use that, not because modern monitors need a screensaver, but merely as a way to show random slideshows of all my thousands of photos.

---

### Post by ubupro97 on 2014-12-04
> **ajgreeny said:**
> **Light-locker** is separate from  any screensaver or power-manager settings you have made, so you probably  need to go to light-locker in the xfce4 settings-manager and either  disable it completely, or set it up as you want it.

I have xscreensaver installed and use that, not because modern monitors  need a screensaver, but merely as a way to show random slideshows of all  my thousands of photos.

Cheers, this was the issue! For some reason these settings did not match my power settings.

> **coldcritter64 said:**
> 
Post back that first code here in a code box, use the advanced editor here and the # button on the toolbar to get code tags inserted. Copy and paste the xset -q command output in between the code tags. That should give a better idea of the settings in use.


I do know how to use BBCode, lol. Have you checked how old my account is?

---

### Post by coldcritter64 on 2014-12-04
> **ubupro97 said:**
> ...
I do know how to use BBCode, lol. Have you checked how old my account is?

Sorry. No I didn't note your join date. 
OTOH, even some "old timers" don't use them (or [SOLVED] tags ;)) Good to see you've got it fixed. Cheers. :)

---

