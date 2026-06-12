---
title: "trashed my gnome gui"
date: 2009-02-07
forum: General Help
---

### Post by jocatoth on 2009-02-07
help

i have been trying to fix small fonts in login and password boxes. i tried several things to change it. the list thing i did was

 Re: very small font
I got the same problem. Solved changing the xorg initialization (sorry if the translation is incorrect:

- Gnome menu System/Administration/Login Window (gdmsetup, the last one option).

- Tab "Security", button "Configure X Server"

- On "Command" field, add " -dpi 96" (no quotes) at the end of the command.

In my case, it solved the problem. Try it.


this was from [http://ubuntuforums.org/showthread.php?t=312359](http://ubuntuforums.org/showthread.php?t=312359)

now my gui wont start. i have tried several things to repair this in xfix, tried several drivers for my ati.

i am trying to learn and not just reinstall but i guess i do not know what i am doing.

here is lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
Subsystem: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
Flags: bus master, 66MHz, medium devsel, latency 8
Memory at d0000000 (32-bit, prefetchable) [size=128M]
Capabilities: [a0] AGP version 2.0
Capabilities: [c0] Power Management version 2

00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge (prog-if 00 [Normal decode])
Flags: bus master, 66MHz, medium devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000c000-0000cfff
Memory behind bridge: e0000000-e00fffff
Prefetchable memory behind bridge: d8000000-dfffffff
Capabilities: [80] Power Management version 2

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: Belkin F5D5000 PCI Card/Desktop Network PCI Card
Flags: bus master, medium devsel, latency 32, IRQ 16
I/O ports at d000 [size=256]
Memory at e0110000 (32-bit, non-prefetchable) [size=256]
[virtual] Expansion ROM at 50000000 [disabled] [size=64K]
Capabilities: [50] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Flags: bus master, medium devsel, latency 32, IRQ 17
I/O ports at d400 [size=32]
Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Flags: bus master, medium devsel, latency 32, IRQ 17
I/O ports at d800 [size=32]
Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Flags: bus master, medium devsel, latency 32, IRQ 17
I/O ports at dc00 [size=32]
Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-i,f 20 [EHCI])
Subsystem: VIA Technologies, Inc. USB 2.0
Flags: bus master, medium devsel, latency 32, IRQ 17
Memory at e0111000 (32-bit, non-prefetchable) [size=256]
Capabilities: [80] Power Management version 2

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
Flags: bus master, stepping, medium devsel, latency 0
Capabilities: [c0] Power Management version 2

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686,/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
Flags: bus master, medium devsel, latency 32, IRQ 19
[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
I/O ports at e000 [size=16]
Capabilities: [c0] Power Management version 2

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
Subsystem: Biostar Microtech Int'l Corp Unknown device f614,
Flags: medium devsel, IRQ 20
I/O ports at e400 [size=256]
Capabilities: [c0] Power Management version 2

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
Subsystem: Biostar Microtech Int'l Corp Unknown device 2200
Flags: bus master, medium devsel, latency 32, IRQ 18
I/O ports at ec00 [size=256]
Memory at e0112000 (32-bit, non-prefetchable) [size=256]
Capabilities: [40] Power Management version 2

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA controller])
Subsystem: ATI Technologies Inc Radeon 7000/Radeon VE
Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 21
Memory at d8000000 (32-bit, prefetchable) [size=128M]
I/O ports at c000 [size=256]
Memory at e0020000 (32-bit, non-prefetchable) [size=64K]
[virtual] Expansion ROM at e0000000 [disabled] [size=128K]
Capabilities: [58] AGP version 2.0
Capabilities: [50] Power Management version 2

sudo glxinfo | head
name of display: :0.0
display: :0 screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control,
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group

i could use some help. i guess i am more of a newb than i thought i was. thanks in advance

---

### Post by HermanAB on 2009-02-07
Hmmm, without trying to look at your problem... too complicated!

If you have a desktop problem, the easiest way to get back to normal is to create a new user account.

Cheers,

Herman

---

### Post by jocatoth on 2009-02-07
Thanks HermanAB

i dont know how to do that from the command line.

---

### Post by hellion0 on 2009-02-07
Try looking into either adduser or useradd for adding a new user via the commandline. Both ```
adduser --help
``` and ```
useradd --help
``` will give you info.

When you do use either one to actually add the new user, sudo will be required.

---

### Post by Aearenda on 2009-05-07
It's probably way too late now, but just in case anyone else finds this thread, creating a new user isn't likely to fix the OP's problem, since the GUI has to start in order to login to any user at all. 

I believe the procedure the OP followed would have modified the /etc/gdm/gdm.conf-custom file. 

To fix it, log in at a console (text-only) session (the GUI won't start, remember).
First make a copy of the file, just in case:
```
sudo cp /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom-backup
```

The command to edit the file is
```
sudo nano /etc/gdm/gdm.conf-custom
```

Remove the '-dpi 96' (or the whole [server-Standard] section) from this file and save it. If it isn't there, look in the file /etc/gdm/gdm.conf instead - but do not remove the server-Standard section from this file, and again, make a backup first!

GDM should start up again as before on the next attempt - give it a try (for 8.04):
```
sudo /etc/init.d/gdm start
```

On 8.10 and later, that should work too, but this is better:
```
sudo service gdm start
```

---

