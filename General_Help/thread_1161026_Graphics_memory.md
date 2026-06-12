---
title: "Graphics memory"
date: 2009-05-16
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-05-16
I was piddling around today curious about my video mem. Used the "lspci -v | less" command to get some info. 

01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 
8x] (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 8951
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=64M]

        "[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]"

        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb
 
I noticed that vitural memory is disabled, Is this an option that can be enabled, or is it set to disabled for a reason?

---

### Post by dcstar on 2009-05-16
> **Feelin_froggy8877 said:**
> I was piddling around today curious about my video mem. Used the "lspci -v | less" command to get some info. 

01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 
8x] (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 8951
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=64M]

        "[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]"

        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb
 
I noticed that vitural memory is disabled, Is this an option that can be enabled, or is it set to disabled for a reason?

Look up the definition of "ROM".

---

