---
title: "Can not support a full graphical boot with 14.04 LTS"
date: 2015-04-23
forum: Desktop Environments
---

### Post by gbrunati on 2015-04-23
What could be the difference between a standard booting and to do it with recovery mode/resume sequence?


In my case, if I do it in the standard mode, the computer boots but freezes after a while when I'm working. 
If boot in recovery mode/resume sequence:

- if I change the X.Org X server-Nouveau driver to the NVIDIA one, the display crashes next reboot (even in recovery mode) so only reinstall option remains.
- the /etc/X11/xorg.conf file doesn't exist
- the display settings only show 1024x768 and 800x600 resolutions




----------------------
description:    Desktop Computer
- OS:    Ubuntu 14.04 LTS
- Memory 5.7 GB
- CPU:    AMD Phenom(tm) II X4 955 Processor
size:    800MHz
capacity:    3200MHz
width:    64 bits
- 00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2) (prog-if 00 [VGA controller])
- Graphics VESA: MCP61-mcp61-80
- OS type 64-bit
- Disk 247.6 GB


Help will be truly appreciated


G. Brunati

---

### Post by grahammechanical on 2015-04-23
I am not sure what it is you are asking about.

> What could be the difference between a standard booting and to do it with recovery mode/resume sequence?

Recovery Resume loads to the desktop with an open source video driver which for Nvidia adapters is called llvmpipe. Ubuntu uses llvmpipe in 3 ways.

1) If the video adapter is incapable of doing hardware accelerated 3D rendering and so cannot run Unity 3D, then llvmpipe is used to give a Unity 3D experience.
2) Recovery Resume
3) If there is some sort of conflict regarding proprietary video drivers.

I am not sure if any of this has to do with the system freezing. If you run this command you will get a list of available video drivers for your adapter. The command takes a little time to do it stuff.

```
ubuntu-drivers list
```

This command will install the current proprietary video driver

```
ubuntu-drivers autoinstall
```

Installing the proprietary driver through the terminal might throw up some errors that will help explain why the reboot "crashes," as you put it. I do not think that the xorg.conf file is used any more as Linux probes the monitor for its Extended Display Identification Data (EDID) as it loads.

Regards.

---

