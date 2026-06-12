---
title: "Second monitor not detected on cold boot."
date: 2009-04-29
forum: Desktop Environments
---

### Post by TheGolfball on 2009-04-29
I am using Ubuntu Linux 9.04 with the nVidia 180.44 drivers. My system has an EVGA 122-CK-NF67-A1 motherboard with two XFXForce GeForce 7600 GT video cards. I have one LG W2042TQ digital flat screen monitor digitally conected to each video card (2 monitors total, one connected to each card). When I do a "cold boot" both video cards are detected but only the first one correctly detects its attached monitor. The monitor on the second card remains "asleep". If I then perform a reboot ("warm boot") then everything is detected correctly. This phenomenon is consistently repeatable. I would appreciate any help on this because I don't know if its related to the nVidia drivers, the MotherBoard bios, monitors, Linux X.org, etc.

The cold boot Xorg.0.log file contains (among many other things) the following:
(II) NVIDIA(GPU-1): No display devices connected; falling back to CRT-0
(ww) NVIDIA(GPU-1): Unable to read EDID for display device CRT-0

Later there are a few configuration error messages apparently related to the inability to correctly detect the monitor on GPU-1.

The warm boot works great and the error messages do not appear

I get no display problems under Windows XP so I don't think that it's the MB bios. Thanks.

---

