---
title: "Erronious error runnning WOW under wine"
date: 2005-05-29
forum: Gaming &amp; Leisure
---

### Post by nivenmk1 on 2005-05-29
First off, I'm pretty new to the whole idea of non-MS operating systems and have tried almost every distro under the sun before setting on Ubuntu.

One of the largest hangups I have is that my primary gaming joy has no native support.

I've been fooling all day with getting World of Warcraft running under wine.

I've moved over 4 dll's and generally followed the tutorial found at [http://forums.gentoo.org/viewtopic-t-246098.html](http://forums.gentoo.org/viewtopic-t-246098.html).

Right now I'm having an error which reads as such :

> nivenmk1@ubuntu:~/.wine/fake_windows/Program Files/World of Warcraft$ wine WoW.exe -opengl
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:seh:EXC_RtlRaiseException call (from 0x5ed085a1) to unimplemented function KERNEL32.dll.IsWow64Process
wine: Unhandled exception (thread 0009), starting debugger...
err:seh:start_debugger Couldn't start debugger ("winedbg --debugmsg -all 8 104") (2)
Read the Wine Developers Guide on how to set up winedbg or another debugger
Wine exited with a successful status
[email]nivenmk1@ubuntu:~/.wine[/email]/fake_windows/Program Files/World of Warcraft$

 
Has anyone seen this before or know what exactly is the issue?

I'm running the latest release of WINE on a fresh install of Hoary.  I installed wine using Symbolic.

I have read about a CVS Tree Update for wine but am unsure of what it is or what it does.

Any help or comments are greatly appreciated.

---

### Post by equilibrium on 2005-05-30
I'm using cedega atm to run WoW and it seems to be very stable :)

I'm getting highs of 100fps in 1024x768 windowed mode  :smile: I think you can get a CVS version of cedega for free. Not sure if it's as good as the one you pay for tho  :neutral:

there is a good wine + wow howto on the gentoo forums: [http://forums.gentoo.org/viewtopic-t-246098.html](http://forums.gentoo.org/viewtopic-t-246098.html)

which has led to a wiki being made:
[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

some good info there.

---

### Post by Terrasque on 2005-05-30
I've gotten it to work almost perfectly under normal wine. 

You have to uninstall the apt wine package (in synaptic, search for wine and remove everything except winesetuptk package. Install the winesetuptk package if it's not installed already), and compile yourself the newest wine release (or you can use the [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) method. It will probably work too, and be much easier.)

Firstly first, remove the ~/.wine directory just to be sure there are no old stuff lying around (rm  -rf ~/.wine in console, or mv   ~/.wine ~/.wine-backup if you just want to move it to another folder). Then run winesetuptk, accept all the default values.

Then it's just to follow the gentoo guide, more or less. Get the dlls (from for example [http://www.dll-files.com/](http://www.dll-files.com/) ), grab windows mozilla and the moz activex control and install both, and run the WoW install.

After install, change the WoW shortcut on your desktop's run command to wine "bla bla wow.exe" -opengl
to fix sound chopping you can put nice -n 19 infront of wine, but beware, this can affect the game performance.

---

### Post by nivenmk1 on 2005-05-30
[QUOTE=Terrasque]I've gotten it to work almost perfectly under normal wine. 

You have to uninstall the apt wine package (in synaptic, search for wine and remove everything except winesetuptk package. Install the winesetuptk package if it's not installed already), and compile yourself the newest wine release (or you can use the [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) method. It will probably work too, and be much easier.)

Firstly first, remove the ~/.wine directory just to be sure there are no old stuff lying around (rm  -rf ~/.wine in console, or mv   ~/.wine ~/.wine-backup if you just want to move it to another folder). Then run winesetuptk, accept all the default values.

Then it's just to follow the gentoo guide, more or less. Get the dlls (from for example [http://www.dll-files.com/](http://www.dll-files.com/) ), grab windows mozilla and the moz activex control and install both, and run the WoW install.

After install, change the WoW shortcut on your desktop's run command to wine "bla bla wow.exe" -opengl
to fix sound chopping you can put nice -n 19 infront of wine, but beware, this can affect the game performance.[/QUOTE]
 > You have to uninstall the apt wine package (in synaptic, search for wine and remove everything except winesetuptk package. Install the winesetuptk package if it's not installed already), and compile yourself the newest wine release (or you can use the [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) method. It will probably work too, and be much easier.)

Originally I did the install as listed at the top part of the link above, adding the wine repositories to the sources file and pulling them through synaptic.  WoW fired up, dowloaded the patch and crashed, citing DLL issues.  I pulled the DLL's from my XP machine (now I find out XP dll's don't work so hot).  WoW patched itself without issue but wouldn't restart.

At the moment I'm using apt-get to pull the source, then recompile, then install.

I'll post back and let ya'll know how it goes.

Thanks for the link to a good source for DLL's.

---

