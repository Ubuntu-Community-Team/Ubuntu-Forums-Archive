---
title: "Failure to create xorg.conf"
date: 2016-03-27
forum: Desktop Environments
---

### Post by nmw01223 on 2016-03-27
Running 14.04.4 LTS with 1600x1200 Eizo monitor connected by VGA input (all it has). ATI Radeon HD5450 graphics card, Nouveau driver.

I am trying to create a base xorg.conf that I can then modify, I switched mode with alt-ctrl-F1 and logged in, then stopped lightdm with
```
sudo service lightdm stop
```
All good so far.

However when I try to create an xorg.conf with
```
sudo X -configure
```
it says nothing to configure, exiting with error (2).

Don't see what is wrong?

---

### Post by ajgreeny on 2016-03-27
The nouveau driver is for nvidia graphics not AMD, so it is difficult to know what you really do have as driver for that card, though I suspect it may be the radeon driver.

Show us the VGA section of the output of ```
lspci -v
```in terminal.

---

### Post by nmw01223 on 2016-03-28
```
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 04b3
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at df7e0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at df7c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
```

I thought that was the Nouveau driver doing all these cards, but maybe not. Either way, still not getting an xorg.conf.

---

### Post by ajgreeny on 2016-03-28
As you will see in that final line, you are using the radeon driver, ie the one that comes with Ubuntu at installation and is open source.

If you go to the Additional Drivers utility in the dash you should find there is a recommended proprietary driver for your card; give it a try.

---

### Post by nmw01223 on 2016-03-28
Thanks, yes, I know. I just made the mistake of assuming that all those open source drivers came under the overall label of Nouveau, which, as you pointed out, they don't.

However, that doesn't solve my problem, which is not quite what it might seem. Yes, there is a proprietary driver for this card, but this is merely an experiment before transferring to another (older) system with onboard ATI Radeon graphics for which there is no ATI driver for its current kernel. Hence the need to use the open source driver.

I need to do some things I think I may possibly be able do with xorg.conf (using viewportin, viewportout), but it would help to have a 'get you going' xorg.conf for the system to start with, which is what I was after. These things work fine with nVidia based graphics, but I'm not sure if they will with ATI.

So, it is partly to solve a problem, partly a learning process.

---

### Post by ajgreeny on 2016-03-28
See if [https://www.google.com/url?q=http://askubuntu.com/questions/688388/14-04-gets-black-screen-unless-radeon-modeset-0&sa=U&ved=0ahUKEwiY2IqBpuTLAhVGsxQKHR6pAA4QFggTMAU&client=internal-uds-cse&usg=AFQjCNHp7zh9VOTaTRck7g2wqKDjOIY9zw](https://www.google.com/url?q=http://askubuntu.com/questions/688388/14-04-gets-black-screen-unless-radeon-modeset-0&sa=U&ved=0ahUKEwiY2IqBpuTLAhVGsxQKHR6pAA4QFggTMAU&client=internal-uds-cse&usg=AFQjCNHp7zh9VOTaTRck7g2wqKDjOIY9zw) helps you with a boot option for that card.

I've never needed to do anything like that with my Intel graphics, so have no experience to go on but it must be worth a try.

---

### Post by him610 on 2016-03-29
It is probably not a _failure_ to create xorg.conf, but a design feature.

None of the several machines that I use with Nvida, AMD, and Intel graphics have xorg.conf.  All machines are running 14.04 or later. I remember a few years ago editing xorg.conf, but I have not done it for awhile now. Admittedly, I do have run-of-the-mill systems and only place modest demands on my graphics chips/cards.

Could it be possible that xorg.conf has been removed as unnecessary,  or replaced by something not so easily screwed up?;)

---

### Post by him610 on 2016-03-31
For what it is worth, I have listed the contents of  my 10-amdgpu.conf ...

```
~$ cat /usr/share/X11/xorg.conf.d/10-amdgpu.conf
Section "OutputClass"
	Identifier "AMDgpu"
	MatchDriver "amdgpu"
	Driver "amdgpu"

```

---

