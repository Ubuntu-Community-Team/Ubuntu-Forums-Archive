---
title: "hardware + software volume control"
date: 2006-09-18
forum: Desktop Environments
---

### Post by uturn on 2006-09-18
Does anyone have a good idea for how to integrate the hardware and software volume controls on my Thinkpad T41p? The mute is especially annoying because the software mute doesn't cut out the system beep.

---

### Post by uturn on 2006-09-20
I figured it out, so I'll post here in case it helps anyone else.

The mistake I made was changing the keyboard shortcuts for adjusting volume control. To fix, I used the Keyboard Shortcuts prefences app to set the up, down, and mute hardware buttons as the shortcuts. 

What happens is the hardware buttons send acpi events which are configured to use acpi_fakekey to send fake keypresses to X. So using this method, you could configure any hardware key or button that sends an acpi event to do anything a keyboard shortcut could do.

---

