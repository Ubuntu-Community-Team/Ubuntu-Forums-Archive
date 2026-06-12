---
title: "I can't run Halo Infinite on Steam"
date: 2024-03-03
forum: Gaming &amp; Leisure
---

### Post by tuxsoldier1986 on 2024-03-03
Hi everybody,

So i got my nvidia drivers 64bit installed, and i'm pretty sure i've the i386 ones also installed. But for some reason it's not launching. Any hints on what to do or where to start?:(
I have tried all recent Proton versions
3060Ti
latest stable drivers installed through ubuntu APT
```

NVRM version: NVIDIA UNIX x86_64 Kernel Module  535.161.07  Sat Feb 17 22:55:48 UTC 2024
GCC version:  gcc version 12.3.0 (Ubuntu 12.3.0-1ubuntu1~22.04) 
```
> 
dpkg -l | grep libnvidia-gl
ii  libnvidia-gl-535:amd64                     535.161.07-0ubuntu0.22.04.1                amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-535:i386                      535.161.07-0ubuntu0.22.04.1                i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD






when i launch **Halo Infinite** i get this 

```
Testing for explicit PulseAudio choice...
...and PulseAudio has been explicitly chosen, so using it.
steam.sh[110936]: Running Steam on ubuntu 22.04 64-bit
steam.sh[110936]: STEAM_RUNTIME is enabled automatically
Found NVIDIA version: 535.161.07
Need NVIDIA 32-bit: False
setup.sh[111016]: Steam runtime environment up-to-date!
steam.sh[110936]: Steam client's requirements are satisfied
tid(111059) burning pthread_key_t == 0 so we never use it
```

But weirdly, i can run other games like The Long Dark or Return to Castle Wolfenstein with Steam.

Could it be a problem with Easy Anti-Cheat ?
 should i try Nvidia's official drivers ?

---

### Post by tuxsoldier1986 on 2024-03-05
Got it to work by using flatpak steam app instead. I guess something is missing in the ubuntu version.

---

### Post by keshara283 on 2024-05-11
> **tuxsoldier1986 said:**
> Got it to work by using flatpak steam app instead. I guess something is missing in the ubuntu version.

It has been my understanding that the general advice is to avoid the Snap version of Steam, and to prefer the .deb version or the Flatpak if you prefer. 

Since recently switching to Ubuntu 24.04 on my main Desktop, I originally tried the Snap but that just caused headaches, with the .deb official version I found I was getting weird micro-stutters on my machine, and I've since moved to the Flatpak version without issues.

---

### Post by basednev on 2024-06-25
> **keshara283 said:**
> It has been my understanding that the general advice is to avoid the Snap version of Steam, and to prefer the .deb version or the Flatpak if you prefer. 

Since recently switching to Ubuntu 24.04 on my main Desktop, I originally tried the Snap but that just caused headaches, with the .deb official version I found I was getting weird micro-stutters on my machine, and I've since moved to the Flatpak version without issues.

This right here^ although there are a few reasons not to use Flatpak that I have encountered. For instance: Installing GTA 5 with flatpak version of steam causes the rockstar launcher not to work properly, or HellDivers 2's anti cheat not to load. Using the .deb directly from steam has worked absolutely perfect for me, but might not be the case for a few others. I assume this has to do with the nature of flatpaks being containerized and lacking permissions. Could be completely wrong.

---

