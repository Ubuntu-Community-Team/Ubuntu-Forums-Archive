---
title: "ATI + Ubuntu 7.10 + Multiple Monitors = Fail."
date: 2007-10-23
forum: Desktop Environments
---

### Post by Locke2053 on 2007-10-23
Does anybody know how to get multiple monitors working with an ATI/AMD graphics card on Ubuntu 7.10? Searching the forums shows many people with the problem, but none with the solution.

If you enable the restricted fglrx driver, then check "Secondary screen" under Ubuntu's new "Screens and Graphics" app, then click "Test," the Screens and Graphics app crashes. If you do the same but click "OK" instead of "Test," X will crash after you reboot.

In my case, this occurs on a PC which worked properly with dual monitors using Ubuntu 7.04 (after editing the X configuration file by hand). 

Again, there were many people having this problem in the forums, but here's my hardware configuration:
[LIST]
[*]64bit Intel CPU (Dual Core)
[*]ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)] (rev 80) Graphics Adapter
[*]Typical LCD monitors (2)
[/LIST]

It worked with 7.04 after manual configuration of X, It crashes in 7.10 after using the new Screens and Graphics configuration tool (after a fresh install and total disk wipe).

Thanks to the Ubuntu and Debian teams for putting together such a great system. I only wish someone with the ability could patch this show-stopper bug in the new config tool.

---

### Post by kansei on 2007-10-23
I have that same issue with the "screens and graphics" app, and I'm not even using the proprietary ATI driver, I use the open source driver (it has partial 3d support for the radeon 9600 in my laptop). I was about to try the proprietary driver to see if that would fix it, but of course it doesn't.

I'll have to check for a bug report in the morning, I've had enough of it for tonight.

---

