---
title: "GNOME 3.8.2 screensaver issue?"
date: 2013-06-15
forum: Desktop Environments
---

### Post by pgarlinski on 2013-06-15
I haven't been able to find this anywhere, either on the forums or through Google.

I'm currently using Ubuntu GNOME 13.04 with GNOME 3.8.2. 

I have set the following within the Settings area:

Privacy: 
- Automatic Screen Lock: On
- Lock Screen After Blank For: Screen Turns Off
- Lock Screen On Suspend: On

Power:
- Dim Screen When Inactive: On
- Blank Screen: 10 Minutes

With these settings on, the screen blanks like I would expect it to.

50% of the time, when I move the mouse, the lock screen appears. I slide it up and I can enter my password. Yay!

50% of the time, when I move the mouse, I get a blank black screen. I can't do anything. I see nothing. I can't reboot, I can't enter a password. The only way I can get out of this is to TTY into another session and do a sudo reboot command.

So, the question is...is there a bug somewhere? Or is this a problem with my specific setup? As mentioned, I can't find anything.

P.S. I installed XScreensaver and I'm using that in the meantime, as that works just fine.

---

### Post by guyr34 on 2013-06-15
You can try "killall -HUP gnome-shell" as user into a TTY
Then CTRL-ALT-F7 or F8, no need to reboot ...

---

### Post by markbl on 2013-06-16
I see this also but I have 2 screens and it only happens to my left main screen. I have discovered that I can "reawaken" the screen by switching to a virtual console terminal (using ctrl+alt+f1) and then back again to X (ctrl+alt+f7). You have to get the timing of this just right. If I switch to the virtual console and wait too long then it will not awaken the screen when I switch back. I have to do the switch to and back in about 1 to 1.5 secs and the problem will clear.

---

