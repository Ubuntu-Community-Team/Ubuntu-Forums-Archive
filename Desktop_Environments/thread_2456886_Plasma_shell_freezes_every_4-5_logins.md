---
title: "Plasma shell freezes every 4-5 logins"
date: 2021-01-21
forum: Desktop Environments
---

### Post by vidtek on 2021-01-21
There is an unexplained as yet hang on login after the plasma shell loads every 4th or 5th login.  The mouse pointer works but will not activate anything.  The only way to get back to a working desktop is to reboot or go to another shell and kill the xorg process using top. 
[B][I][COLOR="#000080"]
To the admin moderators who put my post into jail please see that I am using Ubuntu Studio NOT linux MINT!!!!!  linuxmint is my computer name.[/COLOR][/I][/B]
 My system:

    Code:

    tony@[COLOR="#FF0000"]linuxmint[/COLOR]:~$ inxi -F
    System:    Host: [COLOR="#FF0000"]linuxmint[/COLOR] Kernel: 5.8.0-38-lowlatency x86_64 bits: 64 Desktop: KDE Plasma 5.19.5 
               **[COLOR="#00FF00"]Distro: Ubuntu 20.10 (Groovy Gorilla) [/COLOR]**
    Machine:   Type: Desktop Mobo: ASUSTeK model: STRIX Z270E GAMING v: Rev 1.xx serial: <superuser/root required> 
               UEFI: American Megatrends v: 1302 date: 03/15/2018 
    CPU:       Info: Quad Core model: Intel Core i7-7700K bits: 64 type: MT MCP L2 cache: 8192 KiB 
               Speed: 800 MHz min/max: 800/4500 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 5: 800 6: 800 
               7: 800 8: 800 
    Graphics:  Device-1: NVIDIA TU116 [GeForce GTX 1660] driver: nvidia v: 460.32.03 
               Device-2: GEMBIRD Generic UVC 1.00 camera [AppoTech AX2311] type: USB driver: uvcvideo 
               Display: x11 server: X.Org 1.20.9 driver: nvidia resolution: 1920x1080~60Hz 
               OpenGL: renderer: GeForce GTX 1660/PCIe/SSE2 v: 4.6.0 NVIDIA 460.32.03 
    Audio:     Device-1: NVIDIA TU116 High Definition Audio driver: snd_hda_intel 
               Device-2: TBS DVB Tuner PCIe Card driver: TBSECP3 driver 
               Sound Server: ALSA v: k5.8.0-38-lowlatency 
    Network:   Device-1: Intel Ethernet I219-V driver: e1000e 
               IF: enp0s31f6 state: up speed: 1000 Mbps duplex: full mac: 
    Drives:    Local Storage: total: 8.42 TiB used: 7.00 TiB (83.1%) 
               ID-1: /dev/sda vendor: Samsung model: SSD 840 PRO Series size: 238.47 GiB 
               ID-2: /dev/sdb vendor: Toshiba model: HDWE140 size: 3.64 TiB 
               ID-3: /dev/sdc vendor: Toshiba model: MD04ACA500 size: 4.55 TiB 
    Partition: ID-1: / size: 47.83 GiB used: 18.20 GiB (38.1%) fs: ext4 dev: /dev/sda5 
               ID-2: /home size: 82.17 GiB used: 7.94 GiB (9.7%) fs: ext4 dev: /dev/sda6 
    Swap:      Alert: No Swap data was found. 
    Sensors:   System Temperatures: cpu: 31.0 C mobo: N/A gpu: nvidia temp: 38 C 
               Fan Speeds (RPM): N/A gpu: nvidia fan: 0% 
    Info:      Processes: 331 Uptime: 1h 13m Memory: 15.57 GiB used: 3.93 GiB (25.2%) Shell: Bash inxi: 3.1.07

   
    Interesting that another user is having the same issue using an AMD processor and graphics, and I am using an Intel CPU and Nvidia graphics. That tells me it is unlikely to be a hardware issue, far more likely to be a plasma issue.......

    Cheers Tony. 

   

    Asus Z270i7 16gb rm 8tb GT1660 TSB6205 Quad tunr Ubnt Studio 21.04 Greedy/Win 10 Be/FE mythtv 0.32Homerun dual netwk tunr 55¨ Smsng ES8000 Lap Smsng NP R580 i5 nvidia linux Ultimate/Win 10

---

