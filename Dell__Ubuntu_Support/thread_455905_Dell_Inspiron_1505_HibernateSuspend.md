---
title: "Dell Inspiron 1505: Hibernate/Suspend"
date: 2007-05-27
forum: Dell  Ubuntu Support
---

### Post by Neuralgia on 2007-05-27
Now that Dell has this laptop, soes someone now how to make the suspend/hibernate to work?

or does it has something to do with the video card? (mine is an ATI :()

---

### Post by hardyn on 2007-05-27
It likely has everything to do with the video card:
what driver? ATI, Radeon, or fglrx?

try adding vga=791 to grub boot string.
eg:
..........quiet splash vga=791

---

### Post by Neuralgia on 2007-05-27
fglrx

ATI  x1300

(My whole system:
Dell Inspiron 6400
Intel Core 2 Duo T7200 @ 2.0GHz
ATI Radeon x1300
Intel Pro/Wireless 3945
Bluetooth)

*My card reader works OK (at least w/SD, don't have any other cards to try)
*My Wireless and Ethernet works OK
*My USB's work OK
*My Firewire works OK
*My graphics card works ok (I even have XGL session, with all desktop effects working perfectly... Compiz, Beryl is too much for me)
*My CD/DVD burner works OK

Things not working:
1. Hibernate/Suspend
2. External monitor / VGA port (Even though I haven't tried yet, I know this is a problem. I read some where there is a solution for Intel graphics, but mine is an ATI)
3. Modem (Conexant... I know there is a way, but I never use a modem, so haven't wasted my time in that. I also know that you need to pay for those, and the free version is only 14.4kbps)

Things not tested:
1. S-Video

> $ sudo gedit /etc/default/acpi-support

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="fglrx ipw3945"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql bluetooth"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

something that I've never worked out, is that on some tutorials they say to add "bluetooth" on my STOP_SERVICES, since my laptop comes with BT.

By defualt, this space was like this "mysql " (notice the space after mysql. How do I add BT:

1. STOP_SERVICES="mysql bluetooth"
2. STOP_SERVICES="mysql" "bluetooth"
3. STOP_SERVICES="mysql " "bluetooth" (noitce space after mysql)
4. STOP_SERVICES="mysql " "bluetooth " (notice space after mysql AND bluetooth"

=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

Just in case

$ lspci
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [ATI Mobility Radeon X1300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


$ lsusb
> Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  


---

### Post by Neuralgia on 2007-05-27
any ideas?

---

### Post by chriztofur on 2007-05-30
it's not simply a video card issue. i'm running feisty and have the 7300 using nvidia drivers, and still have an issue putting it to sleep. i found that disabling sync to vblank in beryl fixed it.

---

### Post by garion on 2007-06-01
I have an older version of dell e1505 (core duo, but also ati x1300), and I have never figured out how to get resume working (always black screen).  It worked with feisty beta, but stopped working with the final release, and I have tried a million different tweaks, none of them worked.  I read some got it to work on the same model but with ati x1400, but their tweak doesn't work on my x1300 :(.  Anyone has had luck so far?




> **Neuralgia said:**
> Now that Dell has this laptop, soes someone now how to make the suspend/hibernate to work?

or does it has something to do with the video card? (mine is an ATI :()

---

### Post by crazedgremlin on 2007-06-02
the dell 1505n is the ubuntu one I think - and by default it has intel graphics
does anyone know if suspend / hibernate works on this one?

---

### Post by bapoumba on 2007-06-03
Thread moved to "Ubuntu Dell Support" sub forum.

---

### Post by derred on 2007-06-03
That's odd. I have a Inspiron 6400(basically the same thing) and suspend and hibernation work great...
Once in 10-15 suspends I don't get my keyboard back and I have to suspend/resume again for it to work but that's not that serious a fault, at least for me.

I bought it last year so the ubuntu Dells weren't out yet.

---

### Post by paisteuser on 2007-06-04
> **crazedgremlin said:**
> the dell 1505n is the ubuntu one I think - and by default it has intel graphics
does anyone know if suspend / hibernate works on this one?

I own a Dell E1505 with the Intel integrated graphics. Suspend and resume work fine without any tweaking on Feisty (7.04).

---

### Post by rabideau on 2007-06-15
This is cross-posted from elsewhere on this site:

Here's how I fixed things... my problems were on one of the new Ubuntu-Dell e1505n machines.

My machine is running with the **nVidia card, Beryl, and wxga+** resolution.

I fixed the suspend hibernate by doing the following:
[LIST=1]
[*]Went to: Applications>>System Tools>>Sysinfo
[*]Opened Sysinfo and accessed nVidia driver info
[*]XServer XVideo settings: set both Sync to VBlank boxes to "BLANK"
[*]Opened Beryl Settings Manager General Options (go to the bottom of the page) and set Sync to VBlank to blank[/LIST] With those setting my suspend and hibernate work.

I hope this helps

---

### Post by fjgaude on 2007-06-15
> **paisteuser said:**
> I own a Dell E1505 with the Intel integrated graphics. Suspend and resume work fine without any tweaking on Feisty (7.04).

I have the E1505n with the nvidia 7300 board... suspend and resume work fine, but not hibernate. I'm still using the nv video driver, not the nvidia. I also have the 1680x1050 pixel screen. Amazing. Very happy with Dell and Ubuntu.

frank

---

### Post by neptho on 2007-06-15
I have a nearly-first-gen Inspiron 6400 with the ATI x1300 video.  This enables hibernate and suspend for me:

```
%grep -v -e '^#' /etc/default/acpi-support -e  '^$'
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST="fglrx ipw3945"
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
USE_DPMS=true
DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=true
ENABLE_CPU_SPEED_HARD=false
ENABLE_CPU_SPEED_GOVERNOR=true
```

I've also created a few scripts in /etc/acpi to lower/raise the rate the fglrx driver uses when on battery, and ipw3945 driver.  You can find that info in my post history.

I hope this assists you!

---

### Post by danielandrews on 2007-06-21
I'm also having this problem with the 1505n & the NVIDIA 7300 (restricted drivers).  I've tried all of the relevant items I can find around here, to no avail.

---

### Post by rabideau on 2007-06-21
Hi Daniel,

I am certain this is redundant but did you do everything in my post #11?

I have done this a couple of times and it works fine.  One additional item I have noted and that is you need to allow the machine to return from hibernate BEFORE hitting any keys.  I f you are premature on key entry the system hangs.

---

### Post by danielandrews on 2007-06-21
> **rabideau said:**
> Hi Daniel,

I am certain this is redundant but did you do everything in my post #11?

I have done this a couple of times and it works fine.  One additional item I have noted and that is you need to allow the machine to return from hibernate BEFORE hitting any keys.  I f you are premature on key entry the system hangs.

Yeah, I gave this a try and it didn't work for me.  I even reset the NVIDIA settings before doing it just to make sure everything worked.

It does, however work with the default nv drivers.  I'm not sure why it's not working, but I've been looking around to see if others maybe have another solution I could try.

---

### Post by rabideau on 2007-06-24
Hi Daniel,

I blew up my xorg.conf file yesterday and had to reinstall it from scratch using the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

From there I needed to restart the restricted nVidia driver and then restart my machine.  The reason I mention this is that now my hibernate works much better and I have better screen resolution.  Perhaps this approach will help you solve your situation.

---

### Post by Merritt.kr on 2007-06-24
Hey. I went through some hell to get Hibernate working, but it works just fine and dandy now. Check out the thread I got it worked out on:

[http://forum.notebookreview.com/showthread.php?t=126332&highlight=merritt](http://forum.notebookreview.com/showthread.php?t=126332&highlight=merritt)

By the way, I have a 6400 (same as 1505) and an ATI x1400.
Hope that helps! Worked for me. :)

---

### Post by danielandrews on 2007-06-26
> **rabideau said:**
> Hi Daniel,

I blew up my xorg.conf file yesterday and had to reinstall it from scratch using the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

From there I needed to restart the restricted nVidia driver and then restart my machine.  The reason I mention this is that now my hibernate works much better and I have better screen resolution.  Perhaps this approach will help you solve your situation.

what does the -phigh flag(s) do? just curious as to what I'm telling my OS to do.

---

### Post by rabideau on 2007-06-26
Hi Daniel...

I don't really know.  The command is in the xorg.conf file and states to use the string if there's a problem, which there was.

I blindly followed it and it worked.  I don't know what else to say... I'm really happy with my results, but perhaps I was just lucky.  I never even thought twice about it though.

No wonder I'm not in charge...:o

---

### Post by danielandrews on 2007-06-26
haha!

Well, I tried that, to no avail. So far, I've found that I can hibernate/suspend with the restricted drivers enabled, but if I enable desktop effects, hibernate and suspend brings me back to a black screen, with the cursor the only thing showing.

---

### Post by rabideau on 2007-06-27
Hi Dan,

RU using Beryl/Emerald for your desktop? If so which theme engine...

I can send you all my settings if that might help.

---

### Post by rabideau on 2007-06-27
Here are screen shots of all my relevant settings... at least relevant so far as I know.  I hope this helps.:)

File add failed... please PM me with an email address and I'll send the fil to you.

---

### Post by krull_etc on 2007-06-27
Have you made any changes in your RAM size?  I have the E1505n with nVidia.  After adding Beryl, I followed post #11 to get the hibernate working again.  Hibernate quit working when I added more RAM. I had to adjust the size of the swap partition.

---

### Post by danielandrews on 2007-06-27
> **rabideau said:**
> Hi Dan,

RU using Beryl/Emerald for your desktop? If so which theme engine...

I can send you all my settings if that might help.

I'm running the default Metacity in GNOME.  I have the restricted NVIDIA drivers, but no desktop effects enabled.  I went through the steps in #11, to no avail.

---

### Post by danielandrews on 2007-06-27
> **krull_etc said:**
> Have you made any changes in your RAM size?  I have the E1505n with nVidia.  After adding Beryl, I followed post #11 to get the hibernate working again.  Hibernate quit working when I added more RAM. I had to adjust the size of the swap partition.

krull_etc,

I have the 1GB that my e1505n shipped with, so I'm not sure what is causing this.

---

### Post by derred on 2007-06-27
Both hibernate and suspend work with 2 programs causing an exception: Azureus and Beryl
If any or both of them are running i get a hal error and the laptop stays on. 

this is my /etc/default/acpi-support file:

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql bluetooth"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

If I change MODULES_WHITELIST="" to MODULES_WHITELIST="fglrx" I can get suspend to work even under beryl but hibernation doesn't work at all after that.

---

### Post by rabideau on 2007-06-30
Hello derred...

Here is a copy of my file content. I hope this helps you out.;)


# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

---

### Post by neptho on 2007-06-30
Since everyone else is posting theirs, this acpi-support I have modified works with both ATI and NVidia; I do not know if anyone has tested it with the Intel drivers; it'll likely require an addition to the MODULES_WHITELIST, but I don't know the name of the module for that offhand, so I just added 'intel'.

```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="fglrx intel ipw3945 nvidia"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true
```

---

### Post by jppaynesr on 2007-07-01
Ditto  -Dell E1505 with pre-installed Feisty. Suspend works OK. WiFi & USB both come back up.

Mr Neuralgia; are you sure your E1505 came with Bluetooth? It is an option, not standard. The BT card is inside the small side door in the battery compartment.

---

### Post by rabideau on 2007-07-06
Hi all,

I have noticed that I get the following error message on entering and exiting hibernation:

ACPI set timing mode failed (on ata1 & 2)

I think the error may relate to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109529](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109529)

Any knowledgeable folks out there able to confirm or 'rule out' the issue???

---

