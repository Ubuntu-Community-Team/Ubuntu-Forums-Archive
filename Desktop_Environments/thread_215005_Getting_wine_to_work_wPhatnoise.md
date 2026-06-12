---
title: "Getting wine to work w/Phatnoise"
date: 2006-07-13
forum: Desktop Environments
---

### Post by newlinux on 2006-07-13
I am trying to use wine for the first time. I installed PhatNoise Music Manger for wine, but when I try to run it:

```
~$ wine "C:\Program Files\PhatNoise Music Manager\PhatMan.exe"
err:module:map_image Could not map section .text, file probably truncated
err:module:import_dll Loading library WMVCore.DLL (which is needed by L"C:\\Program Files\\PhatNoise Music Manager\\PhatMan.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\PhatNoise Music Manager\\PhatMan.exe" failed, status c0000135
```

I went and put wmvcore.dll into .wine/drive_c/windows/system and added it in winecfg but I still get the same message. Is this just that this application won't run unde wine or am I doing something else wrong. Thanks!

---

### Post by newlinux on 2006-08-06
Anybody got any suggestions for something to try? Perhaps I should use something other than wine?

---

### Post by orb9220 on 2006-08-06
Before even trying you should go here and see if the app is listed.

[http://www.winehq.com/](http://www.winehq.com/)

---

### Post by newlinux on 2006-08-06
I did, and I know tha app isn't listed, however I know others have been able to get apps that aren't listed to work. I just wanted to know if there were any other things I could look into other than adding the appropriate DLL.

---

