---
title: "Laptop drivers"
date: 2010-09-14
forum: Desktop Environments
---

### Post by peter_parker on 2010-09-14
Hey guys,

I have a Compaq Presario CQ60-220US Notebook PC that i installed ubuntu 10.4 on.

i have a feeling i need to upgrade my video drivers on this laptop, because i have issues playing streaming videos (flash, etc) over the web.  They play pretty choppy sometimes.

And even some of my videos played on VLC have issues.

I went on the website and tried to look for drivers.  But they didnt have anything for linux at all...

Am i S.O.L. on this?  What if i wanted to update my sound drivers or whatever...

Thanks in advance.

---

### Post by lovinglinux on 2010-09-15
Go to "System >> Administration >> Hardware Drivers" and activate the latest video driver.

---

### Post by peter_parker on 2010-09-15
When i go there, it goes through a scan and then shows "No proprietary drivers are in use on this system".  It has nothing else listed...

---

### Post by flick on 2010-09-15
Are your graphics card or cards Intel? Nvidia? Something else?

---

### Post by peter_parker on 2010-09-15
Finding my product number and from the site i pull:  

Intel Graphics Media Accelerator 4500M

Using command:  sudo lspci -v | less

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Int
egrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, fast devsel, latency 0, IRQ 28
        Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5110 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable+
        Capabilities: [d0] Power Management version 3
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated
 Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 360b
        Flags: bus master, fast devsel, latency 0
        Memory at 92500000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [d0] Power Management version 3

---

