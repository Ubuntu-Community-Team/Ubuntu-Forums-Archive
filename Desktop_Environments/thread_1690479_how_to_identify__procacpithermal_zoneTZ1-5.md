---
title: "how to identify  /proc/acpi/thermal_zone/TZ1-5"
date: 2011-02-18
forum: Desktop Environments
---

### Post by daxbau on 2011-02-18
Hi everyone.

Id like to identify my thermalzones from
 >  cat /proc/acpi/thermal_zone/TZ[1-5] :confused:

here is my info 
> 
MY TEMPERATURE
[QUOTE]
root@HP-Compaq-8510w:~# cat /proc/acpi/thermal_zone**/TZ[1-5]/temperature**
temperature:             46 C
temperature:             48 C
temperature:             45 C
temperature:             30 C
temperature:             50 C
> 
AND HER ARE MY TRIPPOINTS
root@HP-Compaq-8510w:~# cat /proc/acpi/thermal_zone**/TZ1/trip_points**
critical (S5):           110 C
passive:                 105 C: tc1=1 tc2=2 tsp=300 devices=CPU0 CPU1 
active[0]:               85 C: devices=C387 
active[1]:               65 C: devices=C388 
active[2]:               60 C: devices=C389 
active[3]:               45 C: devices=C38A 
active[4]:               35 C: devices=C38B 

root@HP-Compaq-8510w:~# cat /proc/acpi/thermal_zone**/TZ2/trip_points**
critical (S5):           105 C
passive (forced):<not set>
active[0]:               100 C: devices=C36F 
active[1]:               75 C: devices=C36A 
active[2]:               65 C: devices=C36B 
active[3]:               60 C: devices=C36C 
active[4]:               45 C: devices=C36D 
active[5]:               35 C: devices=C36E 

root@HP-Compaq-8510w:~# cat /proc/acpi/thermal_zone**/TZ3/trip_points**
critical (S5):           105 C
passive:                 95 C: tc1=1 tc2=2 tsp=300 devices=CPU0 CPU1 

root@HP-Compaq-8510w:~# cat /proc/acpi/thermal_zone**/TZ4/trip_points**
critical (S5):           110 C
passive:                 60 C: tc1=1 tc2=2 tsp=300 devices=CPU0 CPU1 

root@HP-Compaq-8510w:~# cat /proc/acpi/thermal_zone**/TZ5/trip_points**
critical (S5):           110 C
passive (forced):<not set>
root@HP-Compaq-8510w:~# 
[/QUOTE]

---

