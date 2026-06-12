---
title: "Elementary won't boot, computer boots straight into Windows"
date: 2014-06-01
forum: Debian
---

### Post by Amor_K on 2014-06-01
I tried a dual boot setup on my ASUS Zenbook UX31A to no avail, the computer keeps booting right into windows. GRUB does not show up at all. I tried boot-repair from the LiveUSB but it doesn't work. Here is the paste bin: [http://paste2.org/O9M25J1n](http://paste2.org/O9M25J1n)
Can someone please help me, I just want to get this working.

---

### Post by bapoumba on 2014-06-01
*Thread moved to **Other OS/Distro Support**.*

---

### Post by Stinger on 2014-06-05
Hi Amor_K
Welcome to the Ubuntu forums.
I think your problem is related to 'secure boot' and 'UEFI-BIOS'
elementary Luna is based on the 'old' and original Ubuntu 12.04 with no support for secure boot and UEFI-BIOS.
Meaning that if you have UEFI and secure boot enabled , you need to disable it. 
> Windows 8 + Ubuntu

We first need to know with what type of motherboard options we are dealing with. Open a terminal (By going to the start menu and typing **powershell** for example) and run the terminal as an Administrator (Right Click the app that will show in the start menu and select Run as Administrator). Now type **Confirm-SecureBootUEFI**. This can give you 3 results:

**True** - Means your system has Secure boot and is Enabled

**False** - Means your system has Secure boot and is Disabled 

**Cmdlet not supported on this platform** - Means your system does not support Secure boot and most likely you do not need this guide. You can install Ubuntu by simply inserting the LiveCD or LiveUSB and doing the installation procedure without any problems. Taken from the first answer/guide here: [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

There is a guide on [Howto download and install elementary Luna]("http://www.elementarynow.com/what-is-elementary-3/installing-luna/") on elementarynow.com, scroll down to "**3. Important things to consider before installation**" and see if the four step guide helps you.

More on [secure boot]("https://help.ubuntu.com/community/UEFI#SecureBoot") and oldfred has a thread about [UEFI Installing Tips]("http://ubuntuforums.org/showthread.php?t=2147295") that might help you.

['May the force be with you']("https://www.youtube.com/watch?v=D9XYKY4Km20") ;)

---

### Post by Stinger on 2014-06-05
Just scrolled through your paste bin.
You seem to be running win7 and no 'secure boot' 
Just use the [Howto download and install elementary Luna]("http://www.elementarynow.com/what-is-elementary-3/installing-luna/") guide and you should be fine :) 

Your problem seems to be missing or damaged grub but for some reason it can't be fixed using boot repair.
> Recommended-Repair
This setting will purge (in order to fix packages) and reinstall the grub2 of sda5 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s

---

