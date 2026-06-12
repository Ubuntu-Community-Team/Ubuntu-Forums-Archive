---
title: "Savage won't run"
date: 2006-10-10
forum: Gaming &amp; Leisure
---

### Post by Pichu0102 on 2006-10-10
When I try to run Savage, it fails and exits.
From the debug log, it read this...

---------------------------------------------------------
Driver capabilities
---------------------------------------------------------
- This driver will support software mode only.
It does not properly support 3D sound hardware.
---------------------------------------------------------
Hardware 3D channels : 0
Using 192 total channels
Init: Error initializing output device.
attempt to compress texture failed for textures/core/alphagrad.tga
BSDSock_Init
Local IP #1: 127.0.0.1
Local IP #2: 127.0.1.1
Port 32902 opened
Port 32903 opened
Savage on Linux - Core build Sep 7 2006 16:16:12
Initializing game...
* Initializing effects...
* Initializing states...
* Initializing team upgrades...
* Initializing game parameters...
* Initializing Objects...
Unknown command: 'textbox'
attempt to compress texture failed for /gui/standard/darkbrown.tga
Invalid start/stop/step combination
attempt to compress texture failed for /textures/loading/nfm_mapoverlay.tga
attempt to compress texture failed for /textures/loading/1_nl_loadingstar.tga
attempt to compress texture failed for /textures/loading/nfm_auth.tga
attempt to compress texture failed for /textures/loading/nfm_auth_ok.tga
attempt to compress texture failed for /textures/loading/nfm_connect.tga
attempt to compress texture failed for /textures/loading/nfm_connect_ok.tga
attempt to compress texture failed for /textures/loading/nfm_waiting.tga
attempt to compress texture failed for /textures/loading/nfm_waiting_ok.tga
attempt to compress texture failed for /textures/loading/nfm_loading.tga
attempt to compress texture failed for /textures/loading/nfm_loading_ok.tga
Signal SIGFPE received.

Graphics card is:
Intel 82852/855GM Integrated Graphics Device

Is there any hope for me?

---

### Post by haxer on 2006-10-10
Try to install drivers? Or do you already got it?:-k

---

### Post by Pichu0102 on 2006-10-10
> **haxer said:**
> Try to install drivers? Or do you already got it?:-k

Drivers? Like, which ones, and how?
I haven't changed those yet...

---

### Post by haxer on 2006-10-10
you got an nvidia card so just install automatix :) and then select your nvidia drivers and it will work just fine :) [http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

---

### Post by jISh on 2006-10-10
```
sudo apt-get install nvidia-glx
```
Don't need bothersome things like Automatix, better to do it yourself it's just as easy.

---

