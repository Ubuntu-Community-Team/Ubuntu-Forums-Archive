---
title: "kubuntu has much lower battery life than windows..."
date: 2005-08-09
forum: Desktop Environments
---

### Post by nocloud on 2005-08-09
why does kubuntu have much lower battery life than windows on the same system?

---

### Post by PeP on 2005-08-09
did you configure the energy setction in the kde kontrol center??

---

### Post by coolclassic on 2005-08-09
You may have to enable power saving modes

---

### Post by ozzie123 on 2005-08-10
I also noticed that the battery display is not accurate... is there anyway to 'fix' this (you know... with an add-on program or such)

---

### Post by coolclassic on 2005-08-10
Using kynaptic I found the following packages for laptops:

laptop-detect 
laptop-mode   --laptop-mode aims to reduce the power cosumtion 
laptop-mode-tools

---

### Post by nocloud on 2005-08-11
[QUOTE=coolclassic]You may have to enable power saving modes[/QUOTE]

what type of power saving options can i configure in there?

also, 

[QUOTE=coolclassic]
laptop-detect 
 laptop-mode --laptop-mode aims to reduce the power cosumtion 
 laptop-mode-tools[/quote]

does anybody know exactly how those packages work and whether they are any good at all?

---

### Post by coolclassic on 2005-08-11
Bt just using google and typing in- laptop-mode linux - the first entry gave me this: [http://www.xs4all.nl/~bsamwel/laptop_mode/](http://www.xs4all.nl/~bsamwel/laptop_mode/)

---

### Post by varunus on 2005-08-11
Laptop battery life is one of things being worked on in Breezy, I think.  There are a few things you can do to get more battery life till then:

1.  Install cpufreqd from Synaptic/Kynaptic.  Ubuntu's default install includes powernowd, which is a CPU scaling daemon that lowers and raises your processor speed based on how much CPU usage there is.  cpufreqd is much more laptop-minded; it keeps the CPU speed down more when on battery, and up when on A/C. It is more configurable (though you have to edit config files).  The default config from it works for me, at least.

2.  Screen brightness controls.  You may be one of those lucky people for whom the Fn-F6/Fn-F7/whatever keys actually lower and raise your screen brightness.  (Mine do, at least, because I have a toshiba and installed fnfxd from Synaptic, but yours may not dim the screen under ubuntu.)  Windows autodims the screen when on battery; If the keys do work for you, there are ways to do this automatically in Ubuntu also, but once again, you need to edit config files...This is being worked on with the new HAL-based power managers.  I don't know if there's a program you can get to dim your screen...maybe look for one, or if yours is BIOS/hardware based, you're in luck.

3.  Configure K-Laptop.  KDE has a laptop daemon that should run in the system tray; you can set it to reduce HD usage and do monitor shutoffs when on battery, I think.

You can look at Window's power settings and do most of the same things in Linux (disable certain things, lower brightness, lower CPU speed).  Work is being done to reduce HD usage when on battery for Breezy, I think.

---

