---
title: "guidance-power-manager.py crashes, new install"
date: 2007-06-13
forum: Desktop Environments
---

### Post by technick on 2007-06-13
Hi All, 

I just installed Kubuntu Fiesty on a HP Desktop with integrated intel vdeo and Nvidia FX 5500 video card. I went thru the steps of disabling the onboard video (edited blacklist) and booted with the nvidia card, everything was working great till I enabled multi-monitor support. Now on boot the "Power Manager" crashes. Here is the specific error and I am attaching the backtrace.

"The application Power Manager (guidance-power-manager.py) crashed and caused the signal 11 (SIGSEGV)"

How can I fix this? Its a desktop so I don't really care about power management. I've tried disabling acpid, apmd and powernowd and still get the same error.  

Thanks in advance.

---

### Post by technick on 2007-06-14
Going Once... anybody wanna chime in on this one?

---

### Post by brett.goodwin on 2007-09-05
I have this same problem.  It seems to occur when I attempt to run my system with multiple monitors, and also prevents me from accessing the Monitor & Display Settings control panel with a similar error.  Any input on this would be appreciated!

---

### Post by benz0 on 2007-09-16
I've got the same problem as both of you.  I've checked system logs and can't find any thing to indicate what might be going on.  Has anyone seen a resolution to this issue?

---

