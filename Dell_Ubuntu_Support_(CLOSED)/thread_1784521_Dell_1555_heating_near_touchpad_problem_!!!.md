---
title: "Dell 1555 heating near touchpad problem !!!"
date: 2011-06-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anubhav2k on 2011-06-17
i have recently installed ubuntu 11.04 on my dell studio 1555 , double boot with win 7..... 
when i use win 7 it doesnt heat up as much as in ubuntu 11.04 ... and fan keeps on at high speed on ubuntu , but not on win7 ....

my config is

core 2 duo 2ghz
4gb ram
320gb hdd
512mb ati graphics

is my config not suitable for ubuntu 11.04 or whats the problem, please help .... my laptop may get damaged due to overheating ???

---

### Post by mikewhatever on 2011-06-18
You should definitely check the temperatures to make sure they are within acceptable bounds. For the CPU, install the **acpi** package, then run **acpi -t** in a terminal window. For the HDD, use the preinstalled Disk Utility, select the HDD and click SMART Data, the temperature is listed at top left. I am not sure how to easily check the ATI card. Is there any utility provided by the ATI driver? If not you may need to use lm-sensors.

---

