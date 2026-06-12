---
title: "[SOLVED] Screen shifts after suspend"
date: 2006-12-11
forum: Desktop Environments
---

### Post by afilonov on 2006-12-11
I have intermittent problem with Edgy on System76 Gazelle Performance. Sometimes after waking up from suspend login screen shifts left. Shift happens in several steps, each about 1/20 of the screen. If I log in, the whole picture is shifted, from 1/8 to 1/4 of the screen, always to the left. Strangely enough, mouse position is correct (i.e. it's not shifted with the screen). I have standard installation with Nvidia 1.0-9629 drivers. The only way to fix this problem is to restart gdm from command prompt. Haven't tried with standard drivers, it's not easy to catch. Sometimes happens every day, sometimes after 6 or 7 suspend cycles only.

---

### Post by afilonov on 2007-01-07
OK, I found the trigger for the shift and also a workaround.
Shift happens when there are output lines on the console screen (Ctrl-Alt-F1). I had ntp-server restart enabled on ip address change (in /etc/network/if-up.d), which created 5-6 lines output on the console, each line making one shift. After I disabled it, I have only one shift, created by "Starting up..." line on the console. In this case, if I do Ctrl-Alt-F2 and then Ctrl-Alt-F7 to return back to GUI, screen shifts back to normal.

I still don't understand several things.

1. Why I have output from ntp-server restart on the console?
2. Why is the shift?
3. Why it only starts happening after 4-6 suspend-wake up cycles?

Hardware/software specifics.

From Nvidia xserver setup settings:

Graphics Processor:      GeForce Go 7300
VBIOS Version:             05.72.22.41.79
Memory:                      256 MB
Bus Type:                    PCI Express 16X
Bus ID:                       1:0:0
IRQ:                           169
Display Devices:           AUO (DFP-0)

Nvidia driver 1.0-9746 (same problems with 9629 and 9631).
Nvidia native AGP, intel_agp module blacklisted. I had same problem with intel_agp, I disabled it and switched to Nvidia AGP to make glx work.

I wonder if anybody else had some similar problem?

---

### Post by Chouca on 2007-01-11
I have the same problem intermittent at suspend. Normally it shifts half the screen:-? 

I have not seen any pattern in why it happens, but I will see if shutting down the terminal(s) will make the problem disappear. 



I run Icewm on Edgy.

Regards

Martin

---

### Post by Chouca on 2007-01-17
My problem was not of the same type, it seems it was related to ROX because I removed ROX and installed idesk instead and now the screen shift is gone.

/Martin

---

### Post by afilonov on 2008-05-07
Gutsy solved problem once and for all. Never happened with Gutsy.

---

