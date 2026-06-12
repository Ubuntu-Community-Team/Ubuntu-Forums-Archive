---
title: "Problems after upgrading to Dapper..."
date: 2006-06-27
forum: Desktop Environments
---

### Post by 1337 on 2006-06-27
Hello I upgraded Ubuntu Breeze some time ago after 1st June to Dapper, in first weeks I didnt have time to notice problems exept one. When system boot in no-splash or dmesg mode I see error text something like that: 

[B]sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[/B]

I got ECS K7S5A MOBO with SIS chipset, computer seems to working fine even with this error but going ahead it's not obvious. My second problem is that my pc seems to freeze when I'm using 3D accelerated apps like Enemy Territory, Quake or Screensavers after some time of using them, screen just freez and last sound played is in the loop (I have nVidia Geforce 5200 card). Keyboard isn't responding only Hardreset left ](*,). I checked the system logs at the hours when pc freeze but I didnt saw nothing important there. 
In Ubuntu Breeze everything were working fine, computer didn't froze or something, if you have some idea, sugestion or even solution I will be grateful.

My PC
AMD DURON 1800
ECS K7s5a MOBO
512 MB DDR RAM Kingson
nVidia GeForce FX 5200 128bit 128MB DDR
Sound Blaster Live! Value
WDC Caviar 80GB 8MB Cache Hard Disk
 
Best Regards

---

### Post by rai4shu2 on 2006-06-27
Have you installed nvidia-glx?

---

### Post by 1337 on 2006-06-27
[QUOTE=rai4shu2]Have you installed nvidia-glx?[/QUOTE]

Yes all needed drivers are installed nvidia-glx with restricted kernel modules and such.

Best Regards

---

### Post by rai4shu2 on 2006-06-27
Does it crash when running glxgears?

---

### Post by 1337 on 2006-06-27
I ran glxgears for about 5 minutes but I didnt notice any freeze, maybe cause I it was short ammount of time but I belive that it can't cause freeze. Here are fps results which I got from glxgears if that can be helpful somehow :)

[B]$ glxgears -printfps
16151 frames in 5.0 seconds = 3230.134 FPS
14581 frames in 5.0 seconds = 2916.133 FPS
15625 frames in 5.0 seconds = 3124.918 FPS
[/B]

Regards

---

### Post by rai4shu2 on 2006-06-27
Have you tried running the "memtest" from the GRUB menu?

---

### Post by 1337 on 2006-06-27
[QUOTE=rai4shu2]Have you tried running the "memtest" from the GRUB menu?[/QUOTE]

Yeah, memory is fine as I said before I notice those problems after upgrading from Breezy to Dapper, before everything was fine. PC dont freeze while doing "normal" hard tasks for CPU @ 100% usage i.e. ripping mp3 from favourite cd and stuff. It only hangs while playing games and using screensavers.

Regards

---

### Post by 1337 on 2006-06-27
Today I reinstalled my Ubuntu Dapper to Xubuntu Dapper and Problems STILL exists... It's for sure not hardware problem.

---

### Post by 1337 on 2006-09-19
UPDATE - This is old stuff but I've fixed the problem I had problems with computer overheating in summer my cooler just wasnt cooling enough I saw that when I installed LMsensors the cooler speed was really low and temperature on cpu was kinda high.

Regards

---

