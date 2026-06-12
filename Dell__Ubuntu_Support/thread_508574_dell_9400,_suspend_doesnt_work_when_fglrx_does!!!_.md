---
title: "dell 9400, suspend doesnt work when fglrx does!!! wtf."
date: 2007-07-24
forum: Dell  Ubuntu Support
---

### Post by puccaso on 2007-07-24
i use feisty
but i have the same problem with gutsy..

i have to build the fglrx manually to get beryl to work, in other words - my 3d opengl stuff dont work if i dont compile myself...

but if i compiile myself - the fglrx i use seems to stop suspend from working.

my suspend works fine, if i use the restricted moduels in feisty, but its not there in gutsy - so my suspend crashes.


iv read alot of people writing "that it suspends, but doesnt remove"

well, mine get stucks on the suspending part.

the screen dies,  but power light remains on, 
and it doesnt return...
i cant ctrl+alt+bakspace
i have to power down
and power up..




this is my acpi stuff..


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
MODULES="fglrx ipw3945"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

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
```






```
mahir@mahir-laptop:/tmp/updatestuff$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6650 (8.39.4)

mahir@mahir-laptop:/tmp/updatestuff$ 

```


any help please?

---

### Post by RangerDanger on 2007-07-24
It seems too simple, but try it.

Change this line:  POST_VIDEO=true to read POST_VIDEO=.

Make sure you use the period and not just a blank.

---

### Post by puccaso on 2007-07-25
nope. doesnt work

---

### Post by Slimo on 2007-08-13
It seems like I am having a similar problem....running Feisty with a Radeon 9800 card using the open source ati drivers.

The computer often locks up after the screensaver has been running for a while, or will not come out of suspend (power management) mode.  I have tried changing the power management settings to 'never' but the computer still tries to suspend!!

Any help would be appreciated!

---

### Post by puccaso on 2007-08-13
i dont have the issue with opencourse drivers..
in feisty, i useded the xorg-fglrx-driver in the restricted
and i had no problem

but the propriotry fglrx module in both gutsy and feisty locks things up for me.



hopefully dell's pressure on ATI to stop ***** footing around, will aid our problems.

Godspeed!

---

