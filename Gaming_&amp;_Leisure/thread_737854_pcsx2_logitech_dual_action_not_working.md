---
title: "pcsx2 logitech dual action not working"
date: 2008-03-28
forum: Gaming &amp; Leisure
---

### Post by taehC on 2008-03-28
When i try to configure the controls i cant enter any keys, can anyone help?  When i go into configure, i get a message saying that NPPTools.dll is missing, does that matter?

---

### Post by acoustibop on 2008-03-28
Yes.  Sounds like you're trying to use a Windows plugin.  Linux doesn't have .dll files.

---

### Post by taehC on 2008-03-28
right now i am in windows.
but i should try it in ubuntu.
why am i even trying this in windows?

---

### Post by acoustibop on 2008-03-28
And why are you asking for help for a Windows application in a Linux forum, taehC?

I used to use Project64 when I used Windows; AIR it seemed to work pretty well; I can't remember any controller problems with it.

There isn't a Project64 version for Linux; there is another Nintendo 64 emulator called Mupen64 that is primarily a Linux emulator, although AIR it has a Windows version too.

---

### Post by equity on 2008-06-21
> **acoustibop said:**
> And why are you asking for help for a Windows application in a Linux forum, taehC?

I used to use Project64 when I used Windows; AIR it seemed to work pretty well; I can't remember any controller problems with it.

There isn't a Project64 version for Linux; there is another Nintendo 64 emulator called Mupen64 that is primarily a Linux emulator, although AIR it has a Windows version too.

^^Lol? Sound a bit off-topic. taehC spoke about PS2-emulatorr issues and you advice him N64-Emulators for Windows. Btw Project64 runs perfectly under Ubuntu using wine (since v1.0rc3). And with it my P880 controller from Saitek, that does not work with PCSX2, although it is a native Linux application... I am looking for an alternative for ZeroPAD, because it only recognizes my keyboard.

---

### Post by dfreer on 2008-06-21
> **equity said:**
> ^^Lol? Sound a bit off-topic. taehC spoke about PS2-emulatorr issues and you advice him N64-Emulators for Windows. Btw Project64 runs perfectly under Ubuntu using wine (since v1.0rc3). And with it my P880 controller from Saitek, that does not work with PCSX2, although it is a native Linux application... I am looking for an alternative for ZeroPAD, because it only recognizes my keyboard.

Probably just a brain fart, acoustibop spends a lot of time dealing with emulator related issues :D

EDIT: For what it is worth, I just tried my logitech dual action with PCSX2 0.9.4 in windows, and using the default controller plugin SSSPSX PAD Plugin Pressure Mod 1.6.0 I was able to configure my controller without any issues. I used the compressed *.7z download, not the installer if that makes any difference.

Maybe you plugged in the controller after you launched PCSX2, which results in the program not seeing the joystick? I guess that doesn't really explain the missing .dll file though...

---

### Post by acoustibop on 2008-06-21
Think it was a brain fart - 28th March was a long time ago, though - nearly 3 months!

---

### Post by equity on 2008-06-22
> **dfreer said:**
> Probably just a brain fart, acoustibop spends a lot of time dealing with emulator related issues :D

EDIT: For what it is worth, I just tried my logitech dual action with PCSX2 0.9.4 in windows, and using the default controller plugin SSSPSX PAD Plugin Pressure Mod 1.6.0 I was able to configure my controller without any issues. I used the compressed *.7z download, not the installer if that makes any difference.

Maybe you plugged in the controller after you launched PCSX2, which results in the program not seeing the joystick? I guess that doesn't really explain the missing .dll file though...

When I use Project64 with wine, my controller gets instally recognized after plugged in. PCSX2 does not recognize my controller even if I reboot my whole system. Looks like the plugin ZeroPAD does not like my controller. I didn't yet find any alternative for ZeroPAD.

I also already tried the windows version of PCSX2, but neither the install version, nor the 7zipped version works with wine. When executed the program claims about missing real time virtual memory access or the like.

Edit: Found out that my trouble in caused through incompatibility with the ZeroPAD version 0.1.0. Gamepads like my Saitek P880 are supported from 0.2.0.
But the point is you only get the source and I have got trouble compiling it. I do not know why I am not able to compile it, but compiling programs like IRC clients is much easier to me.

---

