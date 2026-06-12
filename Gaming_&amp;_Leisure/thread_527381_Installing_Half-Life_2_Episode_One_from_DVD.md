---
title: "Installing Half-Life 2 Episode One from DVD?"
date: 2007-08-16
forum: Gaming &amp; Leisure
---

### Post by quadomatic on 2007-08-16
I've finished installing Steam. Whenever i open Half-Life 2 Episode One setup.exe from the DVD and try to install the game, it gets this error:

Could not execute the external program
C:/program files/steam\Steam.exe

It seems like it can't find the steam.exe...

Is there any way I can get the game to install off of the DVD?

---

### Post by vivichrist on 2007-10-29
yep Me too (on my desktop i386) except this happens to me during install
installs fine on my Laptop (amd64) but laptop GPU is under powered

---

### Post by Crafty Kisses on 2007-10-29
> **quadomatic said:**
> I've finished installing Steam. Whenever i open Half-Life 2 Episode One setup.exe from the DVD and try to install the game, it gets this error:

Could not execute the external program
C:/program files/steam\Steam.exe

It seems like it can't find the steam.exe...

Is there any way I can get the game to install off of the DVD?

I know "The Orange Box" works, but not sure about HL2 Episode One.

---

### Post by cogadh on 2007-10-29
I haven't tried this myself, but doesn't the "Activate a product on Steam..." wizard allow you to install a game from within the Steam client? If not, you might be able to just copy the DVD contents into the correct folders within the Steam directory then run the activation wizard.

---

### Post by Crafty Kisses on 2007-10-29
> **cogadh said:**
> I haven't tried this myself, but doesn't the "Activate a product on Steam..." wizard allow you to install a game from within the Steam client? If not, you might be able to just copy the DVD contents into the correct folders within the Steam directory then run the activation wizard.
That might actually work.

---

### Post by vivichrist on 2007-10-29
Sorry my stupid mistake ... must configure Drives in wine before attempting to install anything ... bla

---

### Post by Crafty Kisses on 2007-10-29
> **vivichrist said:**
> Sorry my stupid mistake ... must configure Drives in wine before attempting to install anything ... bla

Update us after you do that.

---

### Post by vivichrist on 2007-10-29
Actually what does:
> 
Steam.exe (main exception): Win32 StructuredException at 0D80EE23 : Attempt to read from virtual address 88 without appropriate access rights.

mean ?

---

### Post by Crafty Kisses on 2007-10-29
> **vivichrist said:**
> Actually what does:


mean ?

Not sure, sounds like you don't have root.

---

### Post by cogadh on 2007-10-29
DO NOT RUN WINE WITH A ROOT USER OR WITH SUDO!!

Wine is beta software and allowing it unrestricted access to the system through the use of administrator privileges can lead to very bad things. In the best case scenario, anything you install with Wine will have root only permissions and a normal user won't be able to use it. In a worst case scenario, you could hose your whole system.

How are you running the install, i.e. what are you entering in the terminal?

---

### Post by vivichrist on 2007-10-29
Ok tried installing steam through wine doors and
... its stuck.
gay

I didn't use the console I just used nautilus double click

---

### Post by Crafty Kisses on 2007-10-29
> **vivichrist said:**
> Ok tried installing steam through wine doors and
... its stuck.
gay

Hmmm, that sucks, do you know if you have root access.

---

### Post by vivichrist on 2007-10-29
no actually on restarting wine-doors it installs steam but when I Setup.exe on the orange box DVD1 I just get the same error with different address info...
and yes (me is Admin)

---

### Post by Crafty Kisses on 2007-10-29
> **vivichrist said:**
> no actually on restarting wine-doors it installs steam but when I Setup.exe on the orange box DVD1 I just get the same error with different address info...

Hmmm, weird.

---

### Post by cogadh on 2007-10-29
I wrote a how-to for installing Team Fortress 2 from the Orange box, but it should also work for anything that came with it. Check here:
[http://gaming.gwos.org/doku.php/wine:team_fortress_2](http://gaming.gwos.org/doku.php/wine:team_fortress_2)

---

### Post by Crafty Kisses on 2007-10-29
> **cogadh said:**
> I wrote a how-to for installing Team Fortress 2 from the Orange box, but it should also work for anything that came with it. Check here:
[http://gaming.gwos.org/doku.php/wine:team_fortress_2](http://gaming.gwos.org/doku.php/wine:team_fortress_2)

Oh, thanks!

---

### Post by vivichrist on 2007-11-03
so you reckon install off of Harddrive rather than DVD...

i'l try it.

I have a bunch of other interesting problems in gutsy that could be related. the drive mapping is buggered and nvidia-settings say I'm not using the nvidia driver when I clearly am.

---

### Post by cogadh on 2007-11-03
> **vivichrist said:**
> ...the drive mapping is buggered and nvidia-settings say I'm not using the nvidia driver when I clearly am.
Um, this concerns me. What exactly is wrong with your drive mapping and how are you certain that you are clearly using the "nvidia" driver when the Nvidia settings app says you aren't? To me, that would be a clear indication that you are not actually using the Nvidia driver.

---

### Post by vivichrist on 2007-11-04
OK when I boot I have to change the line (hd0.9) to (hd0.8) have tried update-grub, grub-install and editing the menu.list then the later.
but just changes it back. where does grub get it info?

opengl works and quite fast. xorg.0.log tells me it suceeded

---

### Post by cogadh on 2007-11-04
I'll leave the drive issue for someone more knowledgeable in such things than I. Wouldn't want to give you the wrong advice based on my limited experience with that. Never really had a drive mapping problem myself, so I really haven't looked into it. 

The generic "nv" driver has some limited OpenGL support and 3D rendering ability, so the fact that OpenGL is functional doesn't really say anything. What exactly does the xorg.0.log file say?

---

### Post by reagentz on 2007-11-04
I just installed Steam through WINE-Doors last night with no real issues. Launched Steam signed in, setup which games I wanted Steam to install and went to bed. I let Steam install the games back on the PC instead of using my CDs/DVDs. The real test will be when I get The Orange Box this weekend for TF2 and Portal.

---

### Post by vivichrist on 2007-11-06
ahhh found the problem wine and wine-doors were installing in two different places, I set wine to /home/bla/Desktop/C/ and wine-doors is  /home/bla/.wine/c_drive/ (I didn't think it would be different, assumed it would use wines settings) so two c:\ drives and two installs of steam (possibly three with other changes of C:\ mount point, wine changed itself back to default C:\ mounting place). so deleted all (files in /home/bla/Desktop/C/ & /home/bla/.wine/c_drive/) and started fresh making sure to keep with the default. though still got that error when installing off dvd. but copy entire dvd contents to harddrive (/home/bla...), with preliminary install of fonts and gecko though wine-doors and hay presto:guitar:

---

