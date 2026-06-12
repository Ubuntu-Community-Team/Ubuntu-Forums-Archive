---
title: "beryl and nvidia-legacy"
date: 2006-11-05
forum: Desktop Environments
---

### Post by oldforce on 2006-11-05
i have nvidia 32mb tnt2 m64 pro but i cannot run beryl on edgy...
i think my card does not support xgl..
here is the output;

hiozturk@hiozturk-desktop:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

does nvidia-legacy driver support xgl?

---

### Post by NiklasV on 2006-11-05
You either don't have GLX enabled or the driver doesn't support it. (GLX is the OpenGL extension for X, which Beryl requires)
If you can't find the following line in the module section your xorg.conf, add it.
Load           "glx"

And if you have these lines in the module section, remove them.
Load  "dri"
Load  "GLcore"

Also make sure the Driver is set to "nvidia", not "nv" in the Device section.
You have to restart X for this to have any effect. (Ctrl-Alt-Backspace)

If the xorg.conf looks like that already, try installing the legacy driver directly from the Nvidia website: [http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html)

---

