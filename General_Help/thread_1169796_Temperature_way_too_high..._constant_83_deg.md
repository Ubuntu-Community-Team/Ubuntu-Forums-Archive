---
title: "Temperature way too high... constant 83 deg"
date: 2009-05-25
forum: General Help
---

### Post by shleena on 2009-05-25
Firstly, I'm in no way experienced so go gentle and explain everything like you're talking to a three year old :)

9.04 release. System idle, fan on, steadily goes up to somewhere between 80 and 83 degrees but never higher, never lower. CPU is at around 10% and RAM about 100-200 I just want a quiet cool nice laptop like i did have before and not to be sweating buckets when it's on my lap...

System specs:
Acer Aspire 1640z running Kubuntu 9.04,
1.7 Ghz Intel centrino M processor, 
1024MB DDR2 RAM, 

[COLOR="Red"]Here is the output from POWERTOP:[/COLOR]
```

C0 (cpu running)        ( 2.2%)         1.71 Ghz   100.0%
polling           0.0ms ( 0.0%)         1400 Mhz     0.0%
C1 halt           0.0ms ( 0.0%)         1200 Mhz     0.0%
C2                0.0ms ( 0.0%)         1000 Mhz     0.0%
C3                0.0ms ( 0.0%)          800 Mhz     0.0%
C4               33.7ms (97.8%)
Wakeups-from-idle per second : 29.5     interval: 2.0s
no ACPI power usage estimate available

Top causes for wakeups:
  49.6% ( 29.0)       <interrupt> : acpi
  17.9% ( 10.5)       <interrupt> : ata_piix
   9.4% (  5.5)       <interrupt> : uhci_hcd:usb5, HDA Intel, eth0, i915@pci:0000:00:0
```

[COLOR="Red"]output of cpufreq-info[/COLOR]

```
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.70 GHz
  available frequency steps: 1.70 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.70 GHz and 1.70 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.70 GHz.
  cpufreq stats: 1.70 GHz:0.01%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, 600 MHz:0.00%  (86)
```

i've fiddled about with the fan, thats fine, ive altered the settings of the cpu to clock differently, tried fiddling with bios but that was pointless since it gives nothing useful in the way of information, tried altering settings on power management, went on powersave, conservative... tried RTFMing and Googleing but... I dont know. Nothing gets it lower. Ubuntu was never not warm, and if you started getting a few apps up together it shot up to past 80 degrees but Kubuntu is worse, but I like it and want to keep it.

Any suggestions to lower the temperature? If anyone wants more info from the Konsole then shout out :)

now i'm going to have a glass of iced water and put my laptop down on a non-flammable surface...

---

