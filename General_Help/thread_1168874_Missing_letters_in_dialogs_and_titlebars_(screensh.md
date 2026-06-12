---
title: "Missing letters in dialogs and titlebars (screenshot enclosed)"
date: 2009-05-24
forum: General Help
---

### Post by Phil Airtime on 2009-05-24
I'm using a Dell Latitude C400 laptop which hasn't been modified in any way.

Just installed Ubuntu for the first time on this machine and it's all gone OK. But I have a very odd graphics error--certain letters, not the same ones each time, are missing from titlebars, text fields, dialogs and various other elements of the desktop, replaced by grey or blue boxes. It's hard to describe (and hard to Google to see if anyone else has had the same!) so I've attached a screenshot below. 

There are various other pieces of graphical corruption occurring (icons occasionally going astray from the system tray) but this issue with the letters is the most serious. 

Can anyone shed any light? The laptop seemed to run Windows without issue.

---

### Post by jonrkc on 2009-06-16
A similar thing happened to me today. I installed Jaunty on my ThinkPad T43 laptop last week; had been running fine with Hardy. Today all the letter "e"'s in any displayed text using a system-wide font were replaced by underscores.  I finally killed gdm and opened a new X session and the problem disappeared.  The font is DejaVu Sans Book.  Then this afternoon all the letter "w"'s disappeared similarly.  I changed the font in Firefox to the less-legible (blurry) Free Sans and have all the characters back, as far as I can see.  What can be causing what I assume is a corruption of font tables somewhere?  Any idea how to fix this?

---

### Post by humblegenius on 2009-06-21
The same thing is happening to me, and I've tried changing fonts but it hasn't helped so far. I also have the same laptop as Phil--a Latitude C400--which is likely coincidental, but who knows. I've attached a screenshot.

Additionally, sometimes random icons vanish. If you look at the screenshot, normally the Firefox icon is on the top menu bar right next to "System," but it doesn't always show up and I have to scroll over it to refresh it. Any help or suggestions would be appreciated.

---

### Post by hyperdude111 on 2009-06-21
Maybe a bad download, or try changing fonts.

---

### Post by humblegenius on 2009-06-21
Found solution for this:'

Reference: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059)
Thanks to dwchapin

edit /etc/X11/xorg.conf

Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "AccelMethod" "exa"
 Option "MigrationHeuristic" "greedy"
  Option "ExaNoComposite" "false"
EndSection


restart xserver or reboot.

---

