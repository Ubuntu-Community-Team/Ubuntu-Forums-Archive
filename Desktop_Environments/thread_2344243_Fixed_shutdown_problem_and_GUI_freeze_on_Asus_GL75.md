---
title: "Fixed shutdown problem and GUI freeze on Asus GL752W laptop"
date: 2016-11-23
forum: Desktop Environments
---

### Post by fenrice on 2016-11-23
Computer specs for searchability. I installed laptop-power-tools because my machine was taking over 1.5 minutes to shutdown (systemd had to timeout after a shutdown -h or GUI powerdown) . The solution was that "laptop-power-tools" were missing. I'm not sure what happened there or why they were missing. I had to update from 16.04 to 16.10 also, because my laptop was hanging every couple of days (GUI and tty hang, no response from mouse or keyboard, not even ctrl-alt-f* keys would do anything). I just thought that I would capture it here for anyone else experiencing such issues. Upgrading to 16.10 and laptop-power-tools fixed all my issues and it has been rock solid for over a couple of weeks. I'm hoping this helps the community.

Here is a hardware dump from inxi -Fx to help future searchers. 

```
System:   Host: freyr 
Desktop: KDE Plasma 5.7.5 (Qt 5.6.1) Distro: Ubuntu 16.10
Machine:  System: ASUSTeK (portable) product: GL752VW v: 1.0
Mobo: ASUSTeK model: GL752VW v: 1.0                                           
UEFI [Legacy]: American Megatrends v: GL752VW.211 date: 01/12/2016            
Battery   BAT0:charge: 44.9 Wh 100.0% condition: 44.9/48.0 Wh (94%)                    
model: ASUSTeK ASUS status: Discharging                                       
CPU:      Quad core Intel Core i7-6700HQ (-HT-MCP-) cache: 6144 KB                      
flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 20736             
clock speeds:max: 2601 MHz 1: 900 MHz 2: 1200 MHz 3: 1300 MHz 4: 800 MHz     
5: 800 MHz 6: 900 MHz 7: 900 MHz 8: 800 MHz                                   
Graphics: Card-1: Intel HD Graphics 530 bus-ID: 00:02.0                                 
Card-2: NVIDIA GM107M [GeForce GTX 960M] bus-ID: 01:00.0                      
Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.02hz     
GLX Renderer: GeForce GTX 960M/PCIe/SSE2                                      
GLX Version: 4.5.0 NVIDIA 370.28 Direct Rendering: Yes                        
Audio:    Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3     
Sound: Advanced Linux Sound Architecture  
Network:  Card-1: Intel Wireless 7265 driver: iwlwifi bus-ID: 02:00.0                   
IF: wlp2s0 
Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller     
driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 03:00.1                        
IF: enp3s0f1 state: down 
Drives:   HDD Total Size: 512.1GB (27.3% used)                                          
ID-1: /dev/sda model: SanDisk_SD8SB8U5 size: 512.1GB temp: 36C                
Partition:ID-1: / size: 454G used: 116G (27%) fs: ext4 dev: /dev/sda1                   
ID-2: swap-1 size: 17.07GB used: 0.00GB (0%) fs: swap dev: /dev/dm-0          
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present                   
Sensors:  System Temperatures: cpu: 45.0C mobo: N/A gpu: 0.0:47C                        
Fan Speeds (in rpm): cpu: 1900                                                
Info:     Processes: 312 Uptime: 9 min Memory: 2777.3/15942.0MB                         
Init: systemd runlevel: 5 Gcc sys: 6.2.0 Client: Shell (zsh 5.2) inxi: 2.3.1 
```

---

