---
title: "differences between different types."
date: 2008-12-03
forum: General Help
---

### Post by Grolsche on 2008-12-03
Hi,

Being new to linux / Ubuntu etc etc.

I was curious as I see others on about kubuntu, hardy and iteprid etc.

What is the difference between them if any?

I have installed ubuntu but don't really know what these others are.

---

### Post by IHATEDLINK on 2008-12-03
> **Grolsche said:**
> Hi,

Being new to linux / Ubuntu etc etc.

I was curious as I see others on about kubuntu, hardy and iteprid etc.

What is the difference between them if any?

I have installed ubuntu but don't really know what these others are.

I'm not an expert, but here's the basics:
Ubuntu is an operating system built around GNU/Linux. It's based on another popular *distro* (distribution) named Debian.
Cannonical releases a new version of Ubnuntu every 6 months and, instead of naming them "Leopard", "Vista" or "XP, they name the releases using the year and the month in which it has been released. Per example: Ubuntu 8.4 was released on April 2008 (4/8). These releases have also "codenames" (Intrepid Ibex is 8.10, Hardy Heron is 8.4, Gusty....)

Now, Ubuntu has different "flavors" available. These are basically desktop environments. Ubuntu comes with the GNOME desktop environment by default, Kubuntu with KDE and Xubuntu with XFCE. It's up to you what you choose. It's a mater of taste actually.

---

### Post by Titan8990 on 2008-12-03
Those three actually can not be compared. Intrepid and Hardy are version numbers and kubuntu is ubuntu with a different destkop.

Versions:

Hardy - Ubuntu 8.04

Intrepid - Ubuntu 8.10


Desktops:


