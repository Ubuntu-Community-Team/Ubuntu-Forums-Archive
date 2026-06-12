---
title: "Unity DE"
date: 2021-02-09
forum: Desktop Environments
---

### Post by eipapp on 2021-02-09
Hello,

I installed the Unity DE in my Ubuntu 20.04 LTS. I log on ok and initially it seems to be working fine then suddenly it locks up and I have to reboot.
This seem to happen each time I open an application, ex. software center, settings, etc. 
Does anyone know how to resolve this issue ?

Much thanks,
Bruce

---

### Post by ActionParsnip on 2021-02-10
Do other desktop environments work OK?

---

### Post by ajgreeny on 2021-02-10
Give us more detailed information.
How did you install unity and from where?
What hardware do you have? Show us the output of command ***inxi -Fzx*** which will tell us much more.
Which DE did you start with?

---

### Post by eipapp on 2021-02-10
I installed from LinuxH20.com
Comand Line:
sudo apt update
sudo apt install ubuntu-unity-desktop
```
inxi -Fzx
System:
  Kernel: 5.8.0-41-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop System: Hewlett-Packard product: HP Compaq Elite 8300 SFF 
  v: N/A serial: <filter> 
  Mobo: Hewlett-Packard model: 3397 serial: <filter> UEFI: Hewlett-Packard 
  v: K01 v02.90 date: 07/16/2013 
CPU:
  Topology: Quad Core model: Intel Core i7-3770 bits: 64 type: MT MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 8192 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 54278 
  Speed: 1636 MHz min/max: 1600/3900 MHz Core speeds (MHz): 1: 1875 2: 1597 
  3: 1612 4: 1612 5: 1858 6: 1655 7: 1596 8: 1649 
Graphics:
  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics 
  vendor: Hewlett-Packard driver: i915 v: kernel bus ID: 00:02.0 
  Display: wayland server: X.Org 1.20.9 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) 
  v: 4.2 Mesa 20.2.6 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  vendor: Hewlett-Packard driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.8.0-41-generic 
Network:
  Device-1: Intel 82579LM Gigabit Network vendor: Hewlett-Packard 
  driver: e1000e v: 3.2.6-k port: f080 bus ID: 00:19.0 
  IF: eno1 state: down mac: <filter> 
  Device-2: Realtek type: USB driver: rtl88x2bu bus ID: 1-1.4:3 
  IF: wlx74ee2afd013f state: up mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 19.13 GiB (4.1%) 
  ID-1: /dev/sda vendor: Seagate model: ST500DM002-1BD142 size: 465.76 GiB 
Partition:
  ID-1: / size: 217.67 GiB used: 19.12 GiB (8.8%) fs: ext4 dev: /dev/sda3 
Sensors:
  System Temperatures: cpu: 31.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 288 Uptime: 27m Memory: 7.65 GiB used: 2.33 GiB (30.5%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38
```

---

### Post by ajgreeny on 2021-02-10
I did not like unity or gnome desktops but to answer your question a bit more fully have a read through the answer at [https://askubuntu.com/questions/1250788/how-can-i-add-ubuntu-unity-desktop-to-existing-ubuntu-20-04-installation](https://askubuntu.com/questions/1250788/how-can-i-add-ubuntu-unity-desktop-to-existing-ubuntu-20-04-installation) which appears to give more detail than I knew was needed.

I have no experience of adding unity to 20.04 so can not give you any details of potential problems but there is a forum thread regarding all the various flavours of Ubuntu, official and unofficial, with the information about unity at [https://ubuntuforums.org/showthread.php?t=2415676&p=13848097&viewfull=1#post13848097](https://ubuntuforums.org/showthread.php?t=2415676&p=13848097&viewfull=1#post13848097)

Good luck, but bear in mind that unity is one of the now unofficial flavoiurs of DE so your support in the forum may be a bit limited as few users now run unity when compared with the other flavours.

---

### Post by mc4man on 2021-02-11
unity does not work on wayland so you're not using it, at least according to the inxi you posted.
> Graphics:
  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics 
  vendor: Hewlett-Packard driver: i915 v: kernel bus ID: 00:02.0 
  Display: wayland server: X.Org 1.20.9 driver: modesetting 
Try logging into unity from login screen.

---

### Post by grahammechanical on 2021-02-11
Unity 7 is not in the Ubuntu 20.04 repositories. At least I do not think so. Which why you had to download it from somewhere else. I cannot gain access to LinuxH20.com. There is a respin of Ubuntu called Ubuntu Unity. It is a distribution. It is built on to Ubuntu 20.04 and there is a better chance of it working acceptably. At least it installs in the traditional Ubuntu way and it seems to work fine based on my limited experience with it.

[https://ubuntuunity.org/2020/06/05/ubuntu-unity-20-04-v4-released/](https://ubuntuunity.org/2020/06/05/ubuntu-unity-20-04-v4-released/)

Regards

---

