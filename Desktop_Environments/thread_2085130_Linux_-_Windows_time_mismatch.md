---
title: "Linux - Windows time mismatch"
date: 2012-11-17
forum: Desktop Environments
---

### Post by zobayer1 on 2012-11-17
I use both operating systems (Windows 7 x64 and Ubuntu 12.04 PP x64). The chipset is z68. I am on GMT +6 timezone. Whenever I boot with linux, I find that time is OK (GMT +6) but when I go back to windows, it always shows GMT time, although settings show GMT +6 is selected. If I go back to Linux, it always shows correct time.

My computer cannot always stay connected to internet, so it is not possible to get synchronized every time. Probably this happens because of how both OS manages their time settings, but is there any way so that I can avoid fixing them manually every time (other than synchronizing with internet, as I said, that may not be always possible).

Thanks in advance.

---

### Post by anarchticgrimm on 2012-11-17
Hey,

Can you try to set your Windows Time Zone as UTC, then restart your system to check if it's corrected? I've had the same issue several years ago, when I searched on Google found some instructions to make it corrected.

For example; [http://mikebeach.org/2011/04/10/windows-linux-dual-boot-system-time-issues/](http://mikebeach.org/2011/04/10/windows-linux-dual-boot-system-time-issues/)

PS. You won't need to set your Linux time zone as UTC.

---

### Post by zobayer1 on 2012-11-17
Thanks, fixed :)

---

