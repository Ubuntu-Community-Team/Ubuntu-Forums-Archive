---
title: "Make KDE use right screen resolution right away"
date: 2009-11-09
forum: Desktop Environments
---

### Post by bademeister on 2009-11-09
Dear all,

I am running kubuntu 9.10 (amd64) on a thinkpad T60 (intel 945 graphics controller) which I have hooked to a 22" external monitor via a docking station. For this configuration, I want the laptop screen (1024x768) disabled and the external monitor (1920x1080) as primary output (see screenshot).

This used to work fine in ubuntu (gnome with compiz) 9.04 for which I had a custom xorg.conf file. I have copied that file (attached as txt) to /etc/X11 but it doesn't seem to take effect.

The way it is right now is that when I log on, I first have a 1024x768 resolution on my 22" monitor (laptop screen is off how I want it)) and as soon as I click on "Display" in System settings (without making any changes, just running the dialog) it changes to 1920x1080. The laptop screen is listed as 1024x768 even though it seems to be off.

So what is bothering me is that I have to click on "System Settings -> Display" everytime to get the right resolution.

Thank you very much in advance for your help
Paul

---

### Post by dumblebee100 on 2009-12-03
I have the same problem ..I was just about to write a thread over here ...but my change is I want 1600x1200 resolution

---

### Post by bademeister on 2009-12-03
Hey dumblebee,

I never got it to work quite right... I am actually back on gnome because I was so frustrated with the bad support of KDE. Clearly, ubuntu is a Gnome distro and is only dragging kde along for completeness.

One workaround that I used was to call xrandr with the right settings in a login script (say .bashrc or whatever). This is ugly as it sets the screen resolution after the login process, but better than nothing. I actually used it to account for different set-ups (I run with an 22" monitor at home but with an 17" on top of my laptop's screen at the office). 

Let me see if I can still find that script... there it is (get rid of the .txt extension and make it executable (chmod +x monitor_setup))

Ok, it's attached. what it does basically is to look at the first or second line from xrandr (can't remember exatly), decides what monitor is present and then adjusts the settings. Let me know if this works for you.

Cheers
Paul

Btw: If you have a nvidia card then I think this solution won't work for you, b/c the drivers don't support xrandr AFAIK. nvvidia has a similar tool, I don't know how it works but I guess it would be similar to xrandr.

---

