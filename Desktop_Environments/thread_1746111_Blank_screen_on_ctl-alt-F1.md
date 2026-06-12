---
title: "Blank screen on ctl-alt-F1"
date: 2011-05-01
forum: Desktop Environments
---

### Post by aphatak on 2011-05-01
OS: Ubuntu 10.04 LTS, kernel 2.6.32-31-generic.  All updates are current.
Configuration -
[INDENT]CPU: Intel Core i5-2500K, quad core 3.30GHz
Memory:  16GB RAM (10% used), 20GB swap-space (0% used)
Video:  Two ASUS EAH5450 Silent cards, each with ATI Radeon HD-5450 GPU and 512 MB
Monitors:  Sceptre 22", 1680x1050; both connected to one video card.  The second video card has no monitors connected at this time.
ATI/AMD proprietary FGLRX driver[/INDENT]
LSPCI output -
```
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation Device 0112 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4a (rev 05)
00:1f.2 IDE interface: Intel Corporation Cougar Point 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation Cougar Point 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8893 (rev 10)
05:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
05:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```
The PC boots up normally into Gnome desktop environment.  When I hit ctl-alt-[F1-F6], -
[LIST=1]
[*]The screens blank out.
[*]One screen gets no video signal, as evidenced by a blinking power light
[*]The other screen is completely blank (not even a blinking cursor)
[*]If I hit ctl-alt-F7, I get the Gnome desktop back.
[/LIST]
I have been able to determine that even if the screen is blank, and appears completely dead, the system processes my keystrokes.  For example, if I pretend that I am at the log-in screen and type <username> <enter>, then <password><enter>, then 'xinit -fg white -bg blue -- :1 vt8'<enter>, the PC switches to virtual terminal 8, and shows a shell window.  From that point onwards, my keyboard entries show up in white-on-blue characters, and the behavior of this shell window is perfectly normal.  I can log into another Linux box using ssh, start a Gnome / KDE / XFCE4 / LXDE session and work on the machine normally; or start another X-session and a desktop environment of my choice.
My guess is, the console is invoked perfectly well; it is set to display black-on-black characters.

**_What I Am Looking For_**:
[LIST=1]
[*]Confirm if my guess about black-on-black console is valid.
[*]Suggest how I could get a screen showing white characters on black (or indeed, any combination I could read)
[/LIST]
Any ideas, anyone?

---

### Post by aphatak on 2011-05-01
I installed proprietary ATI drivers, and now the blank screens have gone.  I see the regular black-on-white screens in their place.  And no, I cannot reproduce the problem, so I guess I will mark this thread as closed and let it go at that!

---

