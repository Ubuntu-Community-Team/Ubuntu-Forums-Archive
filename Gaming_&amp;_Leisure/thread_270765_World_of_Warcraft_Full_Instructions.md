---
title: "World of Warcraft Full Instructions"
date: 2006-10-03
forum: Gaming &amp; Leisure
---

### Post by DrkMyst on 2006-10-03
Hello to every one

after getting World of Warcraft to work on my Linux 
box i decided to make a how to this how to assumes the following

1) you know jack about Linux
2) you have a fresh install of Ubuntu 6.06 LTS with all the updates done
3) you are using an Nvidia Card

what you will have at the end

a perfect working World of Warcraft
the in-game GPS otherwise known as Cosmos

Now before i drone on a big thanks to

kidcharles for his / her info on WOW with Wine
url = [http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)

Unknown for his her there info on Nvidia
url = [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

SKLP for his / her info on WOW with Wine
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

without them i would not even have WOW on Linux :|

the main reason why i did this is because i fell into a few snags not covered by the tutorials and also it is every thing from the grounds up

this is a long tutorial so i have posted the file so you can read this off line

---

### Post by Laines on 2006-12-07
I have not done this yet, but I have been messing with this installation for days, I am going to undo everything, and start over with your walkthrough. I will post my update tonight! Thanks for the Dummies walkthrough, looks like I can follow this, cause like you assumed, I know nothing of Linux, but I love the Windows in Now Extinct! I will never go back to windows if I can get this and my wireless card to work!

---

### Post by Josh1 on 2006-12-07
I got WoW to work just by wine'ing everything then running it in opengl mode lol.

---

### Post by Sammi on 2006-12-07
DrkMyst's howto is already outdated. But he does link to a howto, which I have tried to update: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Be sure to try it first ;)

---

### Post by mitchbones on 2006-12-07
Thanks Sammi (and DarkMyst), I am going to try and install WoW tommorow and this clears up alot.

---

### Post by dasuberdog on 2006-12-07
Im running edgy with wine 9.026 and nvidia driver etc...

I have done tweak #1 in this thread only no patches to wine.  I have a patched wow from a windows machine.  

I am getting this message in the terminal.  Let me know if you have any ideas.....

scribble@Scribble:/media/hda5/world of warcraft$ wine wow.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d720000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d720000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f34c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  477
  Current serial number in output stream:  477


Thanks

---

### Post by dasuberdog on 2006-12-07
Hmm maybe something is going wrong with my nvidia drivers....

my glxgears score is only averaging like 320 fps.....is that sufficient???

---

### Post by dasuberdog on 2006-12-08
FYI  I downloaded automatix2 instead of easyubuntu.  I installed nvidia drivers and wine with automatix2 and now Wow works perfect.  Also my glxgears score is in the 6000 range.  No patches to wine also.

---

### Post by Sammi on 2006-12-08
I'm no expert, but my guess is that you didn't have the official proprietary Nvidia drivers installed. The open source ones don't do 3d.

---

