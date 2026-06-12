---
title: "[SOLVED] No touchpad and crazy keyboard"
date: 2008-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LK_gandalf_ on 2008-05-01
Hi, I have a DELL Xps M1530, and kubuntu 8.04 64bit. Everything works out of the box, it's perfect, except the two easier things....keyboard and touchpad!!!

Touchpad doesn't respond, and sometimes the cursor goes everywhere cliccking like a mad.
keyboard works well,m but sometimes it "freeze" for some second....it freeeeeeeeeeeeeeeeeeeeeeeeeeeeee (example)

Can you help me?

here some infos, maybe useful:
```

cat /proc/bus/input/devices

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=100f02002000 380307af800d001 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2
B: EV=20017
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10
B: LED=ff00

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=event3
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=3
B: KEY=3f000b00000000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input7
U: Uniq=
H: Handlers=kbd event7
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input23
U: Uniq=
H: Handlers=mouse2 event8
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3


``` 

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc102"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"NoLogo"	"True"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by LK_gandalf_ on 2008-05-03
please up, i have this problems since 2 weeks and nobody helps me. I dont' want to come back to windows for these two stupids problems, everything else works perfectly.

Now, an update: new kernel today (2.6.24-17), touchpad still doesn't works, and I have a new problem: while using normally the mouse, the cursor sometimes goes in the left-corner of the screen and opens the start menu.
-.-

---

### Post by trwww on 2008-05-05
> **LK_gandalf_ said:**
> Hi, I have a DELL Xps M1530, and kubuntu 8.04 64bit. Everything works out of the box, it's perfect, except the two easier things....keyboard and touchpad!!!

Touchpad doesn't respond, and sometimes the cursor goes everywhere cliccking like a mad.
keyboard works well,m but sometimes it "freeze" for some second....it freeeeeeeeeeeeeeeeeeeeeeeeeeeeee (example)

Can you help me?


Hello,

Is this a new machine? This might sound crazy but power supply may be the cause of the trouble:

[Inspiron 1520 TouchPad Troubles :\ Please Help!]("http://www.dellcommunity.com/supportforums/board/message?board.id=insp_general&thread.id=267750")

I haven't saw anyone on linux with this problem, but it personally happened to me on my new inspiron 1520 running xp.

Your touchpad problem description is the same as mine was, and a new power supply fixed it.

I didnt have the same keyboard issues though.

Good Luck,

trwww

---

### Post by OffHand on 2008-05-05
I had the crazy touchpad issue with my M1530. I have added i8042.nomux=1 to the kernel options in /boot/grub/menu.lst

Do not copy below. This is an example so you know where to add it.

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1c8edafe-1b83-4e4a-acea-e6e2453490b1 ro quiet splash i8042.nomux=1

---

### Post by irish8890 on 2008-05-06
Fix your /etc/X11/xorg.conf file to add the 3 OPTION lines in the bottom as shown below (they are SHMConfig, MaxSpeed & AccelFactor).  These worked just fine with 7.10, however, with 8.04 I have had lost & hung-up keypad and occasional system lock-ups over the last few days after upgrading to 8.04.

John

> Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "true"
    Option         "MaxSpeed" "0.99"
    Option         "AccelFactor" "0.08"
EndSection

---

### Post by LK_gandalf_ on 2008-05-08
ehi, it works :) I only have to set the right number, because with this numbers the cursor is too slowly.
Thank you :) So, the problem maybe was not in the drivers, just the settings.
is there any graphical tool to set the touchpad?

---

### Post by limesmoothie on 2008-05-08
Did this machine come with Linux as a pre-instal from Dell i.e. is it brand new? Just as my 1330 developed a similar keyboard/touchpad fault after only a couple of months usage. The tech that came out to fix it said he'd seen a lot of 1330/1530 machines with that problem. He ended up replacing the keyboard and touchpad.

---

### Post by LK_gandalf_ on 2008-05-11
No, I have installed Kubuntu. the laptop here in Italy cames out only with Vista :(

however, the touchpad doesn't work again. -.- I't s incredible. 
And keyboard goes on freezing sometimes.

Any solutions? :(

---

### Post by omarino on 2008-05-23
Can confirm on Ubuntu 8.04 on HPnx7400 notebook. Strange thing though - it started only yesterday after some upgrades and wi-fi driver patch. Cant't point a finger at a culp though.
O.

---

### Post by LK_gandalf_ on 2008-05-26
Ok, I have the solution, thanks to an italian users on the ubuntu forum.

Digit, using your favourite text editor:

sudo kate /boot/grub/menu.lst

find the line about your system, and add at the end the word "i8042.nomux=1"

Like this:

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=30a62181-05a6-4969-ba6e-2e764bf495f6 ro quiet splash i8042.nomux=1


Reboot and enjoy your touchpad ;)

The problem is related only to the Dell A08 Bios. So, if this doesn't work, you have to downgrade your DELL bios and try it.

---

### Post by OffHand on 2008-05-26
That's what I said 2 weeks ago

---

### Post by mrojas73 on 2008-05-27
Update your to 2.4.24.17 and this won't work anymore.

---

### Post by OffHand on 2008-05-28
> **mrojas73 said:**
> Update your to 2.4.24.17 and this won't work anymore.

It does. You just have to re-add it again.

---

