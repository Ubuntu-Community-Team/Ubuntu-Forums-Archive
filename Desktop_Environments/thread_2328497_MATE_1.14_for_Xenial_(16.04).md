---
title: "MATE 1.14 for Xenial (16.04)"
date: 2016-06-21
forum: Desktop Environments
---

### Post by QDR06VV9 on 2016-06-21
Just in case you want to play...if you are happy with Mate 1.12 then just disregard this and [U][B]This is for Xenial (16.04) only... or Yakkety (16.10) Development.
[/B][/U]What&#8217;s new in MATE 1.14
[http://mate-desktop.com/blog/2016-04-08-mate-1-14-released/](http://mate-desktop.com/blog/2016-04-08-mate-1-14-released/)
> The headline changes in MATE 1.14 are:

    Improved GTK+3 support across the entire MATE Desktop.
    Full GTK 3.20 support in all MATE themes.
    Client Side Decorated applications render correctly in all themes.
    Completely ported MATE System Monitor and Mozo to GTK+3 only.
    Touchpad configuration now supports edge and two-finger scrolling independently.
    Python extensions in Caja can now be managed separately.
    All three window focus modes are selectable.
    MATE Panel now has the ability to change icon sizes for menubar and menu items.
    MATE NetSpeed Applet has been merged into the MATE Applets package.
    MATE Terminal support VTE 2.91 API when built for GTK+3.
    Volume and Brightness OSD can now be enabled/disabled.
    Translations are updated. Thank you to our team of translators!

The various components of MATE 1.14 are available for download here:

    [http://pub.mate-desktop.org/releases/1.14/](http://pub.mate-desktop.org/releases/1.14/)



Upgrade to MATE Desktop 1.14.x in Ubuntu MATE 16.04


```
sudo apt-add-repository ppa:ubuntu-mate-dev/xenial-mate
sudo apt update
sudo apt dist-upgrade

```
Been using this for about a week now with no seen ill effects...your mileage may vary!
My Specs
```
$ inxi -Fxz
System:    Host: me-Aspire-M3300 Kernel: 4.4.0-24-generic x86_64 (64 bit gcc: 5.3.1)
          [COLOR=#ff0000]** Desktop: MATE 1.14.1 (Gtk 2.24.30) Distro: Ubuntu 16.04 xenial**[/COLOR]
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 20741
           clock speeds: max: 2600 MHz 1: 1400 MHz 2: 1900 MHz 3: 1400 MHz
           4: 1900 MHz
Graphics:  Card: NVIDIA GF106 [GeForce GTS 450] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTS 450/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 367.27 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF106 High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Creative Labs SB Audigy
           driver: snd_emu10k1 port: e400 bus-ID: 04:06.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-24-generic
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: c800 bus-ID: 02:00.0
           IF: eno1 state: down mac: <filter>
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too v: 0.9.28 port: e800 bus-ID: 04:05.0
           IF: enp4s5 state: unknown speed: 100 Mbps duplex: full
           mac: <filter>
Drives:    HDD Total Size: 2500.5GB (46.4% used)
           ID-1: /dev/sda model: WDC_WD5000AACS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
Partition: ID-1: / size: 452G used: 12G (3%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 7.51GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 211 Uptime: 3:55 Memory: 980.8/6974.8MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.35 

```
Have Fun and Enjoy!:D
Regards

---

### Post by kansasnoob on 2016-06-22
Thanks for posting this info. I'll give it a whirl soon.

---

### Post by Omar_Jair on 2016-06-24
I was also wondering when will they add the gestures to the touchpad, by the way, will this replace the desktop or will i have to deal with a dual desktop login?

---

### Post by RobGoss on 2016-06-25
Already upgraded to 1.04 on one of my machines I don't really see any difference as far a performances so I'll just wait on doing it on my other machines

---

### Post by oldrocker99 on 2016-06-27
Upgrading to 1.14 doesn't add another desktop, but does upgrade your current desktop.

---

### Post by QDR06VV9 on 2016-06-27
> **Omar_Jair said:**
> I was also wondering when will they add the gestures to the touchpad, by the way, will this replace the desktop or will i have to deal with a dual desktop login?
Whimpy (Developer for Mate) has hinted that things are going good...so we should see new things very soon.

> **oldrocker99 said:**
> Upgrading to 1.14 doesn't add another desktop, but does upgrade your current desktop.
+1:)
I myself have only seen a bug or two but no show stoppers..IE: I had to use Dconf editor to remove the bottom panel...and some themes have a different look to them.

---

### Post by dennylockhart on 2016-07-10
Just installed it on my Dell Chromebook 13 (i5/8GB/256GB) using 'crouton' - it's awesome! :P
One question though: How the heck do I remove the '$USER Home' launcher/icon from the desktop?

My System:
```

(xenial-mate)denny@localhost:~$ inxi -Fxz
System:    Host: localhost Kernel: 3.14.0 x86_64 (64 bit gcc: 4.9.x) 
           Desktop: MATE 1.14.1 (Gtk 3.18.9-1ubuntu3)           Distro: Ubuntu 16.04 xenial
Machine:   System: GOOGLE (portable) product: Lulu v: Pilot
           Mobo: N/A model: N/A Bios: coreboot v: Google_Lulu.6301.136.57 date: 03/28/2016
CPU:       Dual core Intel Core i5-5300U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9178
           clock speeds: max: 2900 MHz 1: 813 MHz 2: 813 MHz 3: 813 MHz 4: 813 MHz
Graphics:  Card: Intel Broadwell-U Integrated Graphics bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 driver: N/A Resolution: 1920x990
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Broadwell-U Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k3.14.0
Network:   Card: Intel Wireless 7260 driver: iwlwifi bus-ID: 01:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 256.1GB (11.4% used) ID-1: /dev/sda model: ZTC size: 256.1GB temp: 30C
Partition: ID-1: / size: 106G used: 17G (17%) fs: ext4 dev: /dev/sda13
           ID-2: swap-1 size: 12.15GB used: 0.00GB (0%) fs: swap dev: /dev/zram0
Sensors:   System Temperatures: cpu: 42.8C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 280 Uptime: 1:33 Memory: 3801.2/7910.8MB Init: N/A Gcc sys: 5.3.1
           Client: Shell (bash 4.3.461) inxi: 2.2.35 

```

Thanx for all the hard work,
Denny

---

### Post by dennylockhart on 2016-07-10
I found out how to remove the 'home-icon' by installing `dconf-editor` - no worries.

---

