---
title: "need help installing fallout2"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by hempa on 2007-04-23
hello! i have just installed fallout and i want to install fallout2.. My problem is this, when i installed fallout i had two setup.exe files to choose from. one was just called setup.exe and the other was called setupd.exe the d meaning dos installation. when i ran the ordinary setup i could not start the game but when i installed with the setupd.exe file i could start the game. but the fallout2 cd does not have a setupd.exe file just a ordinary setup.exe file and wehn i install with that file i cant start the game. how can i solve this problem.. i have feisty and i am using wine if that can be of any help.

---

### Post by lakersforce on 2007-04-23
use winecfg to setup the correct version of Windows to emulate. If my memory serves me right fallout2 will not run on anything higher than win98.

---

### Post by hempa on 2007-04-23
yes i know. i took me some time to realize that i could only use win95 or win98 when i installed fallout1. but that is not the problem. the problem is that after i have run setup and the game is in dosdevices->c: in wine it still wont start. but fallout1 that is also installed in the same folder in wine works perfect. and i think it is because i had a file called setupd.exe on that cd wich was a dos setup file. but i dont have a file like that on my fallout2 cd only the setup.exe that doesent seem to work

---

### Post by lakersforce on 2007-04-23
What is the command-line output?

---

### Post by cho on 2007-04-23
I played fallout 2 on XP for a while, I'm gonna install it on my feisty and see what happens.

Edit:

It installed fine (although I'm not sure if thats your problem), but there is no sound. I did the medium installation I think. Help would be appriciated.

Thanks

---

### Post by hempa on 2007-04-24
i can also install fallout2 but i cant start the game it just says could not find/load text fonts. weird.
how did you install?

---

### Post by hempa on 2007-04-24
> **lakersforce said:**
> What is the command-line output?

what is the command line (i am a retard)

---

### Post by lakersforce on 2007-04-24
> **hempa said:**
> what is the command line?

The output of your terminal.

Programs -> Accessories -> terminal

you can list what is in your directory with the command: ls

navigate to your cdrom (proberly: cd /media/cdrom0) and run the setup-file (proberly: wine setup.exe) and show us what it says.

if you managed to install your game try running it and show us what it says.

navigate to your folder where you installed the game: cd .wine/drive_c/ should get your to the standard windows file structure. You will proberly recognize it. Find your fallout directory and run the appropiate *.exe file, proberly: wine fallout2.exe and show us the output.

---

### Post by hempa on 2007-04-25
> **lakersforce said:**
> The output of your terminal.

Programs -> Accessories -> terminal

you can list what is in your directory with the command: ls

navigate to your cdrom (proberly: cd /media/cdrom0) and run the setup-file (proberly: wine setup.exe) and show us what it says.

if you managed to install your game try running it and show us what it says.

navigate to your folder where you installed the game: cd .wine/drive_c/ should get your to the standard windows file structure. You will proberly recognize it. Find your fallout directory and run the appropiate *.exe file, proberly: wine fallout2.exe and show us the output.

Ok. this is what i got from the terminal when i ran the setup.exe for fallout2

armcandy@armcandy-desktop:~$ '/media/FOT_1/Fallout 2/SETUP.EXE' 
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x172e88) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x172540)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x172540)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
armcandy@armcandy-desktop:~$

---

### Post by hempa on 2007-04-25
whoops! for some reason some smileys got in there. smiley nr1 is an 8, smiley nr2 is an x, and smiley nr3 is an 8.

---

### Post by jmervyn on 2007-05-21
Just in case, I found a simple fix for the sound problem - you're probably not configured properly for Fallout 2.  Under Wine configuration, make sure you're using the ALSA driver.

Now if only I could get the keyboard working... :p

---

