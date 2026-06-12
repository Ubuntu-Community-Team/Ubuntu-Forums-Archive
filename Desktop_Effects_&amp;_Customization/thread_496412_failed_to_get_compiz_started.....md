---
title: "failed to get compiz started...."
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by Mia_tech on 2007-07-09
after installing compiz I got the following error
jorge@ubuntu-box:~$ compiz --replace
Fatal: Failed test: non-power-of-two texture support
Checks indicate that it's impossible to start compiz on your system.

this is my video card, does any body has been able to get it running on a card like this
description: VGA compatible controller
                product: Rage 128 Pro Ultra TF
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:f0000000-f3ffffff ioport:c800-c8ff iomemory:ff8fc000-ff8fffff irq:16

---

### Post by Waappu on 2007-07-09
Hi

I found these links and they say you can't run Beryl or Compiz with that card
[http://www.freesoftwaremagazine.com/node/1797](http://www.freesoftwaremagazine.com/node/1797)
[http://fedoraproject.org/wiki/RenderingProject/aiglx](http://fedoraproject.org/wiki/RenderingProject/aiglx)

---

### Post by uterrorista on 2007-07-09
i have a friend that has a** VT8237R Plus**
and don't work either. don't if it is a problem of chipseat support or..
> ubuntu@Ubuntu:~$ compiz --replace
Fatal: Failed test: non-power-of-two texture support
Checks indicate that it's impossible to start compiz on your system.

Note: this is with compiz fusion...

---

### Post by uterrorista on 2007-07-16
in my [blog]("http://linuxinside.blogspot.com/2007/06/compiz-fusion-git-repository-for-ubuntu.html#comments"), there are 2 persons complaining about this problem.

the video chipseat are:
> I've an S3 prosavage8 KM266/KL266.
and
> VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

isn't any way to put compiz working?

---

