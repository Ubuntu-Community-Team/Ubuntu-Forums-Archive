---
title: "Setting up an external monitor in mirror mode using an NVIDIA GF119 driver"
date: 2013-02-02
forum: Desktop Environments
---

### Post by Leo Simon on 2013-02-02
I have just installed the NVIDIA Corporation GF119 on my Dell E6520, running linux ubuntu 12.04. I want to use xorg.conf to connect to an external monitor in mirror mode. But it seems to be hardcoded to TwinView. I've tried what I would have thought would work in xorg.conf, i.e., for example

Section "ServerFlags"
    Option         "TwinView" "0"
EndSection

But the external monitor still comes up in TwinView mode.

There is a post on lists.x.org about exactly this

[http://lists.x.org/archives/xorg/2012-April/054301.html](http://lists.x.org/archives/xorg/2012-April/054301.html)

but when I tried to do what seemed to be being recommended it just hung my machine.  (Hard to figure out exactly what was being suggested on this post)

Could somebody advise please?

Any help would be much appreciated.

---

