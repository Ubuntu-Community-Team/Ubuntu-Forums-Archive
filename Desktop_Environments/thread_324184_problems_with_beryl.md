---
title: "problems with beryl"
date: 2006-12-23
forum: Desktop Environments
---

### Post by tzbishop on 2006-12-23
tzbishop@tzbishop-desktop:~$ beryl-manager
tzbishop@tzbishop-desktop:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kwin: Fatal IO error: client killed
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.

** (process:5256): WARNING **: get_setting_is_integrated not found in backend ini

** (process:5256): WARNING **: get_setting_is_read_only not found in backend ini

** (process:5256): WARNING **: get_setting_is_integrated not found in backend ini

** (process:5256): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
beryl: Failed to load slide: /usr/share/beryl/cubecaps.png
beryl: Failed to load slide: /usr/share/beryl/cubecaps.png
Reloading all options.
[SPLASH]: Could not load splash background image "/usr/share/beryl/splash_background.png" !
[SPLASH]: Could not load splash logo image "/usr/share/beryl/splash_logo.png" !


/usr/share/*.png - all those files actually exist. 
splash plugin is not initialized and I can't set a skydome image.
A lot of errors, etc as beryl-manger OUTPUT above shows..

How can I fix it?

---

### Post by flyboy on 2007-06-28
I had this problem and solved it by opening the Beryl Settings Manager, scrolled down to "Image Format", and clicked the Png and Svg options shown by clicking the dropdown triangle on the left. Straight away, the cubecaps picture loaded. I can't comment on your other problems, as I don't suffer the same here. 

I should add one rider - I had this problem on my desktop under gentoo with Beryl 0.1.4 - my Ubuntu laptop is not suitable for beryl!

Hope it works for you.
Rgds.,
Paul

---

