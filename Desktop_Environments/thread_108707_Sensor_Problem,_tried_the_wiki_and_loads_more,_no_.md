---
title: "Sensor Problem, tried the wiki and loads more, no joy"
date: 2005-12-26
forum: Desktop Environments
---

### Post by WebLOCH on 2005-12-26
First off, if this post is incorrectly placed, will someone please move it, I guess this could be classified as installation, hardware or just desktop software so I just dropped it here, sorry for any hassle.

I have been trying to configure lm-sensors for two days now, and the best I can get is two small outputs that dump some info about my RAM, however, the thing I am really after is CPU info!

Please bear in mind:
  1) I have followed the Wiki to the letter and it has not worked
  2) I have read the forums already and no post has solved my problem
  3) I will need explicit detail as my prior attempts may have residual effect on solving the problem now

My hardware:
  Intel Pentium D 830 3.0ghz clocked at 3.9-4.0ghz.
  Asus P5WD2 Premium Motherboard

If you need any other details let me know, I shall leave you with the output from 'sensors', I thank you for your time in advance.

------------------------------- 
baris@azazel:~$ sensors
eeprom-i2c-0-52
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR2 SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR2 SDRAM DIMM
Memory size (MB):       512

---

### Post by Dark79 on 2006-01-08
The sensor on the P5WD2 board is W83627EHF. I know this because I have the same board. Unfortunately, it's not supported in Breezy. The only way I got it to work was to download a new kernel, apply patches that gave me the sensor support, recompile, and install the newly patched kernel.

Sorry I can't give you any more info than that. I ditched Ubuntu many months ago on my P5WD2 rig because of the lack of IT8211F IDE controller support. I hear someone got the IT8212 (which also includes the controller I need) working and has detailed steps how to get it working, so I may go back to it soon.

Good luck!

---

### Post by javierfh on 2006-06-07
[QUOTE=Dark79]The sensor on the P5WD2 board is W83627EHF. I know this because I have the same board. Unfortunately, it's not supported in Breezy. The only way I got it to work was to download a new kernel, apply patches that gave me the sensor support, recompile, and install the newly patched kernel.

Sorry I can't give you any more info than that. I ditched Ubuntu many months ago on my P5WD2 rig because of the lack of IT8211F IDE controller support. I hear someone got the IT8212 (which also includes the controller I need) working and has detailed steps how to get it working, so I may go back to it soon.

Good luck![/QUOTE]
Hello,

i have read your post and wonder if you updated to 6.06 and if the sensors were supported there without all the trouble of recompiling kernel, that sounds bit scary to totally newby into linux.

Thanks in advance.

---

