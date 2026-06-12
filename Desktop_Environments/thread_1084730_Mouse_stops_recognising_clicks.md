---
title: "Mouse stops recognising clicks?"
date: 2009-03-02
forum: Desktop Environments
---

### Post by ichilton on 2009-03-02
Hi,

I've got a rather annoying problem - even now and again I suddenly stop been able to click the mouse.

I can still move the mouse round the screen but I can't click on anything, anywhere.

The only way to fix it seems to be to ctrl-alt-backspace to restart X.

It seemed to only happen about once a day but it's happened 3 times today!

I'm running Ubuntu 8.10 with an NVIDIA GeForce 8400GS card with 2 monitors and an ATI Radeon 8250 card with another monitor on.

I'm mainly only using aterms and a few VirtualBox hosts running Windows.

Any ideas?

Thanks

Ian

---

### Post by ddrichardson on 2009-03-03
Sounds like a hotplug problem.  Is there anything happening prior to it not working? If you have xev running, does it register anything?

Is it related to [https://bugs.launchpad.net/ubuntu/+bug/296167](https://bugs.launchpad.net/ubuntu/+bug/296167)

---

