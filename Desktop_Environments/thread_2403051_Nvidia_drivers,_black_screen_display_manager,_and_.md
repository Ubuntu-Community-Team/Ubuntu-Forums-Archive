---
title: "Nvidia drivers, black screen display manager, and 4 displays"
date: 2018-10-06
forum: Desktop Environments
---

### Post by devodl on 2018-10-06
Posted as **Solved** because there is a workaround but it would be interesting to learn the root cause.

Here's my story
Nvidia GTX 1050 Ti card with 4 display devices (1 DisplayPort, 2 HDMI, 1 DVI)
New system update comes out and during reboot the system hangs.  Prior experience has shown that the Nvidia drivers often need to be updated or reinstalled.  
Ctrl+Alt+F2, login as root, kill processes using Xserver, reinstall the Nvidia drivers, reboot and everything is fine unless...   
A fourth display (in my case a Samsung TV) is physically connected through HDMI. 

**Symptom**  
When a fourth display is plugged in during a reboot and when gdm/lightdm are starting then a black screen appears on display #1 and the other displays remain idle (no signal).
**Solution**: Unplug the fourth display and the system will boot and display properly. (It may even complete the current boot after a few minutes).

Note: Once logged in the 4th display can be plugged back in and used to expand the desktop. 

It is not clear why the display behaves in this manner but I figured I would post the symptoms and workaround solution for those who have 4 displays.

FWIW,
Steve

---

