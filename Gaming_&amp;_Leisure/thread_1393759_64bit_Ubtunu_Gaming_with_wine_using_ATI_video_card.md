---
title: "64bit Ubtunu Gaming with wine using ATI video card"
date: 2010-01-29
forum: Gaming &amp; Leisure
---

### Post by Sensistar on 2010-01-29
Hello all, I have spent countless hours searching for an answer to my problem and have found and tried many solutions that worked for some that are not working for me(None of which were exactly my problem). A brief description of my problem is that drivers installed fine, show that they are installed fine, games won't open under wine.

First off, here is my system specs:
AMD Phenom Quad-core X4 3.0ghz
8GB DDR2 1066 Memory
ATI Radeon 4870 1GB Video Card
Ubuntu 9.10 Karmic Desktop x86_64 
kernel version: 2.6.31-17-generic

This is a fresh install of Ubuntu 9.10 Desktop 64bit. I ran the update manager to update all packages. Then i removed the default fglrx drivers following ATI's installation instructions, then installed the newest ATI 64bit drivers for my 4870 card.

ati-driver-installer-10-1-x86.x86_64.run from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

The installation appeared to install fine. I can access the ATI control panel, change any settings I want. I have 2 monitors, one at 1680x1050 and one at 1280x1024, both are displaying fine.

```
c0le@c0le-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series 
OpenGL version string: 3.2.9252 Compatibility Profile Context
```

fglrxinfo even shows they are installed.

I installed the newest wine1.2 and i've installed the newest playonlinux 3.7.2. No game will open using wine or under playonlinux. I've tried new and old games; World of Warcraft, original Starcraft, FarCry, Warcraft III, Diablo II. 

They all give a version of this error with different numbers.

```
c0le@c0le-pc:/media/Games/Games/Starcraft$ wine StarCraft.exe
fixme:advapi:SetSecurityInfo stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1088
  Current serial number in output stream:  1088
```

That is running off a mounted NTFS partition. I have copied over games and tried running them off a linux partition, same error.

I'm guessing since i'm on a 64bit system with 64bit drivers running 32bit wine to run 32bit games, this is my problem.

According to the ATI website where i got the drivers (link above) it says: 
32-Bit packages must be installed for 64-Bit Linux drivers to install or work. 

Is there some 32bit packages/libraries i need to install to make this work?

Let me know if I should give any more information or similar error codes from other games.

---

### Post by NightwishFan on 2010-01-30
The x86_64 arch is compatible with 32-bit userspace. You can run 32-bit Wine applications fine from 64-bit Ubuntu.

You say "copy". Did you install the games normally through Wine? You cannot (at the least should not) run games installed in Windows on Wine. Install them normally on Ubuntu.

Do you have 3d rendering? Do Linux games such as Nexuiz work?

---

