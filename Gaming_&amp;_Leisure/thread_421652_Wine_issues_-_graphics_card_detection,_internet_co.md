---
title: "Wine issues - graphics card detection, internet connection"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by cogadh on 2007-04-24
Since upgrading to Feisty, I've been trying to use Wine to play some of my Windows games. At first I was having so many problems that none of the games would launch or sometimes even install. I have decided to focus on a single game for now and try to work through all the problems with it until it works as well as possible. Hopefully that will resolve some of the problems I have with other games.

The game I am working with is Star Wars Knights of the Old Republic. It is listed in Wine's AppDB as working and has been rated gold. I have the game at a point where it is functional, but getting there has brought two major problems to light:

1. Apparently, Wine does not properly detect my graphics card, GeForce FX 5200 256 MB. I am using the 9755 driver from the Ubuntu reps and  direct rendering is functional. Native 3D games work perfectly as does Beryl. When I first tried to  configure the game, it correctly detected all of my system specs, including OpenGL support, but did not report any info on my graphics card and indicated it only had 64 MB of memory. I added a registry entry in Wine to correct the memory discrepancy, but the card itself is still not detected. How can I get Wine to correctly detect the card?

2. When I try to use the game's update feature, it reports there is no network connectivity after sending a failed ping to the update server. I believe this problem is due to ICMP requiring root access in Linux. Networking is not really my thing with Linux, so how do I change the permissions on ICMP to allow a normal user access to it?

System Specs:
Dual-boot XP Home/Ubuntu 7.04
P4 2.0 GHz
1 GB RAM
GeForce FX 5200 256 MB
SB Audigy LS
Samsung Lightscribe DVD-RW
Wine 0.9.35 (latest stable)

---

### Post by lordhebe on 2007-04-24
> **cogadh said:**
> 1. Apparently, Wine does not properly detect my graphics card, GeForce FX 5200 256 MB. I am using the 9755 driver from the Ubuntu reps and  direct rendering is functional. Native 3D games work perfectly as does Beryl. When I first tried to  configure the game, it correctly detected all of my system specs, including OpenGL support, but did not report any info on my graphics card and indicated it only had 64 MB of memory. I added a registry entry in Wine to correct the memory discrepancy, but the card itself is still not detected. How can I get Wine to correctly detect the card?

It's not that it doesn't properly detect you graphics card, it's that it disguises it as generic in order to not confuse games into activating unsupported features by default.

---

### Post by cogadh on 2007-04-24
So when I see this in the terminal:
```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1809b8) : stub, simulating 256MB for now, returning 256MB left
```
I shouldn't worry? I don't speak Wine, but that looks to me like Wine can't properly identify my graphics card specs and is only getting the memory right because I forced it to with a registry edit.

---

### Post by cogadh on 2007-04-25
(bump)
No help for the ICMP question?

---

### Post by eternalwolfman on 2007-04-29
i feel your pain! i havent been able to get any games to run under wine, or cedega for that matter. i have a geforce go 7400, and ive tried even installing native games such as ut , and no cigar! i hope someone can help us.

-greg.

---

### Post by StarSoul on 2009-02-02
i'm currently playing DoW Soulstorm on wine 1.0.1 over lan with no problems.

-the ICMP; i just uninstalled Firestarter, which might not be a solution, but it works.

---

