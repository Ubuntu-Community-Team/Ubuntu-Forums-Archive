---
title: "Getting X errors when trying to launch certain programs?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-10-31
Basically when I launch games I get errors about the X server.  I have been getting this on this computer since I instaled 5.04 about a month ago, and I just upgraded to 5.10 last night when I got a hub so this could be connected to the internet.  

It has onboard video, I mainly use this for programming but I enjoy a round of Doom II once in a while.  I get the following error when trying to launch Doom Legacy (the build in the repos):

> john@schwank1:~/legacy_142_linux$ ./llxdoom
 Apr 18 2004           Doom LEGACY v1.42 Birthday version              22:42:44
DOOM 2: Hell on Earth
Z_Init: Init zone memory allocation daemon.
system memory 219Mb free 3Mb
20 megabytes requested for Z_Init.
W_Init: Init WADfiles.
Added file /home/john/legacy_142_linux/doom2.wad (2919 lumps)
Added file /home/john/legacy_142_linux/legacy.dat (80 lumps)
===========================================================================
                     This program is Free Software!
             See the terms of the GNU General Public License
===========================================================================
I_StartupTimer...
I_StartupGraphics...
Using XFree86-VidModeExtension Version 2.2
Using MITSHM extension
X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x2a
  Serial number of failed request:  17
  Current serial number in output stream:  20

Eh... this is odd.  It has 1800 MHz and 512 MB ram.  I am pretty sure the onboard video is made by savage, thats what the default drivers were on 5.04 and it installed those drivers when I updated the distro.

Also, in IceWM, how do you change resolution?  Mine is using 1600 x 1200 but I would like to use something like 1024 x 768 on this computer.

Thanks.

---

