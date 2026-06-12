---
title: "Gnome-Power Backport?"
date: 2005-08-22
forum: Deferred/Invalid Requests
---

### Post by Manny C on 2005-08-22
Hi all..

Wondering whether there were any plans on backporting gnome-power?

See [http://gnome-power.sourceforge.net/](http://gnome-power.sourceforge.net/)

I'm not in a rush as suspend and hibernate work for my Compaq Presario 2267 out of the box.

The added functionality of gnome-power would be great. It seems that a breezy package has also been created.

---

### Post by diensthunds on 2005-08-22
My ? is, how did ya get the suspend / hibernate to work? I have a Presario 2100 and have yet to get either to work

---

### Post by Manny C on 2005-08-22
I don't know. The only thing I had to do to get suspend working was uncomment the ACPI_SLEEP line in the acpi-support script.

```

# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. It should look something like MODULES="e1000 ipw2100"
MODULES=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

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

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "
``` 

Then to suspend, (using Ubuntu), I click System->Log Out->Suspend the Computer.

I tried to get these features working in kubuntu through klaptop...no luck.

---

### Post by Game_Ender on 2005-12-22
I would like to second the request for a gnome-power-backport. Or is it already in the backports repository?

---

### Post by jdong on 2006-01-02
An earlier (0.2.8) backport has been done, and the Ubuntu devs say that any more backporting of this is pointless without upgrading the underlying hal/dbus framework... So I don't think I'll do any more gnome-power stuff :)

---

