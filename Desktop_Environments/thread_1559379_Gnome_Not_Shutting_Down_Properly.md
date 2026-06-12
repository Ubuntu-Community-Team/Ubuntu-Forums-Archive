---
title: "Gnome Not Shutting Down Properly"
date: 2010-08-23
forum: Desktop Environments
---

### Post by Mrich01 on 2010-08-23
Hello Everyone, I'm using Gnome 2.30.2 with Ubuntu 10.4 & would like to shut down X Windows properly.  Using sudo init 3 from console 1 or a terminal on the Gnome desktop results nothing.  There are a bunch of other ways of doing accomplishing this that I've seen, but the most recommended methods each cause the same errors.  The methods that I’ve used are sudo service gdm stop, sudo stop gdm && sudo pkill X, and sudo /etc/init.d/gdm stop.  After these commands are run I receive the following message: gdm stop/waiting.  Then I switch to console 7 & notice that the screen is frozen & has the following information:  fsck from util-linux-ng 2.17.2 /dev/sda5: clean, 172062/7864320 files, 2712422/314552232 blocks (check in 4 mounts) * Starting AppArmor profiles [OK] * Setting sensor limits [OK] * Speech-dispatcher configured for user session [OK] * Starting common unix printing system: cupsd [OK] * PulseAudio configured for per-user sessions [OK] * Enabling additional executable binary formats binfmt-support [OK] * Checking battery status...  There is a blinking cursor below this message & the terminal does not respond to any command including Ctrl z.  These are the same messages that are quickly displayed when linux normally boots.  I disabled the battery power option in & removed other unnecessary startup processes from System, Preferences, Startup Applications.  I've tried running the gdm stop commands from terminals 1 & 2 as well as consoles in Gnome & it produces the same results.  For some reason though, the gdm commands do work when I used the restart option. Any ideas would be great.  Thanks Mark

---

