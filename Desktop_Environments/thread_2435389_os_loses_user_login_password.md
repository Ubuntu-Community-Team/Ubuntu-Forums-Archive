---
title: "o/s loses user login password"
date: 2020-01-20
forum: Desktop Environments
---

### Post by vidtek on 2020-01-20
On several occasions my Kubuntu 18.04 install loses the user account and denies login with the correct password.

I login with the root account and change the password to the same one and logout root and login my user and all is well until the next time.

```
tony@linuxmint:~$ inxi -F
System:    Host: linuxmint Kernel: 5.0.12-050012-generic x86_64 bits: 64 Desktop: KDE Plasma 5.12.9
           Distro: Ubuntu 18.04.3 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: STRIX Z270E GAMING v: Rev 1.xx serial: N/A
           UEFI: American Megatrends v: 1302 date: 03/15/2018
Battery    hidpp__0: charge: N/A condition: NA/NA Wh
           hidpp__1: charge: N/A condition: NA/NA Wh
CPU:       Quad core Intel Core i7-7700K (-MT-MCP-) cache: 8192 KB
           clock speeds: max: 4500 MHz 1: 4499 MHz 2: 4500 MHz 3: 4500 MHz 4: 4499 MHz 5: 4499 MHz 6: 4500 MHz
           7: 4499 MHz 8: 4500 MHz
Graphics:  Card: NVIDIA GM206 [GeForce GTX 960]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1920x1080@50.00hz
           OpenGL: renderer: GeForce GTX 960/PCIe/SSE2 version: 4.6.0 NVIDIA 430.50
Audio:     Card NVIDIA Device 0fba driver: snd_hda_intel Sound: ALSA v: k5.0.12-050012-generic
Network:   Card: Intel Ethernet Connection (2) I219-V driver: e1000e
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 
Drives:    HDD Total Size: 9257.8GB (85.8% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 256.1GB                                                        
           ID-2: /dev/sdc model: TOSHIBA_MD04ACA5 size: 5001.0GB                                                      
           ID-3: /dev/sdb model: TOSHIBA_HDWE140 size: 4000.8GB                                                       
Partition: ID-1: / size: 58G used: 25G (45%) fs: ext4 dev: /dev/sda5                                                  
           ID-2: /home size: 73G used: 65G (94%) fs: ext4 dev: /dev/sda6                                              
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present                                                
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A gpu: 27C                                                         
           Fan Speeds (in rpm): cpu: 0                                                                                
Info:      Processes: 319 Uptime: 3 days Memory: 7231.5/15970.9MB Client: Shell (bash) inxi: 2.3.56  
```

Very strange behaviour, an annoyance more than anything.  Anyone got any ideas?

Cheers, Tony.

---

### Post by CelticWarrior on 2020-01-20
> **vidtek said:**
> On several occasions my Kubuntu 18.04 install loses the user account and denies login with the correct password.

I think you're misinterpreting a login loop as a "user account lost"... A login loop can happen for many reasons but user accounts/passwords aren't lost. Very likely you're having issues with .Xauthority or something else similar.

Have you installed drivers for the Nvidia card? If so, how?

---

### Post by deadflowr on 2020-01-20
Sidenote, why are you still on a very old mainline kernel?

---

### Post by vidtek on 2020-01-21
> **CelticWarrior said:**
> I think you're misinterpreting a login loop as a "user account lost"... A login loop can happen for many reasons but user accounts/passwords aren't lost. Very likely you're having issues with .Xauthority or something else similar.

Have you installed drivers for the Nvidia card? If so, how?

Thanks for the reply, I have no idea of the difference between a "login loop" and my symptoms.  The login screen just states "incorrect password".  I know it is correct because for this user account I just use the number "1" for convenience.  I would have a password less login but the auto-shutdown routine of Mythtv requires a password login.

The Nvidia drivers are auto-installed by the installation routine when I tick the "install proprietary drivers"  or something similar on initial install.

I appreciate the help, Tony.

---

### Post by vidtek on 2020-01-21
> **deadflowr said:**
> Sidenote, why are you still on a very old mainline kernel?

I did try the 19.04 update, but ran into driver issues with my tuner card/bluetooth/printer/scanner/wireless and had severe cogging on video so reverted to the LTS 18.04.

---

