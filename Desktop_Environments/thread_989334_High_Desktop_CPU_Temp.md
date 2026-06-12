---
title: "High Desktop CPU Temp"
date: 2008-11-21
forum: Desktop Environments
---

### Post by menar003 on 2008-11-21
I have a dual boot system with Vista, and Ubuntu. I recently installed lm sensors to detect my CPU temp in Ubuntu and it was idling around 50C; while in Vista it idles at 30C. This is in both Ubuntu 8.04 and 8.10. I looked at the CPU performance and it was under 5% on both cores. Then I installed Linux Mint 5 over the Ubuntu install, added lm sensors, and my CPU temp was 30C! Does anyone know something that is installed on default on a Ubuntu system that is not on Linux Mint that might cause this problem? 



CPU: E6600
Motherboard: Asus P5NE-SLI
Video: 8800GTS 320MB

---

### Post by hictio on 2008-11-21
Did you detected any process, via top, or similar, that might have been using any CPU?
The temperatures that you report, are after using the system for a while, or just out of a boot?

---

### Post by menar003 on 2008-11-21
The temperatures are after it boots up and it sits idle.  After the initial high temps from booting up, it will stay at the same temp for as long as I have it running on Ubuntu/Vista/Mint. On Ubuntu, none of the processes running report high CPU use. I haven't installed any crazy programs either; after I noticed it on 8.04, I installed a fresh copy of 8.10 and immediately installed lm_sensors and got the same results.

---

### Post by GriZzlEnLS on 2008-11-23
Are you using Intel or AMD? Single, Dual, Triple, or quad? Also what temp program are you using in Windows and in Linux?

---

### Post by menar003 on 2008-11-29
I have an Intel Core 2 Duo E6600 (2.4Ghz) (2 cores). In Windows I am using Core Temp and in Ubuntu and Mint I am using lm_sensors and the sensors applet, I also opened terminal and accessed sensors that way as well.

---

### Post by shuffer on 2009-03-13
I had the same thing on my P4 3.2 HT. I think it's just a discrepancy between the temperature monitor software, to be honest, though this is obviously something that needs checking if you're regularly showing over 85C. Is far as I know, the only things that can affect the temperature of the CPU are running rate, fan speed and ambient room temperature. All these things being equal, the temperature should be consistent.

On my current work desktop, there is a hardware temp readout on the front of the machine and according to this, the Linux Mint installation runs cooler than Vista even with the fan speed lower on that installation, due to the CPU running less.

---

### Post by mika7367 on 2009-03-13
I get so many different temps using different monitoring software that I just set system health/alarms in bios to warn of over heating.I dualboot with vista ultimate 64 and ubuntu 8.10 intrepid 64.

Processor AMD Phenom Q9850 BE Quad @ 2.7Ghz (oc'd a little)
Video Sapphire HD 4850 (amd/ati),also oc'd a little via catalyst overdrive.
Mobo Gigabyte GA-MA78GPM-DS2H.(this mobo comes with software to check via bios when overclocking and allows you to set predifined temps for cpu,gpu,hdd etc.)

---

### Post by Psyphre on 2009-03-13
i think menar is trying to say that both ubuntu and mint use lm sensors which are the same program, so why the discrepency?

---

### Post by dccrens on 2009-05-26
I have the same issue. This is on both Jaunty and Intrepid systems that dual boot windows xp. Under Ubuntu temps (using lm-sensors) runs in the high 50s to low 60s for core0 and core1 and read in the 30s for the "cpu"... In windows there the core0 and core1 temp run in the 40s with the "cpu" temp reading in the 30s...

---

### Post by ashwinhgtx on 2009-07-01
Even I have the same problem. I did a lot of googling but most of the results are from the Ubuntu forum threads. I have a feeling that this is an Ubuntu specific issue. Almost all Ubuntu versions since Hardy seem to have this problem, other distros and windows seem to be fine.
I have a core duo in an IBM R60 laptop.

---

