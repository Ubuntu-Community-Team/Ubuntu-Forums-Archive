---
title: "osd was here, now it's gone"
date: 2006-09-11
forum: Desktop Environments
---

### Post by uturn on 2006-09-11
When I first installed Ubuntu 2 days ago onto my Thinkpad t41p, the on screen display that accompanied volume adjustments from the special keys worked fine. Now, however, after trying a window manager other than Gnome, and using tpb, the OSD is gone. I have uninstalled tpb, and reversed the changes I made to get it working. Still, the OSD is absent. Can anyone help? What program(s) provides the OSD?

Thanks.

---

### Post by uturn on 2006-09-20
I figured it out, so I'll post here in case it helps anyone else.

The mistake I made was changing the keyboard shortcuts for adjusting volume control. To fix, I used the Keyboard Shortcuts prefences app to set the up, down, and mute hardware buttons as the shortcuts. So now the hardware buttons are once again integrated with the software volume control, and I see the OSD when I adjust.

What happens is the hardware buttons send acpi events which are configured to use acpi_fakekey to send fake keypresses to X. So using this method, you could configure any hardware key or button that sends an acpi event to do anything a keyboard shortcut could do.

---

