---
title: "Disable passwordless logon?"
date: 2010-04-21
forum: Desktop Environments
---

### Post by mma8x on 2010-04-21
Running a live usb of 9.10/kde, and i can't seem to get it to require a password for logon.  i uncheck "enable passwordless logon" in the convenience tab in settings.  if i log out/in, it requires a password, but if i reboot it will just boot directly to the desktop.  i don't want it to be that easy to access my files if i lose this drive (in fact, i'd like to encrypt the drive, but that's another issue...we'll start with just needing a pw)

---

### Post by thomasaaron on 2010-04-21
I believe you have to actually install Ubuntu to disable that feature. The USB image isn't really meant to be your permanent OS. It is for testing, performing installations, recovery work, etc...

---

### Post by Untitled_No4 on 2010-04-21
Still in Convenience tab, do you have "Enable Auto-Login" checked by any chance?

---

### Post by mma8x on 2010-04-21
well, i don't see why it has to be temporary.  i carry my usb drive with me rather than a laptop for use on work, friend's computers, etc.  i know that it's secure for accessing my online accts or whatever, it's set up like i like, i can vnc into my home computer.  and yes, "enable auto-login" IS checked.  i uncheck, reboot, and there it is checked again...

---

### Post by lisati on 2010-04-21
You might want to create a "persistent" copy on your USB device, mentioned [here]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by mma8x on 2010-04-21
> **lisati said:**
> You might want to create a "persistent" copy on your USB device, mentioned [here]("https://help.ubuntu.com/community/Installation/FromUSBStick").

yeah, that's what i have.  used usb-creator.

---

### Post by Untitled_No4 on 2010-04-21
I can't help you much besides telling you that I had it done once. May have been using the dd command to put the iso on the USB but I can't tell you for sure.

---

