---
title: "UPDATE-problem not XSERVER...plz help !!!"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Neo_Geo{Ech13} on 2006-08-28
Hi first of all, nice forums, I have been following them in a while. Unfortunately last couple of weeks my UBUNTU is broken :(
It's acting weird with my monitor, no matter what I've tried with ATI firegl and standard drivers, but that's not the reason im writing.

The big problem is after my last update, I was so relactant to do it and now i regret it the last couple of weeks.When I ran the upgrade at one point it stopped and it asked [No]? but i didnt quite read it and proceeded. It probably deleted something or has overwritten something but I get this error message when i try to load as normally. Now i can only load holding down ESC and choosing some older version down the menu, with no sound e.t.c. Here is the error message I get 

WARNING: couldn't open directory /lib/modules/2.6.15-26-386 :No such file or directory
FATAL: Could not open /lib/modules/2.6.15-26-386/modules.dep.temp for writing :No such file or directory.

Please someone help me. isn't there some way to repair my system to fix this without reinstalling everything?
Thanks in advance !!!

---

### Post by Neo_Geo{Ech13} on 2006-08-28
wow, busy forums, a couple of hours and my thread is hidden in the 3rd page...

bump ^^, anyone got any ideas?

---

### Post by jberman on 2006-12-14
I realize this was posted a while ago, but I had a similar problem last night so I thought I'd post my solution:

Press ESC when booting up to get into the GRUB menu and choose an older version of the kernel, one that worked before.  Once you're logged in, use the Synaptic Package Manager to search for the kernel version that isn't working (in your case, "2.6.15-26-386").  Then right-click on any of the matching packages and choose to reinstall them.

Note: if you are having trouble loading the Synaptic Package Manager, try issuing this command first from a command line:

sudo rm /var/cache/apt/*.bin

Good luck!

---

### Post by Scunizi on 2006-12-14
I have similar problem.  Been running Dapper fine for months and yesturday removed my crt from a dual monitor setup to a single DVI monitor, reconfigured xorg and restarted with no problems.  This morning I've tried the 686 kernal, 686 recovery, 386 & 386 recovery.  All I every get is the login screen, name & password after that nothing but a mouse cursor that's moveable but no gui.  In the xorg.conf I've tried the nvidia driver, nv driver & vesa driver all with no success.  Any suggestions would be greatly appriciated.  I've got work to do!](*,)

---

### Post by Scunizi on 2006-12-14
Got it fixed... sudo apt-get install gnome-desktop

---

