---
title: "Session closes after program Quit"
date: 2013-01-25
forum: Desktop Environments
---

### Post by PhilOSparta on 2013-01-25
I have two Inspiron 530 systems with Xubuntu/Xfce, and both have been operating perfectly for about a year. A recent routine software update seems to have caused the problem on both machines.

Problem:  Fresh boot -> start up Gimp -> Quit Gimp -> Gimp freezes and after 20 seconds or so the system closes the session and provides a login screen for a new session.  Gimp is only used as an illustration here.  Chromium also causes the same response.  I've removed Chromium from my system to isolate the problem.  I figure that this problem should easily be found since it can be duplicated over and over, but I've been unable to find it.

Other threads with similar symptoms have leaned on the video drivers as the source of the problem.  I've been unable to find a fix in those threads.

Running this command:
lspci -k | grep -A3 -i vga

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8300 GS] (rev a1)
	Subsystem: NVIDIA Corporation Device 0494
	Kernel driver in use: nvidia
Kernel modules: nvidia_current_updates, nvidia_173_updates, nvidia_current, nvidia_173, nouveau, nvidiafb

Any thoughts on further isolation of this problem would be appreciated.
Thanks,
Phil

---

### Post by black veils on 2013-01-25
access grub menu (you may need to hold the Shift key at boot), then choose previous kernel. does this fix it?

if it does, you could set it as default somehow or find out about removing the latest kernel and locking to the version which works for you.

---

