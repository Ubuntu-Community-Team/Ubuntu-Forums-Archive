---
title: "Extreme Frustration - need help with Video"
date: 2008-05-28
forum: Desktop Environments
---

### Post by PHugger on 2008-05-28
I started out with v710 and was never able to configure things correctly.
I'm running with two Dell 17" monitors and two different video adapters -
Intel 915 (integrated)
nVidia MX4000
Many hours of trial and error with xorg.conf and I am able to get one or the other to run at the correct resolution, but never both. The screen resolution widget seemed to detect and occasionally display the correct settings, but they never 'took'. I gave up and ran with a single display. 

Earlier this month I tried an upgrade to v804. The upgrade appeared to complete successfully, but resulted in a very broken machine. All apps had no window borders/controls and many were just blank white boxes. I burned a new install CD and ran a full install today. I looked at the xorg.conf and it appeared to be plain vanilla default, but it work for a single monitor. It detected the nVidia card and I enabled the restricted drivers. The result was an 800x600 display. The screen resolution widget does nothing. It detects nothing and won't allow anything to be changed. This new widget seems to be a step backwards. I've tried dpkg-reconfigure xserver-xorg, but it only seems to be interested in my keyboard and never offers any display options.

I really want this to work. It shouldn't be this hard. I'd hate to give up at this point. I see hundreds of similar posts - this area needs more work.

Can anyone point me in a direction that may offer some insight?


Thanks!

---

### Post by Sirchristopher on 2008-05-28
Are you running Compiz?  If so there is an option you have to enable to get the top border for the windows.

---

### Post by mrtomservo on 2008-05-28
I was surprised too when I couldn't adjust video settings with dpkg-reconfigure xserver-xorg... Maybe in 8.04 is has moved to another package to be configured or something...anyone out there know?

Anywho - have you installed/run the nvidia-settings program?  If it's not on the menu try running it from the terminal.  I found that to provide what I need for resolutions and dual screen settings.  Obviously remember sometimes you might have to restart X for the settings to take effect.  Hope that helps a little bit!

---

### Post by PHugger on 2008-05-28
I did run the nVidia display settings program and restarted X several times. Still no joy.



PCH

---

### Post by PHugger on 2008-06-02
Well, there were another 20 or so updates today. After a restart it magically started working. It detects the monitor and displays the correct resolutions. I'll still need to work on getting the 2nd card working, but at this point I'm just happy to have one that work.



Thanks,
PCH

---

