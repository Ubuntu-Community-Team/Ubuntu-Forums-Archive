---
title: "Unable to change screen resolution"
date: 2009-02-19
forum: General Help
---

### Post by ghd on 2009-02-19
Using the live CD (8.10) my laptop screen was correctly identified and I could change the refresh rate and resolution. After install to the hard drive the screen is not detected, resolution is locked at  1024x768 and the refresh rate is showing 0Hz

I have tried 
 xrandr
 sudo dpkg-reconfigure xserver-xorg 
 
xorg.conf has
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

which appear to be the same as when booted from the live cd

---

### Post by anlag on 2009-02-19
Might help if you posted up what graphics card you have. Sounds a bit like a drivers problem.

---

### Post by mikewhatever on 2009-02-19
Did you check under System->Admin->Hardware Drivers? Is there a proprietary one available for your card? Which catrd is it, by the way?
What resolution and refresh rate did you have from the live cd?

---

### Post by ghd on 2009-02-22
The laptop is a IBM Thinkpad G40 with and Intel 855GM or 852 Video Chipset. Chipset. From the Xorg.log I can see the correct driver is loaded
"(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 4.1
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8000 kB
(II) VESA(0): VESA VBE OEM: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS"

While booted from the live CD the screen is shown as a 14" laptop screen and had 1024*768, 800*600  and 61,65 and 70 Hz as options.

---

### Post by paydaydaddy on 2009-02-22
Sometimes you will need to configure the X Server. It often can't display any larger than 1024 x 768. Here is a quick way to do so. 

   1. Open up a shell terminal session
   2. Type in the following command:
      Code:

      sudo dpkg-reconfigure -phigh xserver-xorg

   3. Enter your password at the prompt. You will notice it won't actually show up on the screen, this is normal.
   
   4. exit out of the session and reboot to restart the X Server. you should now be able to choose the correct resolution.

---

### Post by ghd on 2009-02-25
Tried
> **paydaydaddy said:**
> 
      sudo dpkg-reconfigure -phigh xserver-xorg
.
But with no change. Anyone suggest why the live CD correctly configures the display but the install (no patches) does not?

---

