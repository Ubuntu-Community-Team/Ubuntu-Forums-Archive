---
title: "Minecraft running slow on Nvidia 1060"
date: 2018-07-30
forum: Gaming &amp; Leisure
---

### Post by dexterisawesome on 2018-07-30
Processor: i5
GPU: Nvidia 1060
Driver: llvmpipe (LLVM 6.0, 256 bits)
Java: 10.0.1

I am having no problem starting and running minecraft but I think it is not using the Nvidia card because it is running very slow. I have tried both updating to the Nvidia card in the GUI and terminal to no avail. 

Thank you

---

### Post by mIk3_08 on 2018-07-31
Just want to check the specification on your laptop including the O.S;
Open your terminal
install inxi in your system using this command;
```
sudo apt-get install inxi
```
after it was successfully installed;
in terminal type this command
```
inxi -F
```
Then copy paste the result here in thread.

---

### Post by dexterisawesome on 2018-07-31
Ok, i will just do that. my dad posted the last post so ill just foollow your directions

here u go.
```
System:    Host: dexter-G11CD Kernel: 4.15.0-29-generic x86_64 bits: 64 Desktop: Gnome 3.28.2
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: G11CD v: Rev 1.xx serial: N/A
           UEFI: American Megatrends v: 0802 date: 02/03/2016
CPU:       Quad core Intel Core i5-6400 (-MCP-) cache: 6144 KB
           clock speeds: max: 3300 MHz 1: 2400 MHz 2: 2311 MHz 3: 2360 MHz 4: 2400 MHz
Graphics:  Card: NVIDIA GP106 [GeForce GTX 1060 6GB]
           Display Server: x11 (X.Org 1.19.6 ) driver: nouveau Resolution: 1920x1080@60.00hz
           OpenGL: renderer: NV136 version: 4.3 Mesa 18.2.0-devel
Audio:     Card-1 NVIDIA GP106 High Def. Audio Controller driver: snd_hda_intel
           Card-2 Intel Sunrise Point-H HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-29-generic
Network:   Card-1: Realtek RTL8821AE 802.11ac PCIe Wireless Network Adapter driver: rtl8821ae
           IF: wlp3s0 state: up mac: b0:c0:90:b1:62:cd
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller driver: r8169
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: 34:97:f6:81:f0:ee
Drives:    HDD Total Size: 1762.4GB (4.9% used)
           ID-1: /dev/sda model: HFS512G32MND size: 512.1GB
           ID-2: /dev/sdb model: TOSHIBA_DT01ACA1 size: 1000.2GB
           ID-3: /dev/sdc model: WDC_WD2500BEVS size: 250.1GB
Partition: ID-1: / size: 228G used: 81G (38%) fs: ext4 dev: /dev/sdc2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 253 Uptime: 11:50 Memory: 9122.7/15970.0MB Client: Shell (bash) inxi: 2.3.56 
```
ok there

i also have a linux distro on this computer.... so could it possibly be that? or could it be because i run linux on a small harddrive?

---

### Post by mIk3_08 on 2018-07-31
I think this issue involves fps
Did you already install Java in you Ubuntu system?
if not just follow the instruction below;

Install the Default OpenJDK
First, update the package index to the latest version:
```
sudo apt update
```
Install Java
```
sudo apt install default-jdk
```
Verify the Java installation
```
java -version
```
Output
```
Openjdk version "10.0.1" 2018-04-17
OpenJDK Runtime Environment (build 10.0.1+10-Ubuntu-3ubuntu1)
OpenJDK 64-Bit Server VM (build 10.0.1+10-Ubuntu-3ubuntu1, mixed mode)
```
if it needs to install OpenJDK 8
here's the command;
```
sudo apt update
sudo apt install openjdk-8-jdk
```

---

### Post by mastablasta on 2018-08-01
```
driver: nouveau Resolution: 1920x1080@60.00hz
```

check if you have nvidia driver installed and used.

[https://askubuntu.com/questions/68028/how-do-i-check-if-ubuntu-is-using-my-nvidia-graphics-card](https://askubuntu.com/questions/68028/how-do-i-check-if-ubuntu-is-using-my-nvidia-graphics-card)

---

### Post by sgian on 2018-08-04
I believe mastablasta is on the right track.  You are using the open source nouveau driver for your graphics card, so it is not at full potential.  I have been using the GT 710 cards on my pc's and vanilla minecraft runs fine without lag on them when I use the NVIDIA proprietary graphics driver.

To install the proprietary NVIDIA driver, look for the "Software and Updates" app and open it.  (Keep in mind that I am going from memory since I am on KDE instead of Gnome, so the names might be slightly off.)  Then near the right hand side, there is a tab called "Drivers" or something like that.  Click that tab, and there you can install the NVIDIA drivers with the graphical interface.

---

