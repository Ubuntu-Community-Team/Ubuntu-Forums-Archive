---
title: "Problems with Beryl+XGL and ATi"
date: 2006-10-28
forum: Desktop Environments
---

### Post by BdON003 on 2006-10-28
Hello, on edgy, I had Beryl and Xgl working fine yesterday, but I messed something unrelated up and reformatted to start over.  On a very fresh instal, I used the tutorial [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")the first time and this time, with the fglrx driver.  This timeberyl doesn't load and typing is extremely slow. ```
bdon@BdON-PC:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)

```  Before I installed Beryl, but after fglrx, the Xlib:  extension line never showed up.  ```
bdon@BdON-PC:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
``` I added ```
Section "Extensions"
Option "Composite" Disable"
EndSection
```  Please someone help, it's really aggravating and it was working so much better than Dapper before

---

