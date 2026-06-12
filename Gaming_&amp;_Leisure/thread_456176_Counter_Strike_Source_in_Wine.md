---
title: "Counter Strike Source in Wine"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by immoral giant on 2007-05-27
I have successfully installed Steam through WINE and I copied over all of the SteamApps folder from a Windows installation.

I can run steam but performance in Counter Strike Source is around 9fps in game and the Stress Test only gets 31fps.

I get around 28,000 in glxgears (although I know it is not a benchmark;)) and around 160fps in UT2K4.

In Windows I get 250fps on CSS Stress Test with maximum settings.  

I have tried to install Nvidia drivers within Wine to see if it was something stupid like that but it won't install and I can't install DirectX within Wine either.

I have tried launching CSS with -dxlevel 70, -dxlevel 81 and -dxlevel 90.  They all look and perform the same.

EDIT: I am using Feisty Fawn 7.04.

---

### Post by ShadowFlar3 on 2007-05-27
For 1 thing, glxgears uses GL while HL2 and mods use directx, which makes the 2 hardly comparable in terms of benchmarking. But seems that your card drivers are working correctly anyway. I have no experiences with HL2 games so I can't really help you.

---

### Post by Linkerator on 2007-05-27
I have yet to try this myself, but it is supposed to work best with pixel shaders off.

---

### Post by immoral giant on 2007-05-27
Yes I have turned pixel shaders off.  Although it was the same with them on and off.

---

