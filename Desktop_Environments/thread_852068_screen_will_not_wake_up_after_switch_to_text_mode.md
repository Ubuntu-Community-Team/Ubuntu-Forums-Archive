---
title: "screen will not wake up after switch to text mode"
date: 2008-07-07
forum: Desktop Environments
---

### Post by davidshere on 2008-07-07
On the weekends, I often stop GDM to save memory and CPU for other applications.  I do this:
```
sudo /etc/init.d/gdm stop
```
and enter my password.  Everything is fine.  Then then I come back on Monday, the screen is powered off (sleeping), and nothing will wake it up.  I log on through SSH from a different machine, and I've tried this:
```
sudo /etc/init.d/gdm start
```
and this:
```
sudo /etc/init.d/gdm restart
```
and tried other tips for recovering from a blank screen, including changing the **/etc/gdm/gdm.conf** file to include the line **AlwaysRestartServer=true** and changing **/etc/X11/xorg.conf** to include the line **Option "UseDisplayDevice" "DFP"** under the **Section "Screen"**.  No love.  I cannot find any posts with someone having a similar problem to mine.  Most "my screen is blank" posts describe the problem happening on startup, after logging out, or during installation.  Mine is happening only when I switch to text mode and leave the computer, presumably long enough for the power save to put it to sleep.  I also tried turning the screen off and back on again, and when it comes back on it's still in sleep mode.

Rebooting works, but this is Linux.  I only reboot on kernel changes and power outages.

Background on my machine: It's a Dell Dimension 3100, unmodified except to trash the Windows hard drive, and add an HP DVD burner, and upgrade to 2GB RAM.  My monitor is **DELL E173FP** and my graphics card is **Device		"Intel Corporation 82865G Integrated Graphics Controller"** according to the xorg.conf file -- the onboard video.  I installed Ubuntu 7.04 Desktop on it last year and I've upgraded to Hardy since then.  While I've installed the Desktop version of Ubuntu, I run several server applications such as apache and MySQL.  I also run a CentOS virtual machine for use as a mailserver.  Sometimes on weekends I turn of GDM so that these applications and the virtual machine can have more memory.

---

### Post by davidshere on 2008-07-11
bump

---

