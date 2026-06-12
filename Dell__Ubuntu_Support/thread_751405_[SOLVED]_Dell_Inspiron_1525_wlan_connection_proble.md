---
title: "[SOLVED] Dell Inspiron 1525 wlan connection problems"
date: 2008-04-10
forum: Dell  Ubuntu Support
---

### Post by jsjrod on 2008-04-10
I just got a new Dell Inspiron 1525 and the first thing i did was erase Vista and replaced it with "Gutsy".  The inspiron I have has a built-in wireless card (iwl4965 is what comes up when I run command "sudo lsmod | egrep 'Module|iwl|ipw').   Everytime I reboot my computer or when it shuts down due to battery being low, it will not connect to the internet.  I tried the command (sudo ifconfig wlan0 down... then sudo ifconfig wlan0 up) and had no luck.  I also tried unchecking the wireless network  box in network settings and then checking it again.  I also tried the things listed in this forum ([click here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues")) and replacing it with the information applicable to my system, again no luck.  So far the only fix action is to open up the network settings and remove and replace my network password.  Is there any way to stop this from happening.  Any help will be greatly appreciated.

---

### Post by notwen on 2008-04-10
> **jsjrod said:**
> I just got a new Dell Inspiron 1525 and the first thing i did was erase Vista and replaced it with "Gutsy".  The inspiron I have has a built-in wireless card (iwl4965 is what comes up when I run command "sudo lsmod | egrep 'Module|iwl|ipw').   Everytime I reboot my computer or when it shuts down due to battery being low, it will not connect to the internet.  I tried the command (sudo ifconfig wlan0 down... then sudo ifconfig wlan0 up) and had no luck.  I also tried unchecking the wireless network  box in network settings and then checking it again.  I also tried the things listed in this forum ([click here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues")) and replacing it with the information applicable to my system, again no luck.  So far the only fix action is to open up the network settings and remove and replace my network password.  Is there any way to stop this from happening.  Any help will be greatly appreciated.

The things you attempted from Dell's Linux Wiki only applied to Intel ipw3945 wireless, not your 4965.  You may want to remove the blacklist for ipw4965(did you even blacklist the 4965 or the 3945?) and revert back to the ipw module.  Now to address your issue, do you have your connection set manually or do you let it roam?  I personally let my connection(Intel 3945) roam and it automatically connects to it's previous connection when reboot/power up should that SSID be within range.

When you installed Ubuntu did you install it using a vanilla Ubuntu install or did you use Dell's custom Ubuntu image provided for your specific model.  Check [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO") for the custom images.  (I cannot recall if the Vista-loaded 1525 offers an option for the Nvidia card or not, so hopefully you have the Intel X3100 chipset).

---

### Post by jsjrod on 2008-04-14
Thanks for pointing this out.  I don't know what I was thinking.  This is the first time I have used wireless with linux.  It has worked ever since I enabled roaming mode.  Sorry it took me so long to respond.

---

### Post by notwen on 2008-04-14
Np, glad all turned out well for you.  Mark this thread solved if your issue has been sufficiently resolved.  =]

---

