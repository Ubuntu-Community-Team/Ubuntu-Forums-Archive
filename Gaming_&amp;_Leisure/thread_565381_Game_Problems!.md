---
title: "Game Problems!"
date: 2007-10-02
forum: Gaming &amp; Leisure
---

### Post by Pulser on 2007-10-02
Hello, I've downloaded a game recently called Gunz - gunz.ijji.com, I've downloaded the latest one and installed it to /home/shane/.wine/drive_c/Gunz/ - After doing so I tried to run the "Launcher" and the actual game by using wine but all I get is errors such as:

```
shane@Shane:~/Desktop/Gunz$ wine GunzLauncher.exe
fixme:shdocvw:WebBrowser_QueryInterface (0x171080)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x33d778) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x171080)->(0x33d744)
fixme:shdocvw:OleControl_FreezeEvents (0x171080)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x171080)->(0)
shane@Shane:~/Desktop/Gunz$

```

Is it something to do with my browser? (thats the error from loading the GunzLauncher.exe)
Thanks!

EDIT: I made Internet Explorer as my default browser because ijji only allows people to play games with IE, so after doing that I tried wine again and got the following error:

```
shane@Shane:~/Desktop/Gunz$ wine GunzLanucher.exe
wine: could not load L"c:\\windows\\system32\\GunzLanucher.exe": Module not found
```

It must have something to do with the way I installed gunz because it's looking in C:\ drive

EDIT2: Ok I've added the gunz folder to the /windows/system/ folder in .wine - And it does the same thing as 

```
shane@Shane:~/Desktop/Gunz$ wine GunzLauncher.exe
fixme:shdocvw:WebBrowser_QueryInterface (0x171080)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x33d778) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x171080)->(0x33d744)
fixme:shdocvw:OleControl_FreezeEvents (0x171080)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x171080)->(0)
shane@Shane:~/Desktop/Gunz$

```

---

### Post by TidusBlade on 2007-10-02
I don't really remember but I think Gunz uses GameGuard, correct me if it doesn't but if it does then it wont run properly because I heard Wine and such programs don't run Gameguard very well leading to games like Maple Story and others that use Gameguard to fail :(

---

