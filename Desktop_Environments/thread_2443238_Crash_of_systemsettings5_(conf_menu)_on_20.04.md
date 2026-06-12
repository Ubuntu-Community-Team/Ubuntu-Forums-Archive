---
title: "Crash of systemsettings5 (conf menu) on 20.04"
date: 2020-05-13
forum: Desktop Environments
---

### Post by spoke999 on 2020-05-13
Hi!

Til I migrate from 19.10 to 20.04 I can't open "Configuration menu" (systemsettings5).
It crashes with this message :

```
QQmlEngine::setContextForObject(): Object already has a QQmlContext

```

I try to restart with an empty "~/;config" directory without success.

Here is some configuration data :

```
System:    Kernel: 5.4.0-29-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: KDE Plasma 5.18.4 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Laptop System: ASUSTeK product: X555UB v: 1.0 serial: <filter> 
           Mobo: ASUSTeK model: X555UB v: 1.0 serial: <filter> UEFI: American Megatrends v: X555UB.204 
           date: 10/18/2015 
Battery:   ID-1: BAT0 charge: 26.3 Wh condition: 26.9/37.3 Wh (72%) model: ASUSTeK ASUS Battery status: Not charging 
           Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M315/M235 charge: 5% (should be ignored) 
           status: Discharging 
CPU:       Topology: Dual Core model: Intel Core i7-6500U bits: 64 type: MT MCP arch: Skylake rev: 3 
           L2 cache: 4096 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 20799 
           Speed: 500 MHz min/max: 400/3100 MHz Core speeds (MHz): 1: 500 2: 500 3: 500 4: 500 
Graphics:  Device-1: Intel Skylake GT2 [HD Graphics 520] vendor: ASUSTeK driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GM108M [GeForce 940M] vendor: ASUSTeK driver: N/A bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.8 driver: intel resolution: 1600x900~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2) v: 4.6 Mesa 20.0.4 direct render: Yes 
Audio:     Device-1: Intel Sunrise Point-LP HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
           Sound Server: ALSA v: k5.4.0-29-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK driver: r8169 v: kernel 
           port: d000 bus ID: 02:00.0 
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Realtek RTL8723BE PCIe Wireless Network Adapter vendor: Lite-On driver: rtl8723be v: kernel 
           port: c000 bus ID: 03:00.0 
           IF: wlp3s0 state: up mac: <filter> 
           IF-ID-1: docker0 state: down mac: <filter> 
Drives:    Local Storage: total: 931.51 GiB used: 435.14 GiB (46.7%) 
           ID-1: /dev/sda vendor: HGST (Hitachi) model: HTS541010A9E680 size: 931.51 GiB 
Partition: ID-1: / size: 908.50 GiB used: 434.99 GiB (47.9%) fs: ext4 dev: /dev/sda2 
           ID-2: swap-1 size: 7.90 GiB used: 142.2 MiB (1.8%) fs: swap dev: /dev/sda3 
Sensors:   System Temperatures: cpu: 40.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 2600 
Info:      Processes: 200 Uptime: 17h 19m Memory: 7.67 GiB used: 1.81 GiB (23.6%) Init: systemd runlevel: 5 
           Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 inxi: 3.0.38 

```

---

