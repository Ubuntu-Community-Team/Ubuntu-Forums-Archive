---
title: "Desktop Effects Could Not Be Enabled"
date: 2009-07-04
forum: Desktop Environments
---

### Post by scotty331 on 2009-07-04
Well, Im new to linux. And I Installed Jaunty on my computer. Then when I first ran it, I put the effects to extra. Then it started lagging, so i acidentally put them on None! And now when i try to put them on normal, I get an error saying > Desktop Effects Could Not Be Enabled! Please help me to get the desktop effects back!

---

### Post by Tamlynmac on 2009-07-04
It might help if you would post your system hardware and spces. I suspect someone is going to ask for them. Don't forget to include:
CPU %
Memory & Swap
These can be found on the resources tab of system/administration/system monitor
If your CPU % is high or your memory usage is large check the Processes tab and identify what apps are using the resources.

Sorry I can't be of more help, but I think if you identify your system information, it might help identify the problem.

Good Luck

---

### Post by Ra-Hoor-Khuit on 2009-07-04
Go to System/Administration/Hardware Drivers and make sure the restricted-driver for you video card is enabled; the "advanced desktop effects" require it.

---

### Post by AoSteve on 2009-07-04
Sounds like a driver issue there.   Do you happen to know what video card the system has?  Also, if you don't know you have a very effective way to find out.

Click the "Applications" menu and head to accessories.  Then select terminal.  You will start and see something similar to this : 

gnome@E8400:~$ 


From here simply type this command...   lspci -v

When you post back simply enclose those in the post and we'll be able to determine what video card you have and what the proper drivers are.  :)   You can simply select the information with the mouse and right click and pick copy and then past it into your reply.  :)
[FONT=arial, helvetica,sans-serif][SIZE=1]


[/SIZE][/FONT]

---

### Post by scotty331 on 2009-07-04
> **Tamlynmac said:**
> It might help if you would post your system hardware and spces. I suspect someone is going to ask for them. Don't forget to include:
CPU %
Memory & Swap
These can be found on the resources tab of system/administration/system monitor
If your CPU % is high or your memory usage is large check the Processes tab and identify what apps are using the resources.

Sorry I can't be of more help, but I think if you identify your system information, it might help identify the problem.

Good Luck

Okay. The %'s are

CPU = 22%
Memory =31%
Swap =47%

---

### Post by scotty331 on 2009-07-04
> **AoSteve said:**
> Sounds like a driver issue there.   Do you happen to know what video card the system has?  Also, if you don't know you have a very effective way to find out.

Click the "Applications" menu and head to accessories.  Then select terminal.  You will start and see something similar to this : 

gnome@E8400:~$ 


From here simply type this command...   lspci -v

When you post back simply enclose those in the post and we'll be able to determine what video card you have and what the proper drivers are.  :)   You can simply select the information with the mouse and right click and pick copy and then past it into your reply.  :)
[FONT=arial, helvetica,sans-serif][SIZE=1]


[/SIZE][/FONT]


Okay, Well Its long but 
> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
    Subsystem: Dell Device 0181
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: dfd00000-dfdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
    Subsystem: Dell Device 0181
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at e898 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
    Subsystem: Dell Device 0181
    Flags: bus master, fast devsel, latency 0
    Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: dfc00000-dfcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfb00000-dfbfffff
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ec00 [size=256]
    I/O ports at e8c0 [size=64]
    Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
    Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 0181
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fea0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 0181
    Flags: medium devsel, IRQ 5
    I/O ports at e8a0 [size=32]
    Kernel modules: i2c-i801

03:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
    Subsystem: Dell Device 1000
    Flags: bus master, stepping, medium devsel, latency 64, IRQ 17
    Memory at dfbfe000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at dc00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: serial

03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at dfbff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d8c0 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100



---

### Post by AoSteve on 2009-07-04
> 
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
    Subsystem: Dell Device 0181
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at e898 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
    Subsystem: Dell Device 0181
    Flags: bus master, fast devsel, latency 0
    Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>



Using [this](http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+video) guide I installed the intel video drivers.  I only did part A and tested it and made absolute sure it was identical as it says in the post.   I'm nowhere near advanced enough in linux to start messing with kernels so I stayed with the "safe" option and it worked!   Basically, I enabled "uxa" under the acceleration option and that was about the only change I had to make.   :)

A couple things to remember.   Backup your original xorg.conf file with this command in a terminal.

```

sudo cp /etc/X11/xorg.conf /etc/xorg.BACKUP

```

To easily edit the file like it shows in the "howto"..

```

sudo gedit /etc/X11/xorg.conf

```

Also, another good idea that helped me through it, as I was basically in the SAME situation...   When you get to the login screen you can choose "safe graphics mode" from the options.   If you mess up, and I did a couple times lol, you will have to option for it to automatically reset itself.  :)

If there's anything else I can tell you or explain, please let me know.   Personally, I wouldn't go past step A on that howto as I honestly don't think I'm ready to go that far just yet! :)

---

### Post by roccity1 on 2009-07-05
I have a Inthing.
el video chip as well. I found that by going commenting out the blacklisted intel driver in /usr/bin/compiz helped fix everything.

Open /usr/bin/compiz with gedit and add a # in front of the section dealing with Intel cards. That should hellp you you might have to log out and then back in.

---

