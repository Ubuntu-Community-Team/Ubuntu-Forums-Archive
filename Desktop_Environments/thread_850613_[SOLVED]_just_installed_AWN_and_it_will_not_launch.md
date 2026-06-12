---
title: "[SOLVED] just installed AWN and it will not launch"
date: 2008-07-05
forum: Desktop Environments
---

### Post by vistasucksss on 2008-07-05
does anybody have any suggestions as to why it wont launch when i click system - preferences - awn manager? using hardy

thanks in advance

---

### Post by dje on 2008-07-05
Run the following in a terminal (Applications >> Accessories >> Terminal) and post the output here:
```
awn-manager
```

---

### Post by vistasucksss on 2008-07-05
chris@Cali-PC:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue

---

### Post by dje on 2008-07-05
hmm try restarting awn (right click then 'Close', relaunch at Applications >> Accessories >> Avant Window Navigator). then try opening awn manager again

---

### Post by vistasucksss on 2008-07-05
hey thanks didnt even realize it was in applications (noob mistake) opened it up in applications and then opened the manager.. works fine! im gonna play around with it and make sure! thanks again... while we're at it do you know how i can get the 3D environments that i see all over youtube with the flipping of the desktops and what not? anyways thanks again for the help!!

---

### Post by dje on 2008-07-05
No worries

Have a look in System >> Preferences >> Appearance and in the Visual effects tab. After enabling them you will want to customise the effects so do the following:
```
sudo apt-get install compizconfig-settings-manager
```
Then look under System >> Preferences >> Advanced Desktop Effects Settings

If you cannot enable the effects have a look under System >> Administration >> Drivers Manager and enable any graphics drivers that need to be. Restart if required and try enabling the effects again

hope that helps,
dje

---

### Post by vistasucksss on 2008-07-05
dje thanks alot mate i really appreciate the tips. i installed the app but i cannot seem to get the crazy effects to initiate. is there something i need to do differently? i am pressing alt+ctrl+down for instance and it does nothing.. even restarted my system. do i need to 'create' more desktops perhaps? greatly appreciated.

---

### Post by dje on 2008-07-05
Did you try to enable them in System >> Preferences >> Appearance? If no do that

If that doesn't work did you look in System >> Administration >> Drivers Manager to see if any drivers need installing

If none of the above works please post the output of:
```
sudo lspci
```
This lists all of your hardware

dje

---

### Post by vistasucksss on 2008-07-06
i am sure i am doing something wrong... maybe i just dont know how to use it or like you said the drivers arent proper... there is only one driver in the 'hardware drivers' under system == administration it is called "wl" and it is 'enabled' but 'not in use' with a red indicator...

this is the result of my hardware:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
chris@Cali-PC:~$

---

### Post by vistasucksss on 2008-07-06
OK problem solved.. i figured it out lol im drawing flames on my desktop as we speak... thanks for your help dje.... one last thing for anyone who wants to help... how do i create a 'cube' desktop or have multiple desktops.. right now it is only two seperate desktops. thanks again.

---

### Post by vistasucksss on 2008-07-06
OKAY! found the answer to my problem here and for anyone else who comes across this the FAQ has all your answers lol.. go figure... thanks again to dje and everyone else helping out noobs in the forums. you guys are awesome and dont forget about the noooobss!!!!

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)     <-- HAS ALL OF THE ANSWERS FOR CUSTOMIZING DESKTOP AND EFFECTS WITH COMPIZ FUSION.

---

