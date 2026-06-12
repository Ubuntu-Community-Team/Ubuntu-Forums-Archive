---
title: "Corrupted /etc/X11/xorg.conf ??"
date: 2011-11-09
forum: Desktop Environments
---

### Post by J Blain on 2011-11-09
Am I the only one experiencing this ?

After upgrading from 11.04 to 11.10 on my Dell MX11 (latest NVIDIA drivers installed), I now am incapable of setting up an external monitor.

If I try (using /usr/bin/nvidia-settings), the monitor is recognized but after restarting :

1) The desktop background on the external monitor is white (not my normal background)

2) The top menu on both monitors are not the Gnome classic menu (Application, Places etc) but some unusable generic menu (File, Go, Help etc) and I am left with my on off button

3) All Menu panel applets are gone

This is really really annoying. Any input would be greatly appreciated.

Regards

Jacques Blain

---

### Post by Claus7 on 2011-11-09
Hello,

a quick feedback that I can think of is: have you saved the changes you do in nvidia-settings as root? Because if you do not, every time you reboot, your system will revert to its original (not convenient) for you state.

Regards!

---

### Post by J Blain on 2011-11-09
> **Claus7 said:**
> Hello,

a quick feedback that I can think of is: have you saved the changes you do in nvidia-settings as root? Because if you do not, every time you reboot, your system will revert to its original (not convenient) for you state.

Regards!
Yes I did originally run nvidia-settings with sudo.

Jacques

---

