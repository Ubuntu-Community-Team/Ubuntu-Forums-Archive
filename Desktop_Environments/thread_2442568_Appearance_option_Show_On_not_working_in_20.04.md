---
title: "Appearance option Show On not working in 20.04"
date: 2020-05-04
forum: Desktop Environments
---

### Post by rpessoa on 2020-05-04
Hello,

I'm running Ubuntu 20.04 and yesterday I decided to check the Settings > Appearance > Show on option.

I use two monitors. Everything was OK until I decided to see how it would look if I had the dock in "All Displays".

Of course I didn't like it and now it is impossible to revert back to one display only.

 It doesn't matter which display I chose back, the dock is always on both monitors. I can change the option, leave and come back and the "All Displays" is always active.

Is there a way to revert back or use the terminal to force one of the options?

Thanks!

---

### Post by CelticWarrior on 2020-05-04
Please check if you have inadvertently selected the mirror option in screens, not appearance.

---

### Post by rpessoa on 2020-05-05
No, I am using 'Join Displays".

As I said, everything was fine until I tried the "Show on" option and now I can't chose any other option. It is stuck on "All displays". :(

---

### Post by CelticWarrior on 2020-05-05
Try changing to mirror them back to join.

---

### Post by rpessoa on 2020-05-05
> **CelticWarrior said:**
> Try changing to mirror them back to join.

Tried, also tried single monitor and the appearance option still doesn't change.

Could it be my GPU driver? I have a RADEON R9 390X GPU and the official AMD driver for 20.04 is still not available, so I am using the default driver.

---

### Post by CelticWarrior on 2020-05-05
The default driver is as much official than the one you may or may not have available from AMD later (amdgpu-pro).

---

### Post by deadflowr on 2020-05-05
In a funky way you can check
```
gsettings get org.gnome.shell.extensions.dash-to-dock multi-monitor
```
default should be false, if set to true try running reset
```
gsettings reset org.gnome.shell.extensions.dash-to-dock multi-monitor
```
if reset doesn't change it to false try setting it to false
```
gsettings set org.gnome.shell.extensions.dash-to-dock multi-monitor false
```

You can also set primary monitor
```
gsettings get org.gnome.shell.extensions.dash-to-dock preferred-monitor
```
-1 is primary monitor.
1 is secondary monitor
should be defaulting to the primary, but in case it doesn't try
```
gsettings set org.gnome.shell.extensions.dash-to-dock preferred-monitor -1
```

---

### Post by rpessoa on 2020-05-05
It worked!!! 

It was set to true.
So I reset it, but the dock was on the wrong monitor.
Then I set to -1 and everything is back to my normal! :)

Thanks a lot for the help!

---

