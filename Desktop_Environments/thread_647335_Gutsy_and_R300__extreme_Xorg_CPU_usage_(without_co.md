---
title: "Gutsy and R300 : extreme Xorg CPU usage (without compiz!)"
date: 2007-12-22
forum: Desktop Environments
---

### Post by alanfranz on 2007-12-22
Hello, I'm experiencing a really nasty problem since I've switched to Gutsy (in Feisty everything was all right).

My laptop is a Dell Latitude D810 ( Pentium M, ATI Mobility Radeon X600 ( r300-based), 2GB RAM, 160GB hd) which would always work correctly.

Since I installed Gutsy ( x86 32 bit), just typing something like

less textfile

In any X terminal, will drive the CPU usage of Xorg up to 100% when doing a simple scroll. Same issue with Gvim (which I use a lot).

I thought it was a configuration issue, hence I made the same check from the Gutsy live cd... and the problem was already there! No need to install, just open a terminal, less a file and I get that extremely high cpu usage.

I tried many things to solve the problem:
- I changed xorg.conf in plenty of ways, enabling/disabling DRI, installing or uninstalling the proprietary fglrx driver, enabling or disabiling the composite extension, but I had no luck. That thing keeps happening.
- I tried to do an strace on Xorg but too many things happen in the server to be able to understand what's the real issue.
- I tried to install compiz (through fglrx and xgl) and I found that everything works pretty fine (but it's a bit unstable when watching videos, I can't use it on a daily basis) with it.
- I tailed -f Xorg logs for problems, but found nothing useful. There seems to be no explicit error reports.

In the end, I think it's a driver issue, but I'm unable to track it down to a specific problem.

Any help will be greatly appreciated.

---

### Post by kc0eks on 2008-01-03
I have similar problems in Gutsy, I dont see any problem in terminal but all the web browsers and some other GUI programs max out CPU usage whenever I scroll. Firefox and Opera are nearly unusable on some sites due to very laggy scrolling.

---

