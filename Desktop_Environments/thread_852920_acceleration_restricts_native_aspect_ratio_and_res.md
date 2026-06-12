---
title: "acceleration restricts native aspect ratio and resolution from working"
date: 2008-07-08
forum: Desktop Environments
---

### Post by trossthree on 2008-07-08
Greetings

I have a Nvidia 5600 ultra video card and a Westinghouse Wide screen LCD monitor. My native resolution is 1440x900 and it works fine except when I enable the 3d acceleration. When I enable the 3d acceleration I lose my native aspect ratio which is wide screen and my resolution will not set any higher than 640x480.

---

### Post by overdrank on 2008-07-08
> **trossthree said:**
> Greetings

I have a Nvidia 5600 ultra video card and a Westinghouse Wide screen LCD monitor. My native resolution is 1440x900 and it works fine except when I enable the 3d acceleration. When I enable the 3d acceleration I lose my native aspect ratio which is wide screen and my resolution will not set any higher than 640x480.

Hi and have you installed nvidia settings via synaptic manager. Then use the alt, F2 keys  and enter the command ```
gksu nvidia-settings
``` then adjust your resolution there.

---

### Post by bimmerd00d on 2008-07-08
in Compizconfig settings manager, make sure in General Options, Display Options that "Detect Outputs" is either checked, or the proper resolution is in the bottom area.

---

