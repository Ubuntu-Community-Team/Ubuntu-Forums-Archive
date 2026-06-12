---
title: "Issues with Neverhood on Wine"
date: 2007-02-20
forum: Gaming &amp; Leisure
---

### Post by tylersticka on 2007-02-20
Hiya!

I'm attempting to get the classic point-and-click adventure game The Neverhood. I found tutorials [here]("http://frankscorner.org/index.php?p=neverhood") and [here]("http://neverhood.etomite.sk/svk_linux.htm").

I almost have it working... the problem is that I can't seem to configure the game to run in windowed mode.

I'm attempting to get to this screen of winecfg as shown in the second tutorial link:

[IMG]http://neverhood.etomite.sk/imgs/wine_tuto/003.png[/IMG]

But my winecfg, when selecting NHC.exe as the specific application, the option of running items in a virtual desktop is grayed out and not able to be selected.

When I attempt to launch the application anyway, the app starts fine until the Xfce window manager updates and then I'm left with a tiny box view of the my desktop until I restart.

Anyone know a way to get that checkbox to stop being grayed out? Thank you!

---

### Post by tylersticka on 2007-02-20
Update: So if I change the default settings to emulate a virtual desktop, the same problem happens... the program launches successfully, but upon exiting everything is confined to a 640 x 480 box in the middle of the screen.

Does anyone know anything Ubuntu/Xubuntu/Edgy-specific to keep games from doing this?

---

### Post by churchyard on 2007-04-01
[IMG]http://wiki.ubuntu.cz/The_Neverhood?action=AttachFile&do=get&target=003_winecfg_graphics.png[/IMG]
My Xubuntu screenshot...

I cannot emulate virtual desktop... but I can use this:```
wine explorer /desktop=ref,800x600 "E:\Neverhood\SETUP\NHC.EXE"
```As you can see the most important part is **explorer /desktop=ref,800x600**

---

### Post by tylersticka on 2007-04-01
> **churchyard said:**
> I cannot emulate virtual desktop... but I can use this:```
wine explorer /desktop=ref,800x600 "E:\Neverhood\SETUP\NHC.EXE"
```As you can see the most important part is **explorer /desktop=ref,800x600**

Success! Thanks so much, it works exactly as I wanted now.

---

### Post by churchyard on 2007-04-02
You are wellcome... you can change resolution to 640x480...

---

### Post by tylersticka on 2007-04-02
After the virtual desktop is launched and NHC.exe begins running inside of it, it automatically resizes the window to 640 x 480. But I will change it just to avoid any unnecessary steps.

---

### Post by churchyard on 2007-04-02
Also if you want hide your XFCE's mouse cursor, run winecfg (after running Neverhood) and close it. Next double click on Neverhood icon in left-down corner of emulated window.

---

