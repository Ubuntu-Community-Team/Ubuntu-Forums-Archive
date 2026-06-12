---
title: "Can't Install ubuntu or xubuntu on dimension 2350"
date: 2008-03-19
forum: Dell  Ubuntu Support
---

### Post by Revo75 on 2008-03-19
Hey I have a dimension 2350 with a intel celeron 1.99ghz with 128mb of ram and some onboard graphics. Im able to initiate the start process I boot up the cd choose install ubuntu(or xubuntu) after a couple of minutes im hit with some device error which reads
[180.829056] buffer i/o error on device fd0 logical block 0
*I copied this error when trying to install with the safe graphics mode in xubuntu

after the error it starts a whole bunch of services and daemons later on it says it can not start xserver (which is responsible for the gui right?) then it disables xserver and im stuck with a command prompt / terminal screen since I dont know many nix commands by heart its of no use to me. 
It also allows you to diagnose the problem this is what it reads
/etc/gdm/failsafeXServer: line 47: [: too many arguments
Warning: Failsafe mode was already attempted within 30 seconds.
Warning: Falling back to gdm to report the issue.

Is there any way I can get this to fully install and working with the onboard video? I want to set this PC up for my mom and I really don't want her running a windows machine. Im not a total noob when it comes to nix I've used it on and off over the years but never really got the hang of it and im pretty technical so any info at all would be greatly appreciated! I just want to get my mom rolling in the linux camp =) thanks!

---

### Post by michaelaly on 2008-03-19
2350's are tricky. Check your BIOS setting for the graphics card and make sure it's set to onboard not Auto(A02 BIOS) or PCI(A01 BIOS). Any setting besides Onboard will cause any Linux to fail on the install, it's some sort of odd bug with 2350's.

---

### Post by Revo75 on 2008-03-20
Its always been set to on board video would using an ubuntu live cd to install work? or is there some command i could use once im in the terminal window to start a text install and then from there hopefully find some working drivers?

---

