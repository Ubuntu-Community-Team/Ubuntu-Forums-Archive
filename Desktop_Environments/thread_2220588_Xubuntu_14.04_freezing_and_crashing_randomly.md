---
title: "Xubuntu 14.04 freezing and crashing randomly"
date: 2014-04-28
forum: Desktop Environments
---

### Post by gabriel19 on 2014-04-28
I have just installed Xubuntu 14.04 and it's constantly crashing just like the pic shows and I have to reboot. Could you tell me what's happening and possible solutions? I'm new to the system. Thanks.
[ATTACH=CONFIG]252615[/ATTACH]

---

### Post by dannyboy79 on 2014-04-28
can you tell us what graphics card and driver you're using please? you can issue the following command and look for the line that has "VGA" in it (i think)

```
sudo lspci -v
```

---

### Post by gabriel19 on 2014-04-28
> **dannyboy79 said:**
> can you tell us what graphics card and driver you're using please? you can issue the following command and look for the line that has "VGA" in it (i think)

```
sudo lspci -v
```

It says:

 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6100 nForce 405] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device d000
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 40
    Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: nouveau

It usually happens after I launch an application, especially after I click on the mail notification and firefox but also the file manager.

---

### Post by dannyboy79 on 2014-04-28
Ok, you have an nvidia card and are using the default nvidia open source driver. may i suggest trying out the proprietary nvidia driver, look within settings, additional drivers. it appears like a graphics driver problem but it may be related to something else, who really knows. good luck

---

### Post by gabriel19 on 2014-04-28
It worked well. The screen is even brighter :). Thanks for your help.

---

### Post by dannyboy79 on 2014-04-30
awesome, glad i could help. please mark the thread solved using the "thread tools"

---

