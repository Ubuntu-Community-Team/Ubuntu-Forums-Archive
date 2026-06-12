---
title: "Bluetooth is disabled"
date: 2009-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by groovomata on 2009-11-11
Hello All, 
My Bluetooth isn't working. The Gnome Bluetooth app says that Bluetooth is disabled, and will not (or can not) turn it on. I checked the bios for my Dell Inspiron 6400 laptop and have it set that bluetooth is enabled. I also have it set so that the function-key+F2 toggles it on and off along with my wireless card, however the wireless icon is on (and works fine), but the Bluetooth one is not (and does not work). 
My question is, how do I turn it on?
Thanks,
Erik.

---

### Post by coffeeaddict22 on 2009-11-12
Hi,
First of all, you have had working Bluetooth in the past?  If so, what broke it?  If not, are you sure the hardware is present?
Open a terminal (Start/Accessories/Terminal), and type in the following command.  Post back the output; it may help.
```
hciconfig -a
```

---

### Post by groovomata on 2009-11-12
> **coffeeaddict22 said:**
> Hi,
First of all, you have had working Bluetooth in the past?  If so, what broke it?  If not, are you sure the hardware is present?
Open a terminal (Start/Accessories/Terminal), and type in the following command.  Post back the output; it may help.
```
hciconfig -a
```
Thanks for your reply coffeeaddict22!
I don't know if Bluetooth has worked in the past or not with this laptop as I have never tried it. I can say though, that there is a Bluetooth symbol on the laptop, beside the wireless symbol, but it is not lit. 
I entered > hciconfig -a in a terminal, and got no response, meaning that I got no error messages.
Thanks,
Erik.

---

### Post by coffeeaddict22 on 2009-11-12
Hmmm.  There's a particularly unpleasant Windows stunt you may be dealing with.  If the Bluetooth has been turned off in Windows, you may need to boot into windows to turn it on.  Have a look [here, ]("https://help.ubuntu.com/community/BluetoothSetup") and (more specifically ) [here.]("http://ubuntuforums.org/showthread.php?t=1101204")

---

### Post by groovomata on 2009-11-12
> **coffeeaddict22 said:**
> Hmmm.  There's a particularly unpleasant Windows stunt you may be dealing with.  If the Bluetooth has been turned off in Windows, you may need to boot into windows to turn it on.  Have a look [here, ]("https://help.ubuntu.com/community/BluetoothSetup") and (more specifically ) [here.]("http://ubuntuforums.org/showthread.php?t=1101204")
Uh oh. That would be a huge bummer. I haven't had Windows on this computer for a long time. Crazy to think that a hardware setting from within Windows long since removed can't be changed by Linux. I haven't had a chance yet to go through it all, as it is late here. However I will have some time this weekend. I'll post back my results.
Thanks for the info coffeeaddict22!
Best,
Erik.

---

### Post by coffeeaddict22 on 2009-11-13
Have to agree it's not particularly nice.  The HP laptop that had the problem (I think I gave you the link) did get out of it by selecting Reset to Defaults in BIOS settings, so you might get lucky (and if you're not a hardware hacker you won't lose any important settings).

---

### Post by groovomata on 2009-11-15
I wonder if it is possible to shrink my linux partition and install Vista (I think I have my old install disk somewhere) without gimbling my linux boot partition. Make the necessary change and then remove Vista and restore my linux partition?
This I will try to research.

---

