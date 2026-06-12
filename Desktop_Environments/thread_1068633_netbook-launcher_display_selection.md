---
title: "netbook-launcher display selection"
date: 2009-02-13
forum: Desktop Environments
---

### Post by ducky101 on 2009-02-13
Hi everyone,
I have a asus eeepc 1000h, and I installed ubuntu netbook remix on it.

The eeepc is connected to an 23" external monitor, which is the top screen. The eeepc is the bottom one.

I want the netbook-launcher to load on the eeepc when I connect to the monitor. Now it always loads on the main screen, which is the monitor.

Is there a "-display :0.1" kind of functionality which I can pass to netbook-launcher?

Thanks
Alex

---

### Post by doobiest on 2011-04-11
late reply, but from a shell:

export DISPLAY=:0.1; netbook-launcher

---