Ubuntu - [Gnome](http://en.wikipedia.org/wiki/Gnome_desktop)

Kubuntu - [KDE](http://en.wikipedia.org/wiki/Kde)

Xubuntu - [XFCE](http://en.wikipedia.org/wiki/Xfce)

Fluxbuntu - [Fluxbox](http://en.wikipedia.org/wiki/Fluxbox)



You can install multiple desktops on the same system and you get to choose which one you would like to log in to. No need to actually install a separate distro. 

I find it odd that they make entire different distros out of different desktops. Many other distros like Slackware just have you select a desktop during installation, but then again they installation DVDs instead of CDs.

---

### Post by Grolsche on 2008-12-03
ah thanks guys.

ok I now understand the intrepid and hardy bit, strnage its like that but hey.

Now just to clarify, what is the difference between Ubuntu, Kubuntu, Xubuntu, Fluxbuntu???

Is it just purely GUI looks or is there certian  features in each that make each one slightly different?

---

### Post by Titan8990 on 2008-12-03
Just the GUIs. If you see all my links are clickable and have screenshots so you can see what each interface looks like.


Also, just because you are running Gnome doesn't mean you can't install a KDE or XFCE application.

---

### Post by Grolsche on 2008-12-03
So can i install them all and try them out and then uninstall the ones i dont want?

Or is that a bad idea?

And how do i install them?

---

### Post by Titan8990 on 2008-12-03
Installing them is easy. Unfortunately, I have to found an easy way to uninstall them because they come with so many dependencies.

To install different desktops:


Applications -> Accessories -> Terminal:


For KDE:


sudo apt-get install kubuntu-desktop


For XFCE:

sudo apt-get install xubuntu-desktop 


And looking there isn't a metapackage for Fluxbox desktop. Flux is typically only used in machines that can't handle the others anyways.


After installing, in order to switch to a different desktop you hit the "sessions" button on the login screen. Also, your log in screen will match the last desktop that you installed but will not effect what your "default" desktop is.

---

### Post by Grolsche on 2008-12-03
Thanks for that.

At least I can now understand a little bit more and know what others are tlaking about :)

Dont suppose you can help to answer a question for me?

I have an ati driver, but when i follows ati instructions to install it, the terminal pops up a message about not being able to identify the X server?

What is X Server and what do i do   so I can get the driver to install?

---

### Post by Titan8990 on 2008-12-03
What instructions are you following?


Xserver is the very base of a graphical environment in Linux. All the desktops versions run on xserver.


Here is the wiki article: [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by Grolsche on 2008-12-03
these ones

# Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver you have downloaded
# Enter the command sh ./ati-driver-installer-8.28.8.run to launch the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed

---

### Post by Titan8990 on 2008-12-03
That method is not needed in Ubuntu. Just go to System -> Administration -> Restricted Drivers Manager


Install your drivers from there.

---

### Post by Grolsche on 2008-12-03
I dont see anything that says restricted Drivers Manager

---

### Post by Titan8990 on 2008-12-03
If you are running 8.10 it might be in System -> Preferences -> Restricted Drivers Manager

---

### Post by Grolsche on 2008-12-03
I cant even  find it in preferences either.

---

### Post by Grolsche on 2008-12-03
if it helps i have somethign that says hardware drivers, but if i open that its completely blank

---

### Post by Titan8990 on 2008-12-03
Lets make sure you have it. Open up the terminal and type:


which restricted-manager

If the result is:

```
jordan@einstein:~$ which restricted-manager
/usr/bin/restricted-manager
```

Then do the following:


gksu restricted-manager


If your which command does not produce the same results that mine did, let me know and I will instruct you on how to install the restricted drivers manager (it should be installed by default).

---

### Post by Grolsche on 2008-12-03
it just returned me

alan@Main-Desktop:$

---

### Post by Titan8990 on 2008-12-03
Alright, you somehow don't have it....


copy and paste the following in to the terminal:



sudo apt-get install restricted-manager

---

### Post by Grolsche on 2008-12-03
and that returns this:

> alan@Main-Desktop:~$ sudo apt-get install restricted-manager
[sudo] password for alan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package restricted-manager is a virtual package provided by:
  jockey-gtk 0.5~beta3-0ubuntu6
You should explicitly select one to install.
E: Package restricted-manager has no installation candidate
alan@Main-Desktop:~$ 


---

### Post by Titan8990 on 2008-12-03
Sorry, I am working on the 7.10 version and the repositories are a bit different.

Try this:


sudo apt-get install jockey-gtk

---

### Post by Grolsche on 2008-12-03
and now it gives this:

> alan@Main-Desktop:~$ sudo apt-get install jockey-gtk
[sudo] password for alan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jockey-gtk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alan@Main-Desktop:~$ 


---

### Post by Titan8990 on 2008-12-03
Take a screen shot (PrtScrn) if your System -> Preferences and System -> Administration menus open. Post the screenshots here. I think they might have renamed the Restricted Drivers Manager on me...

---

### Post by Grolsche on 2008-12-03
how do i get it to prnt screen, it wont let me do it when i open up the system part.

---

### Post by Titan8990 on 2008-12-03
I just tested it and your right.... 


Alright, try this:


gksu jockey-gtk

---

### Post by Grolsche on 2008-12-03
Basically when i did that it asked me for a password and then opened up the one i said to you earlier called Hardware Drivers.

But when that opens there is nothing there.

---

### Post by Titan8990 on 2008-12-03
Well, atleast we are making progress. Post the results of the following command:


lspci -v

---

### Post by Grolsche on 2008-12-03
here it is:

> alan@Main-Desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Giga-byte Technology Device 2570
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: e8000000-f7ffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: c4000000-c40fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 24d1
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: medium devsel, IRQ 9
	I/O ports at 1400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=64]
	Memory at fc001000 (32-bit, non-prefetchable) [size=512]
	Memory at fc002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
	Subsystem: PC Partner Limited Device 0130
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at f9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f8000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
	Subsystem: PC Partner Limited Device 0131
	Flags: bus master, 66MHz, medium devsel, latency 32
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at f9010000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	[virtual] Expansion ROM at c4000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: skge
	Kernel modules: skge

alan@Main-Desktop:~$ 


Good luck :)

---

### Post by Grolsche on 2008-12-03
Have u come up with any suggestions yet?

---

### Post by Titan8990 on 2008-12-03
Sorry for the delay. At work atm and actually got something to do *gasp*.


I hate to be the one to tell you but ATI does not make Linux drivers for your card. What this means is no desktop cube and no 3D games. You were actually only one series behind....


Are you having any issues with screen resolution or just hoping to get Compiz working?

---

### Post by theozzlives on 2008-12-03
> **Grolsche said:**
> ah thanks guys.

ok I now understand the intrepid and hardy bit, strnage its like that but hey.

Now just to clarify, what is the difference between Ubuntu, Kubuntu, Xubuntu, Fluxbuntu???

Is it just purely GUI looks or is there certian  features in each that make each one slightly different?

I don't like how KDE handles my network

---

### Post by Titan8990 on 2008-12-03
You can remove the KDE network manager and install network-manager-gnome inside of KDE (but it will need to download some gnome libraries).

---

### Post by Grolsche on 2008-12-03
if ATI doesnt make linux driver whats this?

[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html")

That's the driver i was trying to ask you about earlier and i was reading  there installation instructions for it.

---

### Post by Grolsche on 2008-12-03
oh yeah i thought i better just clarify that my graphics card is an ATI Radeon 9250 and not the 9200 that's being displayed for the controllers.

---

### Post by Titan8990 on 2008-12-03
The following cards are supported by the ATI Linux drivers:

```
Description: Video driver for ATI graphics accelerators
 Video driver for the ATI Radeon and FireGL graphics accelerators. 
 
 This version of the ATI driver officially supports: 
 
 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400, 
          V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
          X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration) 
 * Mobility FireGL: V5000, T2 
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, 
                   9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series 
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550, 
          X300, 9800, 9700, 9600, 9550, 9500
   
 ATI All-in-Wonder variants of the above cards/chips are also supported, but
 video capture is not. 
 
 This package provides 2D display drivers and hardware accelerated OpenGL.

```

---

### Post by Grolsche on 2008-12-03
so, if ati is crap at providing support for graphic cards.

Do you recommend any graphic card for 3d support in linux?

---

