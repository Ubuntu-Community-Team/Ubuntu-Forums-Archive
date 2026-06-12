---
title: "Urban Terror resolution crash"
date: 2008-04-05
forum: Gaming &amp; Leisure
---

### Post by Trinidado on 2008-04-05
After switching my Urban Terror resolution to 1600x1200, I got this message: ```
----- FS_Startup -----
Going through search path...

----------------------
8032 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 9: 1600 1200
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x75
  Serial number of failed request:  137
  Current serial number in output stream:  139
```

Now it crashes every time I try to play it. I would appreciate any advise on the subject.

Thanks,
Trinidad

---

### Post by Rhubarb on 2008-04-05
There's a configuration file that you can edit that should fix this up.
Going off memory here, I think it should be in your UrT/ base/config.cfg or in ~/.UrT or something similar.

You can delete this file (if you want UrT to be reset back to defaults), or you may edit it manually to fix up the resolution issues.

I can't be of much more help as I don't currently have UrT installed here.

---