### Post by groovomata on 2009-11-15
This thread has some links to really good explanations on how to make space for a Vista installation, then how to repair the master boot record afterwards:
> [http://ubuntuforums.org/showthread.php?t=1241200&highlight=dualboot+vista](http://ubuntuforums.org/showthread.php?t=1241200&highlight=dualboot+vista)
All I need to do now is find my old Vista install CD (where ever that is). I haven't used it in a while.

---

### Post by efflandt on 2009-11-16
I have a company Dell Inspiron 6400 with its original WinXP Pro and it has the Bluetooth LED on it.  But that is an option that has never shown up in WinXP, so not on that laptop and probably not on your laptop.  Does **sudo lspci -v** show any Bluetooth device?

So I am not sure how you would tell "if" you have Bluetooth option.  If you have it, maybe it requires a proprietary driver like wireless does.  See if System, Administration, Hardware Drivers shows anything related to Bluetooth.

I did get Broadcom wireless working from a 9.10 live/install iso on bootable USB.  Not sure how that works on a regular install, but even after I activated the Broadcom STA driver, it did not load automatically from live/install version.  I had to **sudo modprobe wl** for it to work (although, that did not light wireless LED).  Rather than tampering with init scripts, I just added this to ubuntu user's ~/.profile to automate that if the live USB was running on the Dell:

```
# load Broadcom wireless module if Dell laptop
if lspci | grep -q BCM4311; then
        lsmod | grep -qw wl || sudo modprobe wl
fi
```

---

### Post by groovomata on 2009-11-18
Efflandt, thanks for your response. I entered **sudo lspci -v** into a terminal and this is what I got: > 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Device 01bd
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: ed000000-efefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Dell Device 01bd
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: ecf00000-ecffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Device 01bd
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ecc00000-ecefffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Device 01bd
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: ecb00000-ecbfffff
	Capabilities: [50] Subsystem: Dell Device 01bd

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Device 01bd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Device 01bd
	Flags: medium devsel, IRQ 5
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
	Subsystem: Dell Device 2003
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at ef000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01af
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at ecbfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at ecbfd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at ecbfd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 01)
	Subsystem: Dell Device 01bd
	Flags: medium devsel, IRQ 9
	Memory at ecbfd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 0a)
	Subsystem: Dell Device 01bd
	Flags: medium devsel, IRQ 9
	Memory at ecbfd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Device 0007
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ecffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 2
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
As far as I can see, there is no specific reference to any type of Bluetooth service other than what is contained in the Network Controller: Broadcom Corporation BCM4311 802.11b/g WLAN. Additionally, there is no other driver for Bluetooth outside of the Broadcom B43 wireless driver. 

