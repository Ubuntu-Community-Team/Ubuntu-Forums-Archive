---
title: "High temperature issue"
date: 2011-04-25
forum: Desktop Environments
---

### Post by aditya08 on 2011-04-25
Hi All,

Ever since I installed ubuntu 10.10, my laptop is shutting down due to high temperature within 15-20 mins. It makes my laptop literally unusable. Had posted the issue, got some advise but the issue didn't get resolved, hence posting again. Below is previous post. 
[http://ubuntuforums.org/showthread.php?t=1736724](http://ubuntuforums.org/showthread.php?t=1736724)

Is there any tool or way by which I can check if it's a hardware issue.

Thanks,
Aditya

---

### Post by K_45 on 2011-04-25
Have you tried to blow a can of compressed air in the vents? Then check the BIOS for any options related to CPU throttling and set them to default.

---

### Post by conradin on 2011-04-25
You know anyone who can take apart your computer and clean the heatsink and fan? 
Hardware over heating isnt likely the OS. 

just for giggles, 
heres a bash script for monitoring heat
(quick and dirty)
```

        #!/bin/bash
        for i in `seq 1 5`;
        do
                sensors >> someFile
sleep 100
        done 

```

you could boot, run that script, and show us the output. 
you could try scaling down your cpu speed but really thats not going to help only so much.
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by aditya08 on 2011-04-25
> **K_45 said:**
> Have you tried to blow a can of compressed air in the vents? Then check the BIOS for any options related to CPU throttling and set them to default.
Cleaned using a vacuum cleaner.
BIOS - checked using f2 key during startup, there was no such option.

---

### Post by aditya08 on 2011-04-25
Don't know anyone like that..I didn't face any heating issue when I had windows 7.
Here is sample output

tanu@tanu-Studio-1555:~$ more someFile
acpitz-virtual-0
Adapter: Virtual device
temp1:       +58.0°C  (crit = +100.0°C)                  
temp2:       +61.0°C  (crit = +100.0°C)                  
temp3:       +84.0°C  (crit = +100.0°C)                  

acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.0°C  (crit = +100.0°C)                  
temp2:       +62.0°C  (crit = +100.0°C)                  
temp3:       +85.0°C  (crit = +100.0°C)

---

### Post by conradin on 2011-04-25
Windows makes use of ACPI in such a way that is integrated into every part of the OS and nearly impossible to disable. Linux on the other hand views ACPI as a nifty optional thing. If you weren't having issues in W7, it was probably because of some ACPI power scaling thing. So, you can try the cpu scaling trick at the website I previously linked. 
You might also have a look at your acpi settings, here is a link:
[https://answers.launchpad.net/ubuntu/+source/yelp/+question/21703](https://answers.launchpad.net/ubuntu/+source/yelp/+question/21703)

so maybe you can try fan control: 
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

also show us:
```

lsmod | grep fan
dmesg | grep cooling
dmesg | grep acpi

 
```
show us output from there.

---

### Post by aditya08 on 2011-04-25
> **conradin said:**
> Windows makes use of ACPI in such a way that is integrated into every part of the OS and nearly impossible to disable. Linux on the other hand views ACPI as a nifty optional thing. If you weren't having issues in W7, it was probably because of some ACPI power scaling thing. So, you can try the cpu scaling trick at the website I previously linked. 
You might also have a look at your acpi settings, here is a link:
[https://answers.launchpad.net/ubuntu/+source/yelp/+question/21703](https://answers.launchpad.net/ubuntu/+source/yelp/+question/21703)

so maybe you can try fan control: 
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

also show us:
```

lsmod | grep fan
dmesg | grep cooling
dmesg | grep acpi

 
```
show us output from there.
Below is out of the command.

tanu@tanu-Studio-1555:~$ lsmod | grep fan
tanu@tanu-Studio-1555:~$ dmesg | grep cooling
[   11.934155] acpi device:02: registered as cooling_device2
tanu@tanu-Studio-1555:~$ dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.680934] ACPI: acpi_idle registered with cpuidle
[   11.934155] acpi device:02: registered as cooling_device2
tanu@tanu-Studio-1555:~$ 

Does all ubuntu users need to do chnage ACPI configuration? My fear is it seems to tricky to change those setting and at the end it may not resolve the issue.

---

