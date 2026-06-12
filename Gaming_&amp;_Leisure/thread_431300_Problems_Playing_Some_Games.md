---
title: "Problems Playing Some Games"
date: 2007-05-02
forum: Gaming &amp; Leisure
---

### Post by Harkainos on 2007-05-02
I have Ubuntu 6.10 and Wine 0.9.36

I have installed WoW (Runs fine after I changed the resolution, etc)

I have Installed UT2k4 - I am running into problems with the mouse. It appears as though the auto mouse center *thing* isn't working properly and the desktop mouse actually travels to the edge of the window, causing the inability to turn after so far - I have read through the issue on winehq but there doesn't seem to be a resolution If you know one, feel free. I have Allow DirectX apps to stop mouse leaving their window checked and Allow the window manager to control the windows checked. My D3D support is set to hardware.

I have installed DoW: Dark Crusade - I can go through the graphic setup - works fine there, but when I click to actually run the program - nothing happens. I have it set to window version 98 and set the sound to ALSA Drivers - as per Winehq.

Any Ideas? Should I fall back to an earlier version of Wine? If so, how do I do that?

---

### Post by FoolsGold on 2007-05-03
> **Harkainos said:**
> I have Installed UT2k4 - I am running into problems with the mouse. It appears as though the auto mouse center *thing* isn't working properly and the desktop mouse actually travels to the edge of the window, causing the inability to turn after so far - I have read through the issue on winehq but there doesn't seem to be a resolution If you know one, feel free. I have Allow DirectX apps to stop mouse leaving their window checked and Allow the window manager to control the windows checked. My D3D support is set to hardware.
Why are you running UT2K4 in Wine when the LINUX BINARIES are already supplied with the game itself? :)

Install UT2K4 using the linux installer (located on one of the installation CDs), download the latest (linux) patch and apply it. That's my advice.

---

### Post by Iarwain ben-adar on 2007-05-03
Hi there,

What do you get when you run that game from the terminal?
(wine path_to_game/game.exe)


Iarwain

---

### Post by Harkainos on 2007-05-03
desktop:~$ wine /home/nick/Games/Dawn\ of\ War\ -\ Dark\ Crusade/DarkCrusade.exe
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0xb57aec
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:mixer:ALSA_MixerInit Should have found 1 channel for 'Master', but instead found 0
fixme:mixer:ALSA_MixerInit Should have found 1 channel for 'Capture', but instead found 2
nick@nick-desktop:~$ err:rundll32:main Unable to load L"Z:\\home\\nick\\dlltie.dll"


this is the terminal errors. I have no idea what they mean.

---

### Post by Harkainos on 2007-05-03
> **FoolsGold said:**
> Why are you running UT2K4 in Wine when the LINUX BINARIES are already supplied with the game itself? :)

Install UT2K4 using the linux installer (located on one of the installation CDs), download the latest (linux) patch and apply it. That's my advice.

Oddly enough. I only have experience installing through wine. I will try and figure out how to install the linux native. What file should I be looking for on the UT2k4 DVD?


EDIT:::::::::::

I found the linux-installer.sh file  - this is a shell script? How do I run it? Sorry for the noobish question, I have never done this before.


EDIT 2:::::::::::::::

Problem Resolved for UT2k4 Thanks

---

### Post by Iarwain ben-adar on 2007-05-03
> For some reason, the game will either not start, or the videos will stutter heavily unless you create a profile for the DarkCrusade.exe and set the emulated windows version to 98.

As found on [http://appdb.winehq.org/appview.php?iVersionId=6051&iTestingId=6959](http://appdb.winehq.org/appview.php?iVersionId=6051&iTestingId=6959)

Did you try those things they say?


Iarwain

---

### Post by Harkainos on 2007-05-03
yeah...

I can now run Dark Crusade. I followed the instructions on the Relic Site to 'Bypassing the DoW/WA installations. It no longer asks me for a cd-key, but provides an error:

Dawn of War appears to be not installed correctly. Please Reinstall.

Any known issues on this in Ubuntu 6.10 under wine 0.9.35?

Also, I installed it into the default installation folder. The ONLY way it will run is when I go to that location in terminal and wine DarkCrusade.exe - How do I make an Icon that does this for me? Or make my default Terminal right at the DC folder?

---

