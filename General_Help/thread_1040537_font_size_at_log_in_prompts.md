---
title: "font size at log in prompts"
date: 2009-01-15
forum: General Help
---

### Post by jocatoth on 2009-01-15
i am running ubuntu 8.04 on an athalon xp 2600 board with a ati raedon 7000 pci graphics card. somewhere after going from 7.10 to 8.04 the font size in the login user and password boxes is too small to see. the screen resolution settings in gnome do not have any effect on the font in the login boxes.

i opened a terminal ran apt-get to remove xserver-xorg and to reinstall the same. it prompted me to try to fix x server. i restarted ubuntu and the font size is unchanged.

i do not have alot of experience of working from the command line. i guess i am a bit of a newbie. thanks for any suggestions and help

---

### Post by dcstar on 2009-01-15
> **jocatoth said:**
> i am running ubuntu 8.04 on an athalon xp 2600 board with a ati raedon 7000 pci graphics card. somewhere after going from 7.10 to 8.04 the font size in the login user and password boxes is too small to see. the screen resolution settings in gnome do not have any effect on the font in the login boxes.

i opened a terminal ran apt-get to remove xserver-xorg and to reinstall the same. it prompted me to try to fix x server. i restarted ubuntu and the font size is unchanged.

i do not have alot of experience of working from the command line. i guess i am a bit of a newbie. thanks for any suggestions and help

Chances are the /etc/X11/xorg.conf file has settings that are now invalid.

Do a forum search and you should get some posts on fixing this file.

---

### Post by jocatoth on 2009-01-17
i have tried several things. i have removed the xorg.conf revised files. i have then run    sudo dpkg-reconfigure -phigh xserver-xorg which should as i understand it build a new xorg.conf file. also as i understand it xserver-xorg should use the latest such file.

when i do this, for whatever reason the font size (perhaps screen resolution) within the login user box and login password box still is not changed for the better. the resolution on the, for lack of a better description, start up splash screen seems right.

i have looked at some of the forums regarding ati graphics problems. i realize that ati seems to give many folks problems. i also realize i have an older card.
here is some info on my system.

lspci -v
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

i am not sure what else to try.

thanks to all for any suggestions or help you might give.

---

### Post by jocatoth on 2009-01-19
i guess i wonder if this is a driver issue not specifically a xserver-xorg issue. i could use help structuring my efforts at finding a better driver for my graphics card and making it work.

---

### Post by jocatoth on 2009-02-01
i have not had any success in changing the font size of the login and password boxes.

i have tried several things relative to ati drivers and the like

i was wondering if it had anything to do with /etc/gdm/gdm.conf. i have compared this file on the small font machine with another machine running hardy that has a readable font size in those boxes.

anyone have another idea about this?

---

### Post by lukew on 2009-03-28
> **jocatoth said:**
> i have not had any success in changing the font size of the login and password boxes.

i have tried several things relative to ati drivers and the like

i was wondering if it had anything to do with /etc/gdm/gdm.conf. i have compared this file on the small font machine with another machine running hardy that has a readable font size in those boxes.

anyone have another idea about this?

I got this as well. I remember reading that this was an upgrade issue for hardy. Are you using hardy? my desktop is and I have this issue but my laptop is on intrepdi which does not have the issue. I remember reading a sticky post around the time hardy first came out on how to fix this. I can not seem to find any reference to it now.
Will keep looking and post back if I find anything.
Luke

---

### Post by lukew on 2009-03-28
> **lukew said:**
> I got this as well. I remember reading that this was an upgrade issue for hardy. Are you using hardy? my desktop is and I have this issue but my laptop is on intrepdi which does not have the issue. I remember reading a sticky post around the time hardy first came out on how to fix this. I can not seem to find any reference to it now.
Will keep looking and post back if I find anything.
Luke

Looks like I do not have the used font installed.

/usr/share/gdm/themes/<themename>/<themename>.xml

---

### Post by jocatoth on 2009-03-28
thanks for the reply.

i'm running hardy. i have just lived with this situation, it is on a dual boot computer that i mostly use in xp. the machine i use the most is older equipment and is also running hardy. it is running fine. i was working on the problem computer with the small login font and broke gnome and x in a way that i did not know how to fix so i reinstalled. i did notice that on the live cd it had small login fonts also. this suggests to me that the hardware requires a specific driver configuration but i do not know where to put the correct driver (or what that is for that matter) since it appears really before hardy really gets going.

---

