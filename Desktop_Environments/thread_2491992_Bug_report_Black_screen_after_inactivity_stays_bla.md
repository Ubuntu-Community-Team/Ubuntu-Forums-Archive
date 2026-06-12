---
title: "Bug report: Black screen after inactivity stays black forever"
date: 2023-10-27
forum: Desktop Environments
---

### Post by dan1119999111 on 2023-10-27
Hi,

(I tried to file a bug-report on launchpad by clicking on "Report a bug", but it doesn't work and gets me only to the wiki, which I don't understand. I tried the Ubuntu-bug IRC channel, but it doesn't work out of the box with TOR and the wiki for making it work with TOR I don't understand. It's almost as if Ubuntu doesn't respect your privacy and doesn't really want bugs to be submitted, judging by how hard it is. I thought Ubuntu is all about "just works"...or was that just a lie?)

So I submitted a bug report at the Wayland-gitlab-page, but they said it's a Ubuntu problem and I should file a bug report at Ubuntu. The copy of it and still a problem:

"Hi,

I don't know if this is the right place, because usually I don't do stuff like this (don't work in IT) and English is not even my first foreign language, but my second....so please try to keep everything simple for me.

So I think I found a bug or something like this: On my Ubuntu 22.04.03 I have set the time for my screen to go black/shut off in case of inactivity in the energy settings (to save energy) to 5 minutes. So I go back to my computer after 10 minutes or so and the screen is black like it should be. Problem is, that I can't turn the screen on or what I really mean is: get back to the desktop. I tried to type many keys on my keyboard or move the mouse, but nothing works, the screen stays black. I had to disconnect my whole computer from power. I recreated this problem 3 times.
Then I switched to X11 or how it is called....actually it's just called "Ubuntu" and "Ubuntu with Wayland" at the Ubuntu login screen, in which the option just "Ubuntu" is for X11...and no problems with X11.

So now you gotta tell me which information you need from me....and like I said above, please try to keep everything simple. Not only because of the foreign language but also because I don't really use the terminal...."


Thx for any help in advance

---

### Post by crixtux on 2023-12-21
Hello,

I have the same problem here. As mentioned it only happens with Wayland not with x11. 

Managed to get out of this by putting my system to sleep instead of disconnecting the whole computer. (My power button is set to do that).

If someone needs more info to work on this please ask.

I have a fresh install with dualboot. (Don't think this matters but anyway)

My system: 

System:
  Kernel: 6.2.0-39-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)

Machine:
  Type: Laptop System: Micro-Star product: GS73 Stealth 8RE v: REV:1.0
    serial: <superuser required>

  Mobo: Micro-Star model: MS-17B5 v: REV:1.0 serial: <superuser required>
    UEFI: American Megatrends v: E17B5IMS.110 date: 05/17/2019

Battery:
  ID-1: BAT1 charge: 49.3 Wh (97.2%) condition: 50.7/65.0 Wh (78.0%)
    volts: 12.7 min: 11.4 model: MSI BIF0_9 status: Not charging

CPU:
  Info: 6-core model: Intel Core i7-8750H bits: 64 type: MT MCP
    arch: Coffee Lake rev: A cache: L1: 384 KiB L2: 1.5 MiB L3: 9 MiB
  Speed (MHz): avg: 3257 high: 4098 min/max: 800/4100 cores: 1: 2200
    2: 2200 3: 4001 4: 2200 5: 4000 6: 3993 7: 2200 8: 2200 9: 4000 10: 4098
    11: 4004 12: 3995 bogomips: 52799
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx

Graphics:
  Device-1: Intel CoffeeLake-H GT2 [UHD Graphics 630] vendor: Micro-Star MSI
    driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GP106M [GeForce GTX 1060 Mobile] vendor: Micro-Star MSI
    driver: nvidia v: 535.129.03 bus-ID: 01:00.0

  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: modesetting,nvidia
    unloaded: fbdev,nouveau,vesa gpu: i915 resolution: 1920x1080~120Hz

  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes

Network:
  Device-1: Intel Cannon Lake PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlo1 state: up mac: <filter>
  Device-2: Qualcomm Atheros Killer E2500 Gigabit Ethernet
    vendor: Micro-Star MSI driver: alx v: kernel port: 3000 bus-ID: 3b:00.0
  IF: enp59s0 state: down mac: <filter>

Bluetooth:
  Device-1: Intel Bluetooth 9460/9560 Jefferson Peak (JfP) type: USB
    driver: btusb v: 0.8 bus-ID: 1-14:4
  Report: hciconfig ID: hci0 rfk-id: 4 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.1

Drives:
  Local Storage: total: 1.14 TiB used: 15.97 GiB (1.4%)
  ID-1: /dev/sda vendor: Western Digital model: WD10SPZX-17Z10T1
    size: 931.51 GiB
  ID-2: /dev/sdb vendor: Samsung model: MZNLN256HAJQ-00000 size: 238.47 GiB

Partition:
  ID-1: / size: 39.47 GiB used: 15.94 GiB (40.4%) fs: ext4 dev: /dev/sdb6
  ID-2: /boot/efi size: 96 MiB used: 32.3 MiB (33.6%) fs: vfat
    dev: /dev/sdb2

Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile

Info:
  Processes: 314 Uptime: 2h 42m Memory: 15.45 GiB used: 2.82 GiB (18.3%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 1868 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

---

