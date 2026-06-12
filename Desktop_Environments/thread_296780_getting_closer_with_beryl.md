---
title: "getting closer with beryl"
date: 2006-11-10
forum: Desktop Environments
---

### Post by kman14 on 2006-11-10
i'm getting quite excited now - i think i'm almost there with beryl.

i'm just wondering if anyone can tell me how to fix this:

klmc@klmc-desktop:~$ beryl-start
bash: beryl-start: command not found
klmc@klmc-desktop:~$ beryl-manager
klmc@klmc-desktop:~$ Error: API mismatch: the NVIDIA kernel module has the version 1.0-8776, but
this client has the version 1.0-9629.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
Error: API mismatch: the NVIDIA kernel module has the version 1.0-8776, but
this client has the version 1.0-9629.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


i also don't have any way to close/maximize/minimize anything as that bar has disappeared.

thanks.

---

### Post by Kateikyoushi on 2006-11-10
Your packages do not match, therefore you have no acceleration fall back to metacity then you have title bar.

Check this thread for solutions how to correct the packages. [LINK]("http://ubuntuforums.org/showthread.php?t=263851")

```
sudo aptitude dist-upgrade
```
This did it for me but had to select the right packages manually.

---

### Post by kman14 on 2006-11-10
thanks, i'll check it out.

sorry - should have said that i'm very new to linux.
i don't know what metacity is.
also i'm in windows at the moment because when i re-started linux i lost graphical interface.

is their a simple way to do this from the command line? (i think that's what it's called.)

thanks

---

