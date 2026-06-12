---
title: "What are the multimedia capabilities of the E1505 N?"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by last1 on 2007-06-25
I'd like to get one of those Dell ubuntu laptops to replace my aging multimedia setup in the living room, and would like to know if an E1505 N with default hardware configuration will be able to handle that.

Will the default video card, that Intel 950 GMA, be fast enough to play 720p videos without stuttering or lag, and does it come with an S-video output? How powerful is it in Linux? What kind of driver does it use, is it open source, and is it a quality driver, and does it have something similar to the nvidia-settings application I get when using an nvidia card to tweak X settings?

Is it worth the extra money to get the nvidia card instead if I'm just going to be using it for video playback and desktop effects?

---

### Post by rivasdiaz on 2007-06-27
I bought one of those, with the best microprocessor available and the intel video card. I can say that they are fantastic. Desktop Effects works (although once in a while a see some video problem, I hope it is due to the still low quality of the compiz code). I can reproduce DVDs full screen. It has a S-video output.  suspend/hibernate/resume works fine.

From what you asked, the missing part is the Nvidia-like config app. I read recently a blog in planet ubuntu that a new GUI for configuring X is being developed so next ubuntu will close this also, and the packages are available from the developer to feisty.

---

### Post by Paul S on 2007-06-27
I have an E1505 with the nvidia card .. it'll work on all that stuff too.  But, I can't get suspend / hibernate to work because of the nvidia driver.  Probably this will get fixed in the future releases.

regards,

---

### Post by neptho on 2007-06-28
The following /etc/default/acpi-support works for me, and with a modification, works for Frank, so it should work universally, now, for both ATI and NVidia:

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
MODULES_WHITELIST="fglrx nvidia ipw3945"


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
# Ignore these last two lines, they're for my custom ACPI scripts to lower 3945 power drain and force CPU to a slower state
ENABLE_CPU_SPEED_HARD=true
ENABLE_CPU_SPEED_GOVERNOR=false
```

---

### Post by bunted on 2007-06-28
Definetly get the nvidia card if you want no hassle multimedia, just because of the lack of a nvidia type settings GUI.  I have one of the first 1505n's with the integrated intel video card.  S-Video may be a port on the back, but it does not work.  Desktop effects work fine with the plain intel, but there are some occasional artifacts post-effect.  I regularly hook up mine to my HDTV, and play videos with only the occasional hiccup, even when the source is streamed from my smb server.  I am using the i810 driver with the 915resolution patch, which is the only way I had to enable high resolutions.

---

### Post by fjgaude on 2007-06-29
> **Paul S said:**
> I have an E1505 with the nvidia card .. it'll work on all that stuff too.  But, I can't get suspend / hibernate to work because of the nvidia driver.  Probably this will get fixed in the future releases.

regards,

Do as poster netho says, I did, and my suspend/hiberate/resume works now with the nvidia driver. It always did with the nv one.

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="nvida ipw3945"

I think that line does it, but change the others too.

frank

---

### Post by last1 on 2007-06-29
Thanks for the great replies everybody, those are exactly the kinds of things I wanted to know. Sounds like the Intel card is good but the Nvidia is better for my needs, since I for sure will be depending on using the S-video out. As it is right now I've got a tower in the living room using a dual-monitor configuration, one using the VGA port and the other S-video to the TV, and its very nice just a bit slow. 

bunted please let me know if you end up seeing a fix for the S-video problem anytime soon, sounds like if that gets resolved I could go for an Intel card instead.

---

