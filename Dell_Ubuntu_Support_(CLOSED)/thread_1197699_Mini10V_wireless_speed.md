---
title: "Mini10V wireless speed"
date: 2009-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by andy_T_UK on 2009-06-26
I have a Mini10v with a BCM4322 wireless card, the dell 1510. I have tried to follow the instructions on help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy. I got as far as downloading and installing the B43 package [b43-firmware_1.0-0cafuego0_all.deb]("http://ubuntu.cafuego.net/pool/hardy-cafuego/broadcom/b43-firmware_1.0-0cafuego0_all.deb") but I dont see how to use it instead of wl. I want to change as the Dell wl driver does not take advantage of draft n and sometimes only connects at 11Mb.

Andy :confused:

---

### Post by coffeeaddict22 on 2009-06-27
Hi Andy,
You've got 2 problems.  Firstly, if you've already got wireless, I think you can take it for granted the mini's weren't meant to work at 1/4 the wireless speed of normal machines.  It's not the wl driver.  If you want to troubleshoot that, it's probably your best option.

If you don't, then ndiswrapper is an option.  It's a messy option, and was essentially a stopgap until the Linux drivers were working, but it's probably possible to get them working in Jaunty.

What version of Linux are you running?  Open a terminal, type in ```
uname -a
``` and that'll tell you enough.  Also, what's your current network setup?  in the terminal, type the following two commands ```
lspci -v
nm-tool
```Then decide if you want to fix your current connection or try the wrapper.  If you want more help, post the output from those commands back.

---

### Post by andy_T_UK on 2009-06-28
Here is the output of uname -a:

Linux andy 2.6.24-24-lpia #1 SMP Wed May 6 17:43:36 UTC 2009 i686 GNU/Linux

And the output of[FONT=monospace] [/FONT]lspci -v and nm-tool:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, fast devsel, latency 0
    Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 50000000-500fffff
    Prefetchable memory behind bridge: 00000000f0500000-00000000f05fffff
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at f0444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Memory at 50100000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Dell Unknown device 02f4
    Flags: medium devsel, IRQ 10
    I/O ports at 18c0 [size=32]

03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Dell Unknown device 02f4
    Flags: bus master, fast devsel, latency 0, IRQ 220
    I/O ports at 2000 [size=256]
    Memory at f0510000 (64-bit, prefetchable) [size=4K]
    Memory at f0500000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f0520000 [disabled] [size=128K]
    Capabilities: <access denied>

and

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:AF:69:1D

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes

  Wired Settings


- Device: eth1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:24:2C:20:7A:DD

  Capabilities:
    Supported:       yes
    Speed:           24 Mb/s

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points(* = Current AP)
    *Belkin_N1_A1D496: Infra, 00:1C:DF:A1:D4:96, Freq 2427 MHz, Rate 54 Mb/s, Strength 100 WPA2
    SKY09072:        Infra, 00:18:4D:0C:0C:76, Freq 2412 MHz, Rate 0 Mb/s, Strength 40 WPA
    rollup:          Infra, 00:0F:B5:1A:25:A6, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA
    Belkin54g:       Infra, 00:1C:DF:85:D6:CF, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WEP
    O2wirelessA5307D:Infra, 00:18:F6:6F:9F:8F, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP

  IPv4 Settings:
    Address:         192.168.2.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             62.24.139.140

What is the best way for me to procede?

Andy :)

---

### Post by snowpine on 2009-06-28
I strongly recommend sticking with the wl driver. It is developed by Broadcom themselves specifically for your wireless card, and the Dell Ubuntu "remix" you have installed is designed specifically for your computer. To my knowledge, b43 does NOT support your card. Your best bet is to troubleshoot the problem with wl. One option is to compile the latest version straight from Broadcom: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

You currently have working wireless; as a Dell mini owner myself, I can tell you that is something!

---

### Post by andy_T_UK on 2009-06-28
I have got the file and extracted it to its own dir. Now I have just printed the readme in order to `make` the driver.


Edit: I have tried the make command with various perameters but each time it gives me an error. So as I dont really know what I am doing I am stuck.

Andy

---

### Post by coffeeaddict22 on 2009-06-28
Hi,
You've got, as the man said, a working wireless.  Upgrading the driver may work; it's possible it's the wireless strength,  There have been fairly frequent cases of Linux and other OS getting different signal strengths for the same hardware; dunno why.  So be warned, updating your firmware may not help.  Usually the simplest solution for that is to change the channel on the router.

To install from source, the 3 commands in order are
```
./configure
make
make install
```
 with the proviso that you must do these from within the directory the files have been unpacked to.  You may also need to do them as superuser; if the problem is you get a message along the lines of "insufficient permission" or "you must be root/superuser" then precede the command with "sudo".  The lazy way to do it if you've just typed a command which has failed is to type ```
sudo !!
```
If that doesn't work, post back what the error message is and we'll go from there.

---

### Post by andy_T_UK on 2009-06-29
I will try adjusting the WiFi Chanel when I finish work. I was hoping to make use of draft n and not just g speeds. Though if the Netbook connects at 54 almost constantly that will be a great improvement.

Sorry to sound dumb but ./configure says no file or directory, will try the download and unpack again. I did try the other channels I was on 6 but I tried 11 and failed to connect. Then I tried 8 but failed to connect. So I changed back to 6 to get a connection up.

Edit: I did not try the low numbers as there are a few wifi networks near me that use channel 1. If I remember correctly only channels 1, 6 and 11 don`t overlap.

Andy

---

### Post by andy_T_UK on 2009-07-08
I did try protected mode on the WiFi hub as the help said this may help in areas of a lot of 11g traffic, it made no noticable difference.

I then made myself an image of the 9.04 netbook remix and installed that. After setting up the SSID and the WPA2 security for WiFi I got a connection at 51M/s so I tried system/Upgrade and got through about half the downloading before I lost connection. I rebooted and then upgraded again with a wired connection, hoping for a a WiFi driver upgrade. I never got a WiFi connection again no matter where I tried, next to the AP or not. I restored 8.04 from the Dell DVD and performed system/upgrade over the WiFi link.

I notice I now get 24M - 51M speeds, still no where near the 11n draft speeds but it with upgrades it may get better.

Andy :confused:

Edit: The strange thing is standing next to the AP gave me 24M but the other side of a stud wall I was getting 51M, just thought this may help diagnose the issue.

---

