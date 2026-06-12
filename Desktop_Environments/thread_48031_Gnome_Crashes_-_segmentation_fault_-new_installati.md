---
title: "Gnome Crashes - segmentation fault -new installation"
date: 2005-07-10
forum: Desktop Environments
---

### Post by KLG on 2005-07-10
After many attempts, and with much help from this forum i 've managed to install ubuntu 5.04 in an FJS Amilo M3438G laptop
After 2 or 3 reboots, when i log in gnome nothing responds...
the 2 bars (up and down) are as if they don't exist, no matter how much i click.
Only right-click in the desktop's main area works, so i can open a terminal menu and log out.

When i log out, i saw in the end of the screen a segmentation fault..

do u have any suggestions?

The laptop has a GeForce 6800 Go graphics card, is it compatible with linux? Because i suspect than many problems come from this card.

---

### Post by KLG on 2005-07-11
any suggestions???

---

### Post by varunus on 2005-07-11
The video card should work with linux, though you do need to install the nvidia proprietary drivers (there's a howto on these forums).  However, this doesn't sound like a video card problem.  Try opening a terminal by right clicking on the desktop and typing in "killall gnome-panel".  Does this work?

If not, try reinstalling gnome-session and gnome-panel from synaptic.  (you can start it from the above terminal with "gksudo synaptic").

---

### Post by KLG on 2005-07-12
i ve tried that but nothing worked.

I even downloaded and installed kernel 686... nothing worked 

When I Ctrl Alt Backspace, i get
.
.
.
.
/usr/bin/on_ac_power:line 25:7042 segmentation fault grep--quier in line "${FN}/state"

failsafe load into gnome doesn't work either

when i type sudo /etc/init.d/gdm stop
 i get the same "segmentation fault"  only i see 7022 instead of 7042

I cant shutdown or restart also.... I think i messed the 686 installation with forced shutdowns because i only see i a black screen and a cursor

PLZ HEEEEeeeeeelP!!!!!!!

---

### Post by varunus on 2005-07-12
I hate to suggest it, but try a reinstall...and try booting a fresh copy without any tinkering.  Does GNOME load then?

---

### Post by Nikola Kasabov on 2005-07-12
Is the PC overclocked?

---

### Post by KLG on 2005-07-12
No Nikola, I wouldn't dare overclock a laptop.....

I can cook a soup on it, even if it is not overcloacked  :wink:

---

### Post by KLG on 2005-07-13
varanus it works, but after one or two reboots it crashes again

---

### Post by hpw on 2005-07-16
i'm having trouble too with the m3438g

one thing that avoids the crashes:
try to add the line
acpi_cpufreq 
to /etc/modules

That fixes a problem with acpi on this devices.
(Worked for me)

Secondly you could try to add the switch "acpi=off" to the kernel
parameters in grub.

btw: Is your soundcard working?

HPW

---

