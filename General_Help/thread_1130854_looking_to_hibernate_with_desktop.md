---
title: "looking to hibernate with desktop"
date: 2009-04-20
forum: General Help
---

### Post by linuxology on 2009-04-20
I am looking to hibernate with my desktop and have not been successful when I tried.  Is there a site that I can read up on it and is this a common thing that other people do?  I am looking to save electricity when I am away without powering down the machine.  It is a desktop so I guess it could be a hardware compatibility issue.  My motherboard is a Biostar T500.  Thanks to all who post

---

### Post by kiridude on 2009-04-20
It's not really clear what you're trying to do:
Are you trying to set the computer to automatically hibernate after a certain period of inactivity, or do you want to manually make it hibernate?

---

### Post by linuxology on 2009-04-22
Manually hibernate

---

### Post by kiridude on 2009-04-22
click on the red power button on your panel (i think top because I have removed the panels from my screen). This is the same button you would use to shutdown your computer. when you click on it, you will have several options. One is hibernate.

If you do not have this button, right click on a panel and select "add to panel" > then select "shut down" > add. when you click this button that was added to your panel, one of the options will be "hibernate."

---

### Post by linuxology on 2009-04-22
I know how to hibernate, but it does not work.  It goes to sleep and will never wake back up and I have to hold the power button to shut down the computer.

---

### Post by kiridude on 2009-04-22
Oh, I asked you specifically what you were trying to do and in your last post, you said, "manually hibernate."

Anyway, if it doesn't wake up, try the following:

```
gksudo gedit /etc/default/acpi-support
```

Then locate and edit the following lines to match the below:

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true 

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

Then close the window and click "save" at the prompt.

---

