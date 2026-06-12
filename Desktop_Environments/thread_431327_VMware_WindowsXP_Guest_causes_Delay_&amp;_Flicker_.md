---
title: "VMware WindowsXP Guest causes Delay &amp; Flicker upon entering Full-screen mode"
date: 2007-05-02
forum: Desktop Environments
---

### Post by nick1 on 2007-05-02
Greetings,

First, my setup:

dual-booting Windows XP Professional SP2 and Ubuntu 7.04 Feisty Fawn
Vmware Workstation version 5.5.4 build-44386 installed on Ubuntu
Created a guest VM in Ubuntu running Windows XP Professional SP2
VMware Tools are installed on the guest VM

Hardware:
Dell Latitude D820
4GB of RAM
Nvidia GeForce Go 7400 512MB
using the restricted Nvidia driver via Restricted Drivers Manager (NVIDIA accelerated graphics driver)
Sigmatel STAC 9200 Sound Card
100GB Hard Drive


Problem:

While trying to send the Windows XP guest virtual machine into full-screen mode, 
the monitor goes black and flickers for about 10 seconds, as if it is trying to 
adjust its video settings.

Eventually the guest virtual machine either enters full-screen mode or partial full-screen mode,
meaning a black border surrounds the guest virtual machine.

In VMware workstation, I have the following display settings configured under Edit > Preferences:
Autofit window = enabled
Autofit guest = enabled
Resize guest = enabled

Within the Windows guest VM:

Viewing Display Properties > Adapter in Windows shows the following information:
Adapter Type: VMware SVGA II
Chip Type:  VMware SVGA II
DAC Type:  VMware SVGA II
Memory Size: 16MB
Adapter String:  VMware SVGA II
Bios Information:  VMware SVGA II

Viewing Display Properties > Monitor in Windows shows the following information:
Monitor Type: Default Monitor
Screen refresh rate: 85Hertz


Resolution:

I have yet to find a resolution to this problem.

I would like to resolve the delay and flicker that occurs while trying to send the guest virtual machine
into full-screen mode.  A smooth transition should occur while entering full-screen mode.

Thank you for your time,

*Nick*

---

### Post by nick1 on 2007-05-03
*BUMP*

I'm hoping someone can help me with this problem.

Thanks,

*Nick*

---

### Post by orb9220 on 2007-05-03
Do you have compiz or beryl on?

---

### Post by nick1 on 2007-05-03
> Do you have compiz or beryl on?

Thanks for replying.  It looks like compiz is installed but beryl is not installed.
I am not knowingly using any fancy desktop effects.  Is there something I should configure in compiz?

Thanks,

*Nick*

---

### Post by nick1 on 2007-05-05
and another *BUMP*

I'm hoping someone can help me with this problem.

Thanks,

*Nick*

---

### Post by nick1 on 2007-05-13
I believe my problem has been resolved.

Here's what I did:

1.) uninstalled VMware Workstation version 5.5.4 build-44386

2.) left the virtual machines intact

3.) installed VMware Workstation version 6.0.0 build-45731

Now when I send the Windows XP guest virtual machine into full-screen mode, the guest instantly adjusts without delay.



*Nick*

---