As well I found this thread: [http://ubuntuforums.org/showthread.php?t=1071298&highlight=Bluetooth](http://ubuntuforums.org/showthread.php?t=1071298&highlight=Bluetooth), and entered **lsmod** which didn't bring up any references to Bluetooth. So I'm not really sure right now whether Bluetooth can work or not with my computer.

Thank you,
Erik.

---

### Post by teward on 2009-11-18
Oh, let me tell you this:  Even if there's a bluetooth icon on the computer (the hardware), it doesn't mean you have Bluetooth.  I should know: I have a Latitude E6500, and it has a bluetooth icon, but no bluetooth hardware.  So you don't actually have a bluetooth internal card unless its listed under your devices.  Since it isn't listed, you don't have Bluetooth capabilities.

---

### Post by InaBanina on 2009-11-19
I have this problem too. I'm using a bluetooth dongle that used to work with Windows XP. Upon inserting the dongle, I get a bluetooth icon with a red "x" in the desktop. I try to enable it but it won't work. Right-clicking on the icon gives me the option to "turn off bluetooth" (thus making me think that it's actually enabled) but the red "x" remains. Has anyone had problems with this too?

I'm new to Ubuntu so I apologize in advance for "noobing." :-)

---

### Post by groovomata on 2009-11-19
Ah, thanks for that. I think I'm starting to agree with you. 
Regards,
Erik.

---

### Post by coffeeaddict22 on 2009-11-22
Hi Groov,
Sorry, got busy.
Can you try typing in the following (separate) three commands```
cat /var/log/dmesg | grep Blue*
hcitool dev
hciconfig
``` in a terminal(Applications/Accessories/Terminal)?  That should tell us if you've got Bluetooth, and if so where the problem lies.

Just as an aside, if you're not sure what to look for, in a terminal type apropos xxxx, and it'll come up with some relevant commands.  You can then type in man yyyy where yyyy is the commands it came back with, and you get more info than you really wanted.  There are always a few idiots out there, so if you see a command you're not sure about, ASK.

---

### Post by groovomata on 2009-11-24
Hi coffeeaddict22, thanks for your response. Here is what I got:
> cat /var/log/dmesg | grep Blue*
[    0.236008] Bluetooth: Core ver 2.15
[    0.236023] Bluetooth: HCI device and connection manager initialized
[    0.236023] Bluetooth: HCI socket layer initialized
[    0.922745] Bluetooth: L2CAP ver 2.13
[    0.922746] Bluetooth: L2CAP socket layer initialized
[    0.922749] Bluetooth: SCO (Voice Link) ver 0.6
[    0.922751] Bluetooth: SCO socket layer initialized
[    0.922792] Bluetooth: RFCOMM TTY layer initialized
[    0.922795] Bluetooth: RFCOMM socket layer initialized
[    0.922797] Bluetooth: RFCOMM ver 1.11

> hcitool dev
Devices:


hciconfig didn't give any error messages. I didn't run them as sudo though. 
Any thoughts?
Thank you,
Erik.

---

### Post by coffeeaddict22 on 2009-11-25
Still not sure if you've got a running card.  They don't show up sometimes.  Can you try ```
sudo lsusb -v | grep Blue

``` and post back the output?

---

### Post by groovomata on 2009-11-26
Coffeeaddict22, I did > sudo lsusb -v | grep Blueand got no output. On the plus side, I got no error messages either.
Thank you for your time,
Erik.

---

### Post by HotShotDJ on 2009-11-26
> **groovomata said:**
> I did and got no output. On the plus side, I got no error messages either.Erik... I read through this thread.  I am confident that you have no Bluetooth hardware on your computer.  My System76 laptop has built-in Bluetooth. Here is the output of lsusb -v | grep Blue```
$ lsusb -v | grep Blue
Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
  bDeviceProtocol         1 Bluetooth
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth

```Just like you, I also have a Dell laptop (E1505) which has a Bluetooth indicator, even though it has no built-in Bluetooth device.

---

### Post by coffeeaddict22 on 2009-11-27
I'm strongly suspicious the card is turned off.  Have you tried the commands - especially lsusb -v | grep Blue  - before and after hitting the on/off key combo?  And there may be two switches- one a key combo, and another a separate key on the side or front of the machine.

---

### Post by teward on 2009-11-27
I'm 100% certain the poster of this thread HAS no bluetooth hardware in his/her/its computer.  Even if its disabled, it would have shown up.

---

### Post by groovomata on 2009-11-28
Thanks, everyone, for your posts. I'm pretty certain that I don't have Bluetooth on this laptop. It's still a good laptop, but I think that the next laptop I buy will have Bluetooth and built in web cam which this one doesn't have. 
Thanks again for all your help.
Erik.

---

### Post by gdesilva on 2009-11-29
Hi everyone I hope one of you can point me in the right direction to solve this issue.

I have a Dell Dimension 9150 with a Dell bluetooth dongle and bluetooth mouse and a keyboard. 

Had everything working fine on Win XP. Then I loaded Ubuntu 9.04 (dual boot) and had no issue with bluetooth.

Upgraded to 9.10 and all of a sudden bluetooth app claims that there are no bluetooth devices. However, I am still able to use my bluetooth keyboard and the mouse without any problem. Of course, I cannot connect to any other bluetooth device.

I did a clean 9.10 install and the problem is the same. Device manager claims that the USB bluetooth dongle is in HID Proxy mode. hciconfig claims there are no devices.

Any ideas on how to resolve this issue?

Many thanks

---

### Post by teward on 2009-11-29
> **gdesilva said:**
> Hi everyone I hope one of you can point me in the right direction to solve this issue.

I have a Dell Dimension 9150 with a Dell bluetooth dongle and bluetooth mouse and a keyboard. 

Had everything working fine on Win XP. Then I loaded Ubuntu 9.04 (dual boot) and had no issue with bluetooth.

Upgraded to 9.10 and all of a sudden bluetooth app claims that there are no bluetooth devices. However, I am still able to use my bluetooth keyboard and the mouse without any problem. Of course, I cannot connect to any other bluetooth device.

I did a clean 9.10 install and the problem is the same. Device manager claims that the USB bluetooth dongle is in HID Proxy mode. hciconfig claims there are no devices.

Any ideas on how to resolve this issue?

Many thanks

post this in a new thread of your own.  First thought is that 9.10 is being evil.

---

### Post by gdesilva on 2009-11-30
The following post from niteshifter worked for me - thanks niteshifter!

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8298037)

In my case the bluetooth was stuck in HID Proxy mode and the procedure outlined in the above post fixed it.

---

