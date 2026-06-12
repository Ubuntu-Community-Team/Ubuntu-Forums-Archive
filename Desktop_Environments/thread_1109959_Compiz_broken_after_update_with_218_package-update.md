---
title: "Compiz broken after update with 218 package-updates"
date: 2009-03-29
forum: Desktop Environments
---

### Post by mig96 on 2009-03-29
After an update with 218 packages showed up in the tray, I went like oh well what the hell and installed all of them.  Big mistake.  

It looks like xorg updates break nvidia configs, so now compiz isn't working.  I looked on Google and UbuntuForums and found a few old threads that told me to redo a few broken links (ln extensions/nvidia-glx.180.29 or something to main folder) in some folder, I did that and it still doesn't work.

The output it gives me goes like this.

Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/kwin

---

### Post by mig96 on 2009-03-30
Fixed by reinstalling nvidia driver. =)


For those of you who don't want to, libglx.so MUST BE A SOFTLINK not a hardlink.

---

### Post by danteuk on 2009-03-30
I had the same problem. The re-install of Nvidia driver fixed it for me too. Thanks :D

---

