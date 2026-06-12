---
title: "partial acpi installation? :-)"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Arnaud_B on 2006-07-19
Hi,
You probably already heard about it concerning laptops but this actually happen on a new desktop I got... :confused: 
So here is the problem...
This is the message kde gives:
> 
Your computer seems to have a partial ACPI installation. ACPI was probably enabled, but some of the sub-options were not - you need to enable at least 'AC Adaptor' and 'Control Method Battery' and then rebuild your kernel.

I know it looks bad but well it's just a standard kde message when kde cannot understand the acpi implementation I guess... but what follow is better ;-)
> 
arnaud@arnaudpc:~$ cat /proc/acpi/thermal_zone/*
cat: /proc/acpi/thermal_zone/*: No such file or directory

and...
> 
arnaud@arnaudpc:~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no

Basically there is virtually no acpi support :-(

So facing this problem I only see 3 options:
1/ recompiling my kernel with new acpi patch... from [http://acpi.sourceforge.net/download.html](http://acpi.sourceforge.net/download.html) 
2/ recompiling my kernel using a vanilla kernel + previous acpi patches + Kolivas patches...
3/ forgetting about acpi and coming back to apm, I am not sure it's possible the machine is new... and I would not like it much...
4/ trashing the pc... nono kidding this is not an option :-)

I don't mind any of the firt two but before starting my numerous compilings I would like to have some feeback if possible... :-)

Any ideas? suggestions? what do you think of these options? are there others?

Thanks in advance for your help...

A.

PS: I did not provide outputs of lspci, cat /proc/cpuinfo,etc... not to take too much place but if you want/need to see just ask me please...

---

### Post by Arnaud_B on 2006-07-19
well none of the first two options solved my problem :-( there is really nobody who has a little idea?
Besides that everything works great but I'm not sure it is safe not to be able to check the temperature among other things... and scalling is probably not working either...
Ideas?
A.

---

### Post by Arnaud_B on 2006-07-19
In case it might help powernowd does not start:
> 
arnaud@arnaudpc:~$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 1 scalable unit:  -- 4 'CPUs' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]

however...
> 
arnaud@arnaudpc:~$ dmesg | grep acpi
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[17179587.008000] ibm_acpi: ec object not found
[17179587.040000] pcc_acpi: loading...


I no longer know where to look for answers... Still no idea?
A.

---

### Post by kinematic on 2006-07-19
The whole acpi thing never made much sense to me also.
I installed sysv-rc-conf and acpi isn't checked but the acpi services are started and stopped at boot and shutdown and cpu scaling and power managment work just fine.
On my PCLinuxOS install acpi IS enabled by default and cpu scaling also works 
as well as other power managment.
And I don't notice any real performance differences between the 2.

---

### Post by Arnaud_B on 2006-07-19
Thanks for your answer...
But what does the fact that /proc/acpi/* is empty could mean? Do you see something for instance in /proc/acpi/thermal_zone ? for me it's empty meaning I cannot even monitor the temperature...
Any ideas?
A.

---

### Post by kinematic on 2006-07-19
i have nothing in there as well so i cant help on that one.

---

### Post by Arnaud_B on 2006-07-19
ok... Thanks for your help... I guess I'll stay like that until I figure out why this thing isn't working ;-)
A.

---

