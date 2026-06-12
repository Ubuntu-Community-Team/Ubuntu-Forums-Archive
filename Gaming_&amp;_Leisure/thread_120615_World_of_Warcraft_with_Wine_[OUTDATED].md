---
title: "World of Warcraft with Wine [OUTDATED]"
date: 2006-01-22
forum: Gaming &amp; Leisure
---

### Post by kidcharles on 2006-01-22
I had a hard time getting WoW to work in wine using the information I found on this forum and others. After being pointed to this howto ([http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft)) by a helpful individual named 'vanilla' on the winehq irc channel, I had great success. I thought I would make a post on the Ubuntu forums showing what worked for me. I borrowed heavily from that howto, but added some things I did to deal with workspace switching better, and some customizations I have done.

DOWNLOADS:

If you have already installed wine from the repositories, you will want to do a "complete removal" of it before continuing.

Install the 'build-essential' package if you haven't already that will install the compiling utilities you will need.
You will probably want to run the command 'sudo apt-get build-dep wine' which should install anything you will need to compile wine. Otherwise you may get messages during './configure' about missing libraries.

Download and extract the source code for wine (I used 0.9.6) from sourceforge [http://prdownloads.sourceforge.net/wine/wine-0.9.6.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.6.tar.bz2).

Get the two patch files needed, and place them in the top directory of the source files:
[http://kaspersandberg.com/~redeeman/winestuff/wine-cvs-glx.diff](http://kaspersandberg.com/~redeeman/winestuff/wine-cvs-glx.diff)
[http://kaspersandberg.com/~redeeman/winestuff/wine-wow-fixes.patch](http://kaspersandberg.com/~redeeman/winestuff/wine-wow-fixes.patch)

Get the two Windows .dll files necessary:
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

Get MozillaControl (I think this is needed for patching WoW)
[http://prdownloads.sourceforge.net/wine/MozillaControl1712.exe?download](http://prdownloads.sourceforge.net/wine/MozillaControl1712.exe?download)

COMPILATION AND INSTALLATION

Before compiling and installing wine, we have to patch the source code. From the top directory of the source files:
$ patch -p1 < wine-cvs-glx.diff
$ patch -p1 < wine-wow-fixes.patch

Now we compile and install wine:
$ ./configure
$ make depend && make
$ sudo make install

Now we need to, as root, make a file with a text editor in /etc called ld.so.conf, that contains a single line specifying a directory: /usr/local/lib
Now run the command 'sudo ldconfig'. This is necessary due to the special way Ubuntu handles dynamic linking (I think), while Wine expects the more standard method.

You may at this point want to run 'wine' with no application specified.
$ wine
This should create the .wine directory in your home directory with the fake C drive.

Now we can put the .dll files in the system folder:
$ mv msvcp60.dll mfc42 ~/.wine/drive_c/windows/system32/

Now we need to install MozillaControl under wine:
$ wine MozillaControl1712.exe

Now we can use the graphical wine configuration utility and choose the following options:
$ winecfg

   1. In the Applications tab change Windows version to &#8220;Windows XP&#8221;
   2. In the Graphics tab:
         1. Enable Pixel Shaders
         2. Set Vertex Shader to Hardware
         3. Enable Allow the window manager to control the windows
   3. In the Audio tab set to OSS output (Option, but reported to be best)

WORLD OF WARCRAFT SETUP

Ok, wine is now ready for WoW. If you do not have a working copy of WoW available, and need to install, your best bet is to copy all of the contents of every CD into a directory on your hardrive, and start the installer using wine. I haven't tested this myself.

Once you have installed WoW, the /World of Warcraft/wtf/Config.wtf file needs to be modified. Add the following lines:
SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"

You should also add in the following two lines, but fill in values for the screen resolution and vertical refresh rate that are right for your setup. Mine were:
SET gxResolution "1280x1024"
SET gxRefresh "85"

Ok, now to run, you can type 'wine WoW.exe -opengl' in a terminal.

WORKSPACE SWITCHING

Ok, I like to use the workspace switching feature in Gnome (also found in every other window manager I am aware of) when playing WoW, to check Thottbot, reply to a IM, particularly on those long griffon/bat flights. I have set shortcut keys to switch to each workspace under System > Preferences > Keyboard Shortcuts, mine are set to CTRL-F1 through F4. If you do this after starting WoW from wine in a terminal, it will switch out, but when you switch back, keyboard input is routed to the terminal instead of the game, so you can no longer use the ingame chat among other things. To fix this, I use a custom panel button to start the game instead. To make this panel button:

1. Right click on the panel you want to add it to (such as the one containing the Applications drop down) and select "Add to Panel..."
2. Highlight "Custom Application Launcher" and click "Add"
3. Give it a "Name" (such as "WoW Wine")
4. Under "Command" type "wine /path/to/World of Warcraft/WoW.exe -opengl"
5. Do not select "Run in terminal"

You can access these options by right-clicking on the button you made and choosing "Properties".

To get the World of Warcraft icon for your shortcut, you can install the 'icoutils' package (in the universe repository I believe). Then run the command:
$ wrestool -x --output=. -t14 /path/to/WoW.exe

This will extract the icon from the .exe file, placing the .ico file in your working directory. To add this icon, press "No icon" in the Properties window for your button, enter the directory where your .ico file is, and choose it.

If you use the panel button to start the game, when you switch workspaces back to the game, the keyboard input will go to the game properly.

LOADING NVIDIA SETTINGS

If you have an nvidia card, you may notice that until you use nvidia-settings during your session, your antialiasing and anisotropic filtering will not be activated. My method to activate these automatically is to start WoW with a script. To create this script, just make a file (mine is named simply 'wow') with the following lines (you can use gedit or other editor):

nvidia-settings --load-config-only
cd '/path/to/World of Warcraft'
wine WoW.exe -opengl

This will load your video card configuration before starting the game. To make this script executable:
$ chmod +x scriptname

To run this from your panel button, just put the script (including the full path) in the Command field.


TOP PANEL PROBLEM

What I experienced is that when switching back to the workspace of the game, the top Gnome panel was still on the screen, and the WoW screen was drawn underneath it, cutting off a small bit at the bottom. My workaround was to drag the top panel (the one with the Applications drop-down) down to the bottom of the screen, just on top of the bottom panel (the one with the trash icon and workspace indicators). This is not ideal, but it worked for me.

SCREEN RESOLUTION/REFRESH RATE PROBLEM

When switching out of the WoW workspace to a different one, I have experienced that the screen resolution switches a few times before settling on the proper desktop resolution (I am running both my desktop and game at 1280x1024 at 85 Hz). It's a bit jarring, but it's not a big deal. However, when exiting the game, the desktop inexplicably settles on a 1600x1200 resolution, which is the highest my monitor can handle. I am then forced to return it to 1280 x 1024 under System > Preferences > Screen Resolution.

If anyone has any ideas on how to avoid top panels being rendered or how to solve the screen resolution issues, or any other ideas or questions, please post to this thread. I'll see you in Azeroth!

UPDATE January 23, 2006

I found a workaround for the problem of it switching to 1600x1200 after game exits (this is apparently a Wine bug). I removed all instances of "1600x1200" in the various "Display" subsections in the /etc/X11/xorg.conf file. Now that resolution is no longer available, and the desktop returns to 1280x1024 upon exit. Also, the workspace switching is much smoother, with just a brief bit of flickering.

UPDATE January 25, 2006

Switched the order of the commands to install MozillaControl and .dll files, and added running the command 'wine' to create the .wine directory in the home directory.

---

### Post by glaze on 2006-01-23
Huge thanks! I had WoW working before, but didn't know the icon thing or a fix for workspace switching problem. Now it's purrfect :-)

---

### Post by schnabea on 2006-01-24
Hi. I am a totally new linux user, picked up Ubuntu cause it seemed stable and cool looking. I am trying to get WoW to run through but I really have no idea what I am doing. I used the synaptic package manager to install the build-essential package you mentioned. I'm not sure what to do next.

I downloaded wine and extracted the wine-20021125-I386-1.tgz to the desktop in a folder named wine. I then placed the two patch files in the wine folder and tried to run the patch command in the terminal and got a long message about how the file in line 4 was not found.

I obviously have no clue what I am doing, so if anyone could point me towards a good step by step resource for this kind of thing I would really appreciate it. I would like to make the move away from windows completely and getting WoW to work will be a big step in that direction.

Also, I have WoW installed on a hdd in an NTFS partition that I use under Windows XP so I need to know how to make that folder available to wine once i get all the other issues ironed out.

Again, any help would be appreciated, I'm sorry for being such a noob :)

---

### Post by Perfect Storm on 2006-01-24
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by alinuxfan on 2006-01-24
AI,
If I do it the apt-get way...how do I add the patches before installing? or can it be done after?

---

### Post by Perfect Storm on 2006-01-24
okay, didn't read the whole thread and can see the problem, you might check this howto and see if it's easier to follow: [http://ubuntuforums.org/showthread.php?t=92367](http://ubuntuforums.org/showthread.php?t=92367)

---

### Post by alinuxfan on 2006-01-24
thanks, I thought I had it workign for a minute, but it gets past where I enter my name and password and says "connecting" forever...gonna look in the thread you pointed me to and see if I can find anything

---

### Post by Viro on 2006-01-24
[QUOTE=schnabea]
I downloaded wine and extracted the wine-20021125-I386-1.tgz to the desktop in a folder named wine. I then placed the two patch files in the wine folder and tried to run the patch command in the terminal and got a long message about how the file in line 4 was not found.
[/quote]

Is there any reason you're using the 2002-11-25 version of Wine? That is almost 4 years old!

---

### Post by alinuxfan on 2006-01-24
[QUOTE=kidcharles]

Now we need to install MozillaControl under wine:
$ wine MozillaControl1712.exe

At this point, wine should have created the .wine directory in your home directory with the fake C drive. Now we can put the .dll files in the system folder:
$ mv msvcp60.dll mfc42 ~/.wine/drive_c/windows/system32/

[/QUOTE]

I found the way to install was to switch these two commands around, you might want to edit your post so that it goes in order in case someone doesn't scroll down to see my post.
All in all it has worked for me...downloading the patches right now...the farthest I have gotten with cvscedega, cedega, or a deb of wine 96
thanks for the howto

---

### Post by kidcharles on 2006-01-24
schnabea:
[INDENT]
I would get the newest source if I were you. Here is a direct link:
[http://prdownloads.sourceforge.net/wine/wine-0.9.6.tar.bz2?download](http://prdownloads.sourceforge.net/wine/wine-0.9.6.tar.bz2?download)

Extract this using the command:

$ tar -xvf wine-0.9.6.tar.bz2

Now you'll have the directory wine-0.9.6. THAT is the top directory in which you should put the patch files. I think what you had before was a directory called 'wine' that contained the directory 'wine-<version number>', and had the patch files in 'wine', while they should have been in 'wine-<version number>'.

One thing I left out is that there are a number of dependencies, packages that are needed for the compilation process, that need to be installed. The quickest way to do this is probably to run the command 'sudo apt-get build-deb wine'. This should grab all the dependencies that you will need to compile wine from source. I'll add that to the top post in the thread.

As for the NTFS partition, you may know that writing to an NTFS partition in Linux is experimental and not recommended as it can destroy data. Reading is fully supported though. I recommend, if you have the space, to make a copy of World of Warcraft on a Linux partition, or at least a FAT32 partition. The game will need to write a multitude of things (chat log files, macro definitions, and addon data files) so running it from an NTFS partition is probably asking for trouble.

Ubuntu by default gives only root the ability to read from NTFS drives. To learn how to change this so normal users have read access to NTFS drives, go to [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs) and read the section entitled: "How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only."
[/INDENT]

Artificial Intelligence:
[INDENT]
The HOWTO that you link to didn't work for me, that's why I thought I'd write this one up. The problem is that it involves using the pre-compiled wine package, which caused problems for me. Also, even if it otherwise works, you will not see targeting circles and surface effects in the game due to a bug in World of Warcraft opengl rendering. There is a sign error in the WoW code that causes targeting circles and the like to be rendered just BELOW the surface, as apposed to just ABOVE the surface. Shame on you Blizzard! The patches that I link to fix this (I think?) and other problems.
[/INDENT]

alinuxfan:
[INDENT]
While getting the precompiled copy of wine is certainly the easiest way to install it, there is not (that I know of) a way to apply the necessary patching to the already compiled files. That's why the method I described starts with the source code. I tried to run WoW with the wine package, and had problems.[/INDENT]

---

### Post by schnabea on 2006-01-24
Alright thanks for the replies... When I get home tonight I'll give everything a try and see if I can't get this working.

---

### Post by alinuxfan on 2006-01-24
[QUOTE=kidcharles]
alinuxfan:
[INDENT]
While getting the precompiled copy of wine is certainly the easiest way to install it, there is not (that I know of) a way to apply the necessary patching to the already compiled files. That's why the method I described starts with the source code. I tried to run WoW with the wine package, and had problems.[/INDENT][/QUOTE]

cool, thanks for the info...
I ended up installing from your howto except i switched around putting the dll's in the system32 folder and THEN install the mozilla exe

thanks for the howto
(I thinkthe realms are down right now cause i can't see the realms to log in, but everything has worked up to that point)

---

### Post by schnabea on 2006-01-25
Ok so I ran the "sudo apt-get build-deb wine" command but I got the error message "E: Invalid operation build-deb" am I doing something wrong here?

Since that didn't work I decided to try and compile wine anyways but it said I needed to install the flex package. I assume that is part of the sudo apt-get problem. Any ideas on how to resolve this?

---

### Post by RAOF on 2006-01-25
[QUOTE=schnabea]Ok so I ran the "sudo apt-get build-deb wine" command but I got the error message "E: Invalid operation build-deb" am I doing something wrong here?

Since that didn't work I decided to try and compile wine anyways but it said I needed to install the flex package. I assume that is part of the sudo apt-get problem. Any ideas on how to resolve this?[/QUOTE]
That's because it should be "sudo apt-get build-de**p** wine".  After you've run that, it should work.

---

### Post by schnabea on 2006-01-25
ahhh lol. Thanks. got that part done now. on to the next step!

---

### Post by schnabea on 2006-01-25
Alright.. one more problem. When I go to install the mozilla control I get an error message saying that it cannot find the mozilla layout libraries or that files are missing int he installation. When I went to the control website the author mentions some C runtime .DLL files which I downloaded. They are MSVCP60.DLL and MSVCRT.DLL Now that I have them I don't know what to do with them to make this work.

Am I even on the right track here? And if not could someone point me in the right direction?

Again, sorry to be such a noob but I really appreciate all the help.

---

### Post by Wolfbite on 2006-01-25
[QUOTE=RAOF]That's because it should be "sudo apt-get build-de**p** wine".  After you've run that, it should work.[/QUOTE]

I run that command, but this is what I get: 

```
Reading package lists... Done
Building dependency tree... Done
Package xlibmesa-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
Package libgl-dev is a virtual package provided by:
  mesag-dev 5.0.0-5.1
  libgl1-mesa-dev 6.3.2-0ubuntu6breezy1
You should explicitly select one to install.
E: Package xlibmesa-dev has no installation candidate
E: Package libgl-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for wine: libgl-dev

```

What should I do?

---

### Post by otake-tux on 2006-01-25
automatix cant be used to install wine?

---

### Post by kidcharles on 2006-01-25
Ahh! Sorry for the build-dep typo, dep is short for dependency. That step is "experimental", I thought it might be a quick way to install all the packages wine needs to be compiled. Another way is to do the 'configure' operation, and each time it errors out saying there is a missing library, go and 'apt-get install' the -dev of that particular library.

---

### Post by kidcharles on 2006-01-25
otake-tux
[INDENT]
I don't know much about Automatix, but I suspect it installs the binary package for wine. This method is specifically a patched source method of installing wine.
[/INDENT]

---

### Post by kidcharles on 2006-01-25
Wolfbite
[INDENT]
I checked the packages I have installed, and I have libgl1-mesa-dev 6.3.2-0ubuntu6breezy1 rather than the other one, so you might try manually installing this particular package. You can use System -> Administration -> Synaptic Package Manager too, it's a GUI program for the package manager.
[/INDENT]

---

### Post by Wolfbite on 2006-01-25
[QUOTE=kidcharles]Wolfbite
[INDENT]
I checked the packages I have installed, and I have libgl1-mesa-dev 6.3.2-0ubuntu6breezy1 rather than the other one, so you might try manually installing this particular package. You can use System -> Administration -> Synaptic Package Manager too, it's a GUI program for the package manager.
[/INDENT][/QUOTE]

Thanks, mate. I just found it wine doesn't support the 64-bit version of Ubuntu, though, so I think I'll wait with it. :)

---

### Post by alinuxfan on 2006-01-25
[QUOTE=schnabea]Alright.. one more problem. When I go to install the mozilla control I get an error message saying that it cannot find the mozilla layout libraries or that files are missing int he installation. When I went to the control website the author mentions some C runtime .DLL files which I downloaded. They are MSVCP60.DLL and MSVCRT.DLL Now that I have them I don't know what to do with them to make this work.

Am I even on the right track here? And if not could someone point me in the right direction?

Again, sorry to be such a noob but I really appreciate all the help.[/QUOTE]

as i told kidcharles
Change the order of the commands:

$ wine MozillaControl1712.exe

$ mv msvcp60.dll mfc42 ~/.wine/drive_c/windows/system32

It should be:
$ mv msvcp60.dll mfc42 ~/.wine/drive_c/windows/system32
then
$ wine MozillaControl1712.exe
(make sure you are the directory with those files for each step)
Those 2 dll's are how mozilla figures out where to install the activex controls
let me know if you have any questions


If you do it like that, I got everything to work, no bugs at all.  I followed his instructions to a T except the one switch right there and it works, I was playing as soon as the realms came up yesterday
Adam

---

### Post by thieves.honor on 2006-01-25
if people are having problems getting the dependencies for wine, then one idea is to get auto-apt from the repositories.  

then run:
sudo auto-apt update
sudo auto-apt updatedb
sudo auto-apt update-local
sudo auto-apt run ./configure

it will go through, download and install all the dependencies that are needed.

---

### Post by kidcharles on 2006-01-25
alinuxfan:
[INDENT]
Thanks for the info about the ActiveX stuff. I've changed the top post to reflect this. I added a line to run the 'wine' command without an argument after installing so that  ~/.wine is made so that the .dll files can be placed there before installing the Mozilla .exe.
[/INDENT]

On another note, I tested out the 'apt-get build-dep wine' method of getting all the needed dependencies and it worked fine on a different Ubuntu machine.

---

### Post by schnabea on 2006-01-25
I'm back. *waits for the groans*

Ok I have everything installed (I think its all correct too :smile: ) and I have WoW installed. I updated WoW using patch files from Fileplanet cause it is a faster dload for me generally than using the blizzard tracker.

Every time i try to start wow with or without the -opengl tag at the end of the command  my screen resolution changes, the WoW music starts and then I get the following error:

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0x80000101 (unknown exception) at 0073:FFFFE410

Now I think we all know its likely I messed something up, but if I didn't does anyone have any idea how to fix this?

Thanks so much for holding my hand through this:D

---

### Post by kidcharles on 2006-01-25
schnabea:

The error 132 is associated with World of Warcraft and is a general error code for a whole number of problems. It appears frequently even in Windows:

[http://www.blizzard.com/support/wow/?id=aww01735p1](http://www.blizzard.com/support/wow/?id=aww01735p1)

This error could be due to wine, or it could be due to WoW. Here's one things I found:

On transgaming.org forums, it was suggested that memtest should be run to check for bad memory:
[http://transgaming.org/forum/viewtopic.php?t=4913](http://transgaming.org/forum/viewtopic.php?t=4913)

If it is happening at a predictable point (like right after selecting character) I would guess that it may not be bad ram, but something else.

I assume when you ran the 'patch' commands that there were one or two lines each time that indicated successful patching? Sorry I can't help more, I'll keep looking though.

---

### Post by alinuxfan on 2006-01-25
schnabea,
what video card do you have and what resolution are you running WoW at?
i run mine at 1024x768 with a refresh of 60 and mine is working fine (FX5200 128 AGP)
I have error messages sometime but I just click ok and it continues doing it's thing...
For now go into winecfg and disable all audio and try it and see if that could be causing your problem...
Let me know how that works out
Adam

---

### Post by moccah on 2006-01-25
Hi there.
I`ve followed this how-to... I`ve even tried Cedega... 
I gave up cedega... and in wine I get an error... Memory could not be read.

This changes the hex value from time to time... I`ve added an attachment.

I managed to play on another char... but as soon as i get to a crowded area, i crash to desktop.

I`ve tried everthing I could think of;
1) disabling the music/sound
2) changing to WinXP
3) I`ve also tried to run```
$wine WoW.exe -d3d
```  I was able to play a little longer, but the textures are seriously bugged.
4)I have edited my Config.wtf as told in this howto, but this didn`t help...

I`m currently running the 8.19.10 ATI driver.

Don`t know if this is of any help, but im pasting it aswell:
```
torage@Gollum:~/.transgaming_global$ dmesg | grep fglrx
[4294730.973000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294730.976000] [fglrx] Maximum main memory to use for locked dma buffers: 1173 MBytes.
[4294730.976000] [fglrx] module loaded - fglrx 8.19.10 [Nov  9 2005] on minor 0
[4294731.017000] [fglrx] ACPI power management is initialized.
[4294731.585000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294731.585000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294731.585000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294731.585000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294731.586000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294731.681000] [fglrx] free  AGP = 256126976
[4294731.681000] [fglrx] max   AGP = 256126976
[4294731.681000] [fglrx] free  LFB = 119828480
[4294731.681000] [fglrx] max   LFB = 119828480
[4294731.681000] [fglrx] free  Inv = 0
[4294731.681000] [fglrx] max   Inv = 0
[4294731.681000] [fglrx] total Inv = 0
[4294731.681000] [fglrx] total TIM = 0
[4294731.681000] [fglrx] total FB  = 0
[4294731.681000] [fglrx] total AGP = 65536
[4296524.416000] [fglrx] Maximum main memory to use for locked dma buffers: 1173 MBytes.
[4296524.417000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4296524.417000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4296524.417000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4296524.419000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4296524.499000] [fglrx] free  AGP = 256126976
[4296524.499000] [fglrx] max   AGP = 256126976
[4296524.499000] [fglrx] free  LFB = 119828480
[4296524.499000] [fglrx] max   LFB = 119828480
[4296524.499000] [fglrx] free  Inv = 0
[4296524.499000] [fglrx] max   Inv = 0
[4296524.499000] [fglrx] total Inv = 0
[4296524.499000] [fglrx] total TIM = 0
[4296524.499000] [fglrx] total FB  = 0
[4296524.499000] [fglrx] total AGP = 65536

```

I am positively sure there is a solution... I just can`t figure out whats wrong :rolleyes:

---

### Post by alinuxfan on 2006-01-26
what video card do you have?
I know when I was trying to use my ATI radeon 7500 series on one computer and my ATI Rage Fury on another
but that was with a different howto.  I didn't find kidcharles' howto until I got my nvidia card...
I'll try to mess around and see if I can get those errors...be back in a bit

---

### Post by schnabea on 2006-01-26
I am using an ATI Radeon 9200se w/ 128 mgs of RAM. When I get home tonight I will try disabling sound to see if that fixes things. I play with sound disabled anyway so that wont bother me.

---

### Post by schnabea on 2006-01-26
ok running without the -opengl command gets me in to the game and everything runs, but of course without the textures. As soon as I try to use the -opengl tag the game will crash after resizing the desktop but before i even see the login screen.

Now I've messed something up though. Last time i ran winecfg I clicked the alsa option by accident in the audio tab and closed it before realizing it and now whenever I run wine or winecfg all I get is the following error message:

ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  14

Any way I can fix that or get the proper file so it will open?

---

### Post by moccah on 2006-01-27
I`ve got a ATI MobileRadeon 9700 128 MB graphic card.

```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5461 (X4.3.0-8.19.10)

```

---

### Post by benjordan06 on 2006-01-28
hello!

first off, thanks for making this guide, it was very helpful so far ...


however, I am running WoW with an athlon 1800+, 1 gig of pc2700 ram, and a radeon 9800 pro 256meg 256 bit, etc...

It is considerably laggier than windows in directx emulation or opengl... I tried to tweak it down to lowest settings and still pretty laggy. Anyone have any new breakthroughs? :)

---

### Post by alinuxfan on 2006-01-28
i am running AMD 1700, 1gig pc3200 and nvidia 5200 128AGP
AND man it runs smooth...then again i haven't played WoW in windows for about 6 months
But I have no complaints whatsoever with the way things turned out following this guide

---

### Post by ashes on 2006-01-29
get this error now:

fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7ccd0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7ccd0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0eef4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f160,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f668,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f654,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0ee70,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x10022): stub
wine-pthread: r200_swtcl.c:103: r200SetVertexFormat: Assertion `VB->AttribPtr[VERT_ATTRIB_POS] != ((void *)0)' failed.
fixme:dbghelp:sffip_cb NIY on 'C:\build\buildWoW\WoW\bin\Wow.pdb'
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

then error 132

---

### Post by moccah on 2006-01-31
Hmm.
I still cant make WoW work under wine... keep getting the error "Memory cannot be written"...

Anyone have the same problem?

---

### Post by Toadicus on 2006-02-01
I followed this method and still have the "mouse bug" problem, where my mouse thinks the background is over the foreground.  I've tried recompiling with different versions (I think) of the Wine WoW patch, and running the export WINEPRELOADER work around, to no avail.  Any suggestions on what I might do to get my mouse to work?

If it's meaningful at all, I can post the text that Wine spews while WoW is loading, and it may be worth noting that WoW has greyed out the "hardware mouse" option.

Thanks for your help. :)

-Toad

---

### Post by moccah on 2006-02-01
I downloaded the latest wine source and patched it with [http://kaspersandberg.com/~redeeman/winestuff/wine-wow-fixes.patch]("http://kaspersandberg.com/~redeeman/winestuff/wine-wow-fixes.patch"). This removed the mouse bug for me. 
However, wow keeps on crashing when im loading my char into the world. 

I`ve heard that there is no need for the GLX patch any more.. can someone confirm this? I haven`t tried to recompile wine without this patch yet.

---

### Post by Toadicus on 2006-02-01
I had that problem running the stock version of wine; patching it with the patches kidcharles linked fixed that.  I'll try recompiling with that patch you gave me, and without the GLX patch... here's hoping.  If anyone else has any ideas, I'd love to hear them. :)

---

### Post by tm.winston on 2006-02-02
In the interest of adding another data point, I followed these directions as best I could, and now get the following error after the game loads (I am able to log in, select my character, and see the loading with progress bar all the way to the end):

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  432
  Current serial number in output stream:  433

```

At this point, the game closes and I am dumped back out.  I have tried turning off sound in winecfg.  Anybody have any other ideas?

---

### Post by ZarathustraDK on 2006-02-04
The method outlined in the start of this thread works perfectly. I followed it to the letter and I'm playing wow now.

System :

3.2 GHz pentium 4
1024 mb sdram
weird agp/pci-e hybrid motherboard from Asrock
Inno3d geforce 7800 GT
Running Ubuntu Breezy

Thanks a lot ;-)

---

### Post by Lord Erik on 2006-02-06
I spent several hours last night trying to install wine and I think it is time to conceed defeat and ask for help.

I installed 5.10 on the weekend and then followed this howto (sort of).  I downloaded the source for wine then tried 

```
erikc@Cassy-May:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine
```

It didnt work.  So I ran ./configure and installed anything it asked for in error messages and also a lot of the stuff that configure said wasn't present.  I think this was a bad idea as I now have a lot of crap on my machine that I probably dont need.

Get to make depend && make and now I get errors.  I wont list the errors here as I think I need to sort out the apt-get build-dep first.  

Why wouldnt be able to find a source package for wine?  Do I need to install wine by package then run build-dep then remove the wine package?  Or am I missing apt sources.

Any help would be appreciated.

---

### Post by Lord Erik on 2006-02-06
I managed to fix my first problem (I didnt have universe enabled) but now it has the following error when running make depend && make

```
make[2]: Entering directory `/home/erikc/wine-0.9.6/dlls/dmime'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o audiopath.o audiopath.c
audiopath.c: In function ‘IDirectMusicAudioPathImpl_IPersistStream_Load’:
audiopath.c:470: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[2]: *** [audiopath.o] Error 1
make[2]: Leaving directory `/home/erikc/wine-0.9.6/dlls/dmime'
make[1]: *** [dmime] Error 2
make[1]: Leaving directory `/home/erikc/wine-0.9.6/dlls'
make: *** [dlls] Error 2
```

---

### Post by Praetorian on 2006-02-06
I wonder myself how much performance you lose if you playing it with wine.
Since the only game I play at this moment is WoW. 
Maybe I can ride of my windows :twisted:

---

### Post by Tartin on 2006-02-06
[QUOTE=Praetorian]I wonder myself how much performance you lose if you playing it with wine.
Since the only game I play at this moment is WoW. 
Maybe I can ride of my windows :twisted:[/QUOTE]

If you've got an nVidia card you probably won't notice any different from playing it on Windows, atleast I didn't. If you've got an ATI card witch I've got on my laptop, it's not even worth installing.

---

### Post by mikelietz on 2006-02-06
[QUOTE=tm.winston]
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  432
  Current serial number in output stream:  433

```
[/QUOTE]

I get a similar error, but the game won't even start up for me. I don't get it when I do the non-openGL, but of course then the game isn't playable.

I used wine 0.9.7 without using any patches. I merely compiled the source and installed it.

and here is what I get:
```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  400
  Current serial number in output stream:  401

```

---

### Post by Imrik on 2006-02-07
[QUOTE=Praetorian]I wonder myself how much performance you lose if you playing it with wine.
Since the only game I play at this moment is WoW. 
Maybe I can ride of my windows :twisted:[/QUOTE]

I followed the guide and got it working just fine. Of course, I added a shortcut to the games tab of the applicatin dropdown instead of just adding it to the panel.

My only complaint is that I lost a little performance (comparing this to windows). Average framerate is about 10 less than it was before. It's playable though, and the jitter I used to get from walking into places like IronForge is completely gone, that alone is worth it to me.

Good luck~

Also, I ditched windows a long time ago since i've been able to get every game I own working in Linux. But I may have more luck than others.

---

### Post by moccah on 2006-02-07
What kind of graphic card you got? NVidia?
It seems like ATI users got a problem... I`ve not tried wine 0.9.7 yet. On the previously release of wine i encountered crash to desktop problems, and ```
 Current serial number in output stream:  401
```

---

### Post by Lord Erik on 2006-02-07
I finally got wine running by reinstalling breezy and then compiling and installing wine in recovery mode (that seemed to stop all the segfaults).  Now I'm having trouble with the WoW installation program.

Has anyone tried installing from one of the WoW 2 week trial DVDs?  Currently it is stopping part way through with file errors.  I'm not sure if the error is on the DVD or when the file is copied to the hard drive.

---

### Post by thieves.honor on 2006-02-07
okay, i have 2 questions.  #1: with wine .0.9.7 do you need the 2 patches??  #2: instead of doing a make install is there a way to create a .deb package??

---

### Post by Lord Erik on 2006-02-07
This is the error I'm now getting.

From the WoW installer
```
The installer was unable to read the file "<unknown>".  This error may be caused by problems with the media or drive at --for example, a scratched or dirty CD-ROM/DVD, hard drive corruption, or a networking problem while downloading the installer.  (The data being read was "World\Generic\Makura\PassiveDoodads\MakuraShells\MakuraShells03.m2", and the error code was 38.)  If this problem persists please contact Blizzard Technical Support (MPQFile:Read)
```

And from wine
```
erikc@Cassy-May:~$ wine d:\Installer.exe
erikc@Cassy-May:~$ fixme:font:CreateScalableFontResourceW (1,0x1210955c,0x121094bc,(nil)): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_GETOLEINTERFACE 0x7e590c8c: stub
fixme:richedit:IRichEditOle_fnGetClientSite stub 0x10090960
fixme:ole:OleCreateStaticFromData (not shown), stub!
```

I've tried from the DVD and from copying the DVD contents to the hdd first.  Any ideas or should I just give up?

---

### Post by Lord Erik on 2006-02-07
I just managed to get it installed by only copying the installer.exe and tome files across.  

Video seems ok but sound is awful (judders and reverbarates) and the mouse is very sluggish.  I dont have an internet connection here right now so I have only seen the intro movie and login page.  I dont really know anything about soundcards under linux so not sure if I can get better sound performace.

---

### Post by RizSilverthorn on 2006-02-07
Excellent guide! WoW was the only reason I hadn't hosed my Windows install (now reformated and completely Ubuntu system). I also have but two issues with WoW:
[LIST=1]
[*]FPS. My fps is pretty bad - under Windows I was getting @35-40 in Org at 1280x1024. Under Wine (or the cedega_time_demo) I get 14-20! My system is NF4 mobo, A64 3200+, 1024MB DDR400 RAM, GF6600 256MB PCI-E. I have installed the latest nvidia drivers (8178 ). I use a Creative SB Live! for WoW & system sounds through the speakers, onboard audio for the headset & mic for Skype.
[*]Being left handed, I use the numberpad with numlock on for movement & spellcasting. When I press 8 (forward) my toon runs until I press 5 (backward). My toon then stops and neither key works again. The same happens to all of the other numberpad keys. I tried the cedega_time_demo, and apart from the annoying logo pulsing away in the middle of the screen and the same low fps, it works fine. The numpad keys work properly. I am 95% certain I'm going to buy a sub to cedega, but until I can afford it (maxed out on Credit Card!) I hope there is a solution to my problem.
[/LIST]
My WoW install is a copy of the one that used to live on my C: drive under windows before I formatted and installed Ubuntu.

After all the issues, I am amazed at the amount of improvement GNU/Linux has made since I first installed my first distro (Slackware '95) in 1995 and the fact I can play a Windows game without windows!

---

### Post by mikelietz on 2006-02-07
[QUOTE=moccah]What kind of graphic card you got? NVidia?
It seems like ATI users got a problem... [/QUOTE]

Yes, ATI, using fglrx. Still haven't heard if I'm supposed to use a GLX patch for 0.9.7.

---

### Post by zionpsyfer on 2006-02-08
Weirdness all around, I've tried using cedega 5.0.1, wine 0.9.6 and 0.9.7(both wine versions patched with the wow fixes).  

I can log in with all of the above.  With the patched wine cvs releases I can get about 1 fps in the game, but no textures load.  Everything is white, with shadows.  With Cedega, all the textures load, but my framerate drops to perhaps one frame every five seconds.   This occurs whether or not I use the -opengl switch.   I've edited the Config.wtf file for wow and appended 

 SET gxApi "opengl "
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "16"
SET gxDepthBits "16"
SET gxResolution "800x600"
SET gxRefresh "60"
_____________________________
To the end, reducing my resolution and color/depth to see if it would help.  No difference.  


glxgears and fglxgears come up with halfway decent framerates, and the native UT2K4 install runs beautifully.  Great framerate at high detail.  


So I know d3d and opengl are working (correct me if glxgears/fglxgears/ut2k4 only implies one is functional.)



hardware: radeon9200

lsmod shows the following related modules loaded:

via_agp
agpgart
fglrx

Any ideas?  I'm fresh out of ideas besides pulling the card and trying an nvidia.



edit:

glxinfo | grep render
direct rendering: Yes
    GLX_ATI_render_texture
OpenGL renderer string: RADEON 9200 DDR Generic


fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)                                   <~~~  low ver num?

---

### Post by moccah on 2006-02-08
UPDATE:

I`ve now tried wine 0.9.7 with the wow patch only, the glx patch only, both patches, and no patches. I still get the crash-to-desktop problem. I also tried the cedega_timedemo.. It worked, but the framerate was very low.

My Config.wtf:
```

 SET gxApi "opengl "
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x800"
SET gxRefresh "50"

```

lsmod shows:
```

intel_agp
agpgart 
fglrx

```

glxinfo:
```
glxinfo | grep render
direct rendering: Yes
GLX_ATI_render_texture

```

dmesg | grep gl:
```

[4294722.993000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies , Starnberg, GERMANY' taints kernel.
[4294722.996000] [fglrx] Maximum main memory to use for locked dma buffers: 1173  MBytes.
[4294722.996000] [fglrx] module loaded - fglrx 8.21.7 [Jan 14 2006] on minor 0
[4294724.056000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294724.056000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294724.056000] [fglrx] Kernel AGP support doesn't provide agplock functionalit y.
[4294724.056000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of  chipset)
[4294724.057000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294724.143000] [fglrx] free  AGP = 256126976
[4294724.143000] [fglrx] max   AGP = 256126976
[4294724.143000] [fglrx] free  LFB = 115732480
[4294724.143000] [fglrx] max   LFB = 115732480
[4294724.143000] [fglrx] free  Inv = 0
[4294724.143000] [fglrx] max   Inv = 0
[4294724.143000] [fglrx] total Inv = 0
[4294724.143000] [fglrx] total TIM = 0
[4294724.143000] [fglrx] total FB  = 0
[4294724.143000] [fglrx] total AGP = 65536

```

fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5582 (8.21.7)

```

If anyone can see any errors in the outputs I`ve put here, please tell me.. I can`t figure out how to get wow to work.

---

### Post by GIBson3 on 2006-02-09
Well I've tried under Wine 9.4 and 9.6 and both have given me this Error when trying to Run WoW.  I was able to install just fine, I've installed the ActiveXMozControl However it keeps telling me that it can't find my moz. Libs, any idea's?

it's bombing out in the IsWow64Process call...

the following is the output from Wine

```

sean@edge:~/wine-0.9.6$ wine /home/sean/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl
wine: Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process, aborting
wine: Unimplemented function KERNEL32.dll.IsWow64Process called at address 0x5ed09ec5 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function KERNEL32.dll.IsWow64Process called in 32-bit code (0x7bebb248).
In 32 bit mode.
Register dump:
...

```

---

### Post by Phoenixfatali on 2006-02-10
For the ActiveX Mozilla problems people are having the solution is to put the .dll's into the System folder instead of the Sytem32 folder.  It looks like wine reads all of the 32bit dll's from the System folder and the System32 folder is for show.  

Even with that solved for me WoW crashes as soon as I try to connect.  It goes through a few of the authenticating options, says downloading and crashes with the normal send error screen wow has declaring a page fault.  This is the wine output in the console

fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0ee70,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x10022): stub
fixme:dbghelp:sffip_cb NIY on 'C:\build\buildWoW\WoW\bin\Wow.pdb'
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

I patched wine exactly as the article stated, wow starts up fine and the framerate looks good but it just freezes when it hits the downloading message.  It's possible they released a patch this morning for WoW that isn't downloading properly in wine but it would be nice if I could get WoW to patch itself.  If anyone has seen this problem before help would be appreciated.

---

### Post by flayedchild on 2006-02-10
***EDIT***
nevermind... they are back up :)
**/EDIT***

is there any reason the patches are not linked anymore? 
I got this to work a few days ago on my compie, and was gonna try on my roommates... but where did the patches go?
-FC

---

### Post by Phoenixfatali on 2006-02-10
Ok, the problem with it freezing during connecting can be solved through two things. One is add SET ffxGlow "1" in your config.wtf.  The other is to make your WDB folder in the world of warcraft directory read only.  These two things solve some problems that came up in the patching of the last week.

---

### Post by vulpine on 2006-02-12
this is the greatest post ever

thank you for this write up

---

### Post by moccah on 2006-02-13
[QUOTE=mikelietz]Yes, ATI, using fglrx. Still haven't heard if I'm supposed to use a GLX patch for 0.9.7.[/QUOTE]

I will try to compile wine 0.9.7 with all the patches + I`ll try to compile without the GLX patch. I`m at work right now, so I`ll post when I`ve tried it.

---

### Post by GIBson3 on 2006-02-13
[QUOTE=Phoenixfatali]For the ActiveX Mozilla problems people are having the solution is to put the .dll's into the System folder instead of the Sytem32 folder.  It looks like wine reads all of the 32bit dll's from the System folder and the System32 folder is for show.  
[/QUOTE]

Thank you for that, I've got the MozConrtol installed at least :D

Now I'm going to track down that damn isWow64Process error :-k 

The part that Bugs me at this point is the
```
Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process
```

Maybe it's just me, but "isWow64Process" sounds more like a WoW.exe function than a KERNEL32.DLL function... maybe that's just me.

[edit]

wrong there, WOW64 is apperently the name of the 32 bit emulation layer in windows 64-bit...  I'm assuming it means "Windows on Windows64"  anyway, I'm currious as to why my copy of wine doesn't seem to support this call. I've tried 0.9.4/0.9.6/0.9.7 all with the same results, but everyone else seems to be fine...

[/edit]

[edit2]

ok after more research it appears this is actually because the gl.h file isn't being found via configure I can fix this easily enough.  Thank you wine mailing list archives and google. :D 

[/edit2]

---

### Post by moccah on 2006-02-14
Hi there.
After testing various patches and fixes, i finally managed to get WoW working on my Laptop. I think this fix will work for users with ATI Radeon Mobility Graphic card. (I`ve only tried it on my laptop, sorry).

Anyhows these are the steps.

1) Grab the latest ATI driver from [http://www.ati.com]("http://www.ati.com")
2) Make sure you uninstall any old ATI driver; Launch the Terminal Application/Window and navigate to the /usr/share/fglrx folder. Then, enter the command ```
sudo sh ./fglrx-uninstall.sh
```
3) Now, make the ATI driver executable ```
chmod +x /path/to/atiDriver
```
4) Run ```
sudo sh ./ati-driver-installer-8.22.5-i386.run
```
5) After installing type in ```
sudo aticonfig --initial
```
6) Then reboot.

Then I grabbed the latest Wine source (wine 0.9.7). Patched it with the GLX patch, and the WoW-fixes patch (Links are on the first page of this tread).

Tell me how this works out ;)

[Edit]
I forgot to mention that I`ve made the WDB read-only
[/Edit]
-Regards

---

### Post by zodder on 2006-02-14
[QUOTE=moccah]Hmm.
I still cant make WoW work under wine... keep getting the error "Memory cannot be written"...

Anyone have the same problem?[/QUOTE]
Not sure if you figured this out yet, but I got the same error when I tried to connect after entering my WoW logon info. I fixed it by giving myself write permission on all directories in the "World of Warcraft" folder.

---

### Post by moccah on 2006-02-14
I had all write permissions.. it seems that my problem was the graphic card driver...

---

### Post by larsemil on 2006-02-20
i get this error, what to do?

```
larsemil@gandalf:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135
```

---

### Post by moccah on 2006-02-20
It seems to me that the OPENGL32.dll is missing..

Did you install wine via src?

Try to run "wine WoW.exe -d3d" just to see if the game starts or not.

---

### Post by larsemil on 2006-02-20
```
larsemil@gandalf:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe - d3d
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Fil es\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135
```

i installed it from src, doing EXACTLY as said... i really dont get it...

Edit: 
if i try sh configure --with-opengl i get an error while make dep && make

Could not open exdisp.h for output
make[1]: *** [exdisp.h] Fel 1
make[1]: Leaving directory `/home/larsemil/wine-0.9.6/include'
make: *** [include] Fel 2

---

### Post by moccah on 2006-02-20
Is this wine 0.9.8 or 0.9.7, I haven`t tried 0.9.8 yet...

---

### Post by larsemil on 2006-02-20
it is 0.9.6

---

### Post by Gaferion on 2006-02-21
[QUOTE=larsemil]i get this error, what to do?

```
larsemil@gandalf:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135
```[/QUOTE]

I am having that exact same error on my machine after following this guide.  I have also tried :

sudo make uninstall
sudo make distclean
rm -rf /home/username/.wine
./configure --enable-opengl
make depend && make
sudo make install
wine (to build directory again)
copy all dll files and run Mozilla ActiveX setup per guide

same error as above when trying to run WoW.exe

I have installed the fglrx drivers following the guide: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584).  I get ~930-940 FPS in fgl_glxgears (sp?)  So I think I installed it right.

After doing that guide, I removed wine again and recompiled/installed doing commands listed above ... still got the error.

Only info I really found online about the error was to use --enable-opengl switch which hasnt helped me.

I have a Intel P4 3.0 Ghz with HT, 1GB Ram, Radeon 9800 PRO using smp kernel latest

I will try downloading the 0.9.7 and applying the patch and seing if that helps.  Also, 0.9.8 is out now ... any news on how that works and if you need patches for it or not?

---

### Post by larsemil on 2006-02-21
i tried 0.9.7 and got the same error again, although i compiled with the --with-opengl option.

think there is some dependencie needed but not prompted for opengl32.dll?

---

### Post by lungdart on 2006-02-21
Went with this tutorial to install wine 0.9.8 with the patches. Now when i wine anything i get these errors

```

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

Along with other errors regarding opengl32.dll for WoW, and any other game i have installed. I've tried reinstalling the apt wine of the same version and no change, and doing a complete removal leaves my wine still there (built from sources)

How can i get rid of/fix this wine configuration? All my other wined apps are useless now and i cant get them working. WoW with my current wine but wasnt able to select anything with the cursor.

I would do anything to get back to regular wine-0.9.8, since this compile seems to have been botched

HELP!:evil:

**edit:** Did a make unininstall and a make distclean, reinstalled 0.9.8 with synaptic, and everything works accept the mouse over again.

Maybe theres another fix for 0.9.8 or something, b/c that guide just didnt cut the cake for me.
Looked back at my error before and it was the same error with the opengl.dll, just getting the dll wouldnt cut it for me though since not even winecfg or anything would work.

This seems interesting as well

> 
I just installed 0.9.8 hoping the bug #4143 is gone but NOOO it is not... again...
Why dont you finally take this bugfix into wine??? Its anoying because compiling wine myself using the fix does not compile the opengl32.dll.so (another anoying bug!)


There seems to be the reason the opengl error was happening and the link to the bug is here [http://bugs.winehq.org/show_bug.cgi?id=4143]("http://bugs.winehq.org/show_bug.cgi?id=4143")
But i cant make heads or tails out of bug trackers. They boggle my non developer mind. Hope its useful to someone. in the meantime, ill be off to see if i can find some tutorial for wine 0.9.8 with the wow patch that works for me

---

### Post by Gaferion on 2006-02-21
The error just above is the OTHER error on a different computer, my laptop, with a radeon 9600 mobility card ... so knowing how to also fix that would make me happy.

I also have a new problem.  What I've done so far is install wine from CVS, then remove and installed from ubuntu's repository, then removed that and am trying to install from CVS again with new ideas ... however there seems to be configurations all over from previous installs that are not getting cleaned out.  Currently after installing wine from CVS again, I am now getting this error :

```
gaferion@Hinata:~$ wine
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
gaferion@Hinata:~$

```

Anyone know how to totally clean wine off a system?  I've been doing :

```
sudo make uninstall
sudo make distclean
```

to remove the CVS and to remove the ubuntu flavour I went to Synaptic Package Manager and did a complete removal of wine (which purges configuration files also).

If no one really knows, I'll just re-install ubuntu since its a fresh install anyways. :P

---

### Post by lungdart on 2006-02-22
> 
Now we need to, as root, make a file with a text editor in /etc called ld.so.conf, that contains a single line specifying a directory: /usr/local/lib
Now run the command 'sudo ldconfig'. This is necessary due to the special way Ubuntu handles dynamic linking (I think), while Wine expects the more standard method.


Did you do that after compiling? Because i tried running wine before this step and had a similiar error when i compiled it myself.

I read that the latest greatest CVS builds are already patched. So if you checked those out and compiled them you should be good to go. Only problem for me is that i have my current wine configuration exactly where i need it for my other games i wine. Just WoW has the "no click" problem everything else works fine. Now if i could install wine cvs along side of 0.9.8 that would be great! being able to run say wine *.exe for my other games and winecvs WoW.exe for wow, but I have no idea how to do that.

Noobs helping noobs, together we'll piss off the world, lol

---

### Post by Gaferion on 2006-02-22
I'll check that ... I did that step the first time I installed CVS, and thought it would still be created after I uninstall since I created that file outside of the wine installation.  I didn't try create / make sure it was created when installing CVS a second time.  Thnx for the tip.

UPDATE: I re-installed and installed CVS following guide.  Only thing I did different was before configuring/building I did
```
sudo apt-get build-dep wine
```
which WAS meantioned at the beginning of the guide ... I missed I sped read to the 'commands' ... :-\  Only thing is that its recomended to prevent errors during configure but actually this resolved the OPENGL.DLL issue for me ... I would say to do the build-dep command regardless

Anyways, so WoW starts, but FPS is dog slow ... Normally on windows box with settings I have I get about 45-50 FPS avg ... now I get 10-20 avg.  Also, when I try to click the audio tab in winecfg I get the following error (snippet):
```
wine: Unhandled page fault on write access to 0x6c38dbc8 at address 0x7eca53b1 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x6c38dbc8 in 32-bit code (0x7eca53b1).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7eca53b1 ESP:7fadc6e8 EBP:7fadc710 EFLAGS:00210202(   - 00      - -RI1)
 EAX:7c0b2a04 EBX:7ed41cd0 ECX:7c045bd8 EDX:7c0c33b8
 ESI:00000004 EDI:7c1c2260
Stack dump:

```But, not too too concerned about that cause audio is working (sorta ... choppy even after playing with buffer setings)

Also, if I try to change ingame video settings, game crashes ... I was trying to disable things to improve performance ...

Ideas on any of the issues outlined?

---

### Post by Delvien on 2006-02-24
Hey guys , just got WoW to work with ACCEPTABLE performance ( very ppoor compaired to windows ) ( which sucks because i dont want to boot that crappy OS ANYMORE !!..


Anyway i am getting a fatal error when changing Video settings down to Low on everything.

I was able to set my resolution with the config.wtf file , but i need to know what i can do to fix this problem , and possibly have better performance.. 

Also what are the commands to put in config.wtf to set all the settings on low ( command for each one )

---

### Post by moccah on 2006-02-24
You can try to run 
```
 wine WoW.exe -d3d 
```

In my experience this will let you change Video settings in WoW.

---

### Post by Delvien on 2006-02-24
[QUOTE=moccah]You can try to run 
```
 wine WoW.exe -d3d 
```

In my experience this will let you change Video settings in WoW.[/QUOTE]


Per the Gentoo wiki i put that in my config.WTF file to run d3d as my 3d accelerator and it is still a problem but i will try running it by that command

---

### Post by yhatz on 2006-02-24
i have recently installed ubuntu 5.10 and my niece is mad because he can't open his favorite GameBoy Advance emulator anymore.can anyone help me with this?

---

### Post by Mnemonicman on 2006-02-26
It works for a minute or two but soon locks up. And when it does it has a low fps. Any way to remedy this?

---

### Post by alinuxfan on 2006-02-26
Mnemon,
do you actually get into the game?
did you follow kid charles' howto exactly?
I am running with 1gig DDR and a geforce 5200 128mb and I get a bit of a low frame rate but that is my only problem, other than that by following his howto on a fresh ubuntu install it works great

alinuxfan

---

### Post by vashstampede on 2006-02-27
Hiya, im new to the forums and somewhat to linux.  I have tried linux a few times  before but have always had to go back to windows because i get too frustrated not being able to do anything, but now i found this thread with nice helpful people and am hoping to change that.  

i have followed this guide to the T and keep running into the same problem.  i get to the point where i move the .dll files and try to run MozillaControl1712.exe in wine and it gives me an error:

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.12 Setup" of other process window (nil) should not use SendMessage
Fixme:win:SetWindowTextA setting text "Mozilla ActiveX Control v1.7.12 Setup" of other process window (nil) should not use SendMessage
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.


i have tried everything i can think of.  i have reconfigured the x server via the command: sudo dpkg-reconfigure xserver-xorg

i have tried installing the flgrx driver numerous times, and i dont think that is installing correctly either.  

i downloaded everything from the links given and have done this right after installing and updating the packages.  hopefully someone can help me? i keep reading all these success stories and i cant seem to get it working, it is making me very frustrated.  

can anyone please help?

PS.  sorry for being so long winded.

---

### Post by Delvien on 2006-02-27
Well i have better framerate than in windows my only problem now is that i dont see any Text above characters heads ( names , dmg being dealth, resist messages etc) anyone figure this out and fix it?

---

### Post by lox on 2006-02-28
hi, great howto: the first one i actually could follow and worked, altho i have 1 MAJOR problem..
my wine can't install in the home/.wine folder.. do i had to create a different drive_c, where i installed activeX controlls WOW the dll's everything!
now, to run 3d applications i need to put sudo infront of the command, because ubuntu doesnt allow my normal user 3d acceleration.
so i: sudo wine wow.exe -opengl
well, that doesnt work, because he can't find wow.exe
if i doubleclick the wow.exe (starting wine automaticly) the game is way to slow, mouse moves once every 3 seconds.. (i do not get errors!)
i believe that my problem lies with wine, not allowing 3d accel, because i am under my user!? (sudo GLtron has great speed, sudo glxgears super, without sudo.. = no openGL)
and how can i make it so wine let's me install to the real "fake" C disk, because the one with WOW on it didn't even have a windows/system32 folder

#1 Can i make ubuntu grand acces to all users for 3d accel?
#2 Can i change the .wine folder? so wine sees another folder as the real "fake" drive c?
#3 do i have to install directX from the wow cd's?
#4 how do i uninstall wine? :D

---

### Post by Squiddish on 2006-02-28
Hey all, brand new to Linux for the most part, and I'm trying to follow what you guys have posted in order to get wine and WoW to work.  However, when I run the make command to compile wine:

```

./configure make depend && make sudo make install

```

I get this error:
```

configure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/sh tools/config.sub make failed


```

I've run the patch commands properly before trying to compile.  Thanks all, any help is appreciated.

---

### Post by lox on 2006-02-28
[QUOTE=Squiddish]
```

./configure 
make depend && make 
sudo make install

```
[/QUOTE]
they are 3 seperate commands :mrgreen:

---

### Post by Squiddish on 2006-02-28
Ah, well when I run the first command it tells me that my compiler can't compile executables :(

---

### Post by Delvien on 2006-03-01
Well i have gotten WoW to run for the most part... but now the problem is i cannot click on characters or NPCs so i cannot fight or quest at all, anyone have this problem? if so what is the solution?

---

### Post by polpak on 2006-03-01
[QUOTE=Squiddish]Ah, well when I run the first command it tells me that my compiler can't compile executables :([/QUOTE]

sudo apt-get install build-essential

---

### Post by Squiddish on 2006-03-01
Well that command seemed to build something, but then I still ge the "compiler cannot create executables" error when I try and compile wine.  KInd of at a loss at this point.

---

### Post by lox on 2006-03-02
[QUOTE=Squiddish]Well that command seemed to build something, but then I still ge the "compiler cannot create executables" error when I try and compile wine.  KInd of at a loss at this point.[/QUOTE]
make sure you have the bison package, make sure you are in the right directory, and make sure you got wine extracted right, try the tutorial again and follow it precicely

---

### Post by ffadmraven on 2006-03-05
Ok, I have done everything up to installing, but when I go to install it keeps asking for me to insert disk 1.  Any ideas on what I should do?  

I have all the CD's copied to my hardrive since I can't seem to get it to copy from my windows NTFS partition.  

Also I appear to be having a font issue with the EULA, so any ideas on that one would be helpful as well.

---

### Post by Yob on 2006-03-05
Hi,

I'm on an amd64 system and can't compile wine with the patches myself. I've tried getting the game to run with every version of Wine available (from 0.9.3-0.9.9) but to no avail.
Right now I have the latest version installed (0.9.9) but can't play the game. When in luck i get to the character selection screen but now i can't even log in.

I anyone could supply a patched deb i would be very, very grateful :D

---

### Post by realistic on 2006-03-05
Hi,

I've started yesterday with linux and i'm trying to run WoW aswell.
I came really far with this thread but now i'm stuck.

> [I]You may at this point want to run 'wine' with no application specified.
$ wine
This should create the .wine directory in your home directory with the fake C drive.[/I]


That's the point where I am now, and I get this message when i type it in the terminal :

```
martijn@dagobah:/mnt$ wine
Wine 0.9.9
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
```

If I try in the directory where i did all other things (/home/wine/wine{version number}) I get the same message.

Does anyone now what I'm doing wrong?

Before linux I worked with windows so I don't know really much about linux yet.

EDIT : oops, my father said it's a hidden directory.
It worked now :-)

---

### Post by Yob on 2006-03-05
Hi,

Did you install WOW? If so open a terminal and do:
cd .wine/drive_c/Program\ Files/World\ of\ Warcraft/

Hit enter and then do:
wine wow

That should start your game ;-)

---

### Post by realistic on 2006-03-05
No, I still didn't manege to install the game.

If my pc is installing from the first cd, everything is alright.
Then I have to change to cd 2.
That's where it goes wrong now.

How do I change the cd?
If I put the second cd into my drive, and mount that drive, I can see the files on the cd.

I got a message "please insert cd 2" and then I can click "okay: or "cancel"
When I click okay, my pc does nothing, and puts the same message on my screen again.  When I click cancel, the installation has been quit. (yes, ofcourse)

How do I change CDs so my pc picks disk 2?

---

### Post by Yob on 2006-03-05
I had a somewhat similar problem when installing. 
Apparently the easiest way is to copy your installation from a windows machine but is it possible to install via wine as well.

As I don't have a windows machine handy i chose to copy all five Cd's to my computer and start the installer locally.

When all files have been copied you start the installer the same way you tried to start the game. CD into the directory where the files are, and simply go "wine installer" or whatever the name is.

---

### Post by ffadmraven on 2006-03-06
Ok, I found out what my problem was.  for some reason when I copied the first disk, it didn't copy the DirectX folder.  I copied it over and now the installer seems to be running just fine.

---

### Post by realistic on 2006-03-06
[QUOTE=Yob]I had a somewhat similar problem when installing. 
Apparently the easiest way is to copy your installation from a windows machine but is it possible to install via wine as well.

As I don't have a windows machine handy i chose to copy all five Cd's to my computer and start the installer locally.

When all files have been copied you start the installer the same way you tried to start the game. CD into the directory where the files are, and simply go "wine installer" or whatever the name is.[/QUOTE]

I tried this now.
I copied the files yesterday already, and I quit after that.
Now I try to run WoW just as you said it, and then I get the following message :

```
[I]martijn@dagobah:~/wow install$ wine Installer.exe
martijn@dagobah:~/wow install$ err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Missing symbol {Error%dOpening%s}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {ContactTechSupport}! (SymbolTable::UnmappedSymbolSubstitution)
fixme:font:CreateScalableFontResourceW (1,0x1121e208,0x1121a308,(nil)): stub
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.[/I]
```

I know already that the display isn't set good.
Where can I change it?  I tried almost every wine file to see if it is the good one.
(found the right file yesterday, but don't know anymore where it is)

It would be nice if you can help me

---

### Post by realistic on 2006-03-08
Well, fixed that problem now to :-)
Only don't know anymore how.

Now I've got another problem :

```
martijn@dagobah:~/.wine/drive_c/World of Warcraft$ wine WoW.exe -opengl
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!

```

Does this mean that it matters that I don't have an opengl video card?
My current is an Ati Radeon 9200SE 256MB.

I'm planning to buy an Nvidia 256 MB (don't know exact type).
Would it help if I do that?

And if not : What do I have to do that make the game works?

---

### Post by GIBson3 on 2006-03-08
[QUOTE=realistic]Well, fixed that problem now to :-)
Only don't know anymore how.

Now I've got another problem :

```
martijn@dagobah:~/.wine/drive_c/World of Warcraft$ wine WoW.exe -opengl
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!

```

Does this mean that it matters that I don't have an opengl video card?
My current is an Ati Radeon 9200SE 256MB.

I'm planning to buy an Nvidia 256 MB (don't know exact type).
Would it help if I do that?

And if not : What do I have to do that make the game works?[/QUOTE]


The Radeon 9200SE is OpenGL Compatible... though the ATI drivers are not the Friendliest out there... as for the Error are you using the ATI Drivers?

---

### Post by ffadmraven on 2006-03-08
Ok, now I've come up with 2 more problems.  the first is video, it is really jerky, and my mouse and keayboard appear to be lagging.  the other one, is that it won't apply some of the patches.  Any ideas out there?

---

### Post by realistic on 2006-03-09
[QUOTE=GIBson3]The Radeon 9200SE is OpenGL Compatible... though the ATI drivers are not the Friendliest out there... as for the Error are you using the ATI Drivers?[/QUOTE]

I'm not sure what drivers I'm using.
I've got the drivers that were installed when I installed Ubuntu, after that, I didn't upgrade my drivers anymore.
I'll take a look for a new driver that supports openGL

---

### Post by nevyndarkdawn on 2006-03-11
Squiddish - I got the unable to compile error and managed to fix it by doing
```
export CC=gcc
```
before running ./configure

---

### Post by trorion on 2006-03-11
When I launch it crashes (d3d, opengl, noflag with WoW.exe; Launcher.exe will give an error, launcher then crash) gives me a feedback manager (maybe I should send it to Blizzard explaining that I need them to start supporting WoW though linux...).  Looks to me like it's a problem with my GLX?  If so is there a way I can patch without removing the existing wine?  If not how can I completely remove wine before attempting again?
```
trorion@desktop:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe --enable-opengl
Xlib:  extension "GLX" missing on display ":0.0".
err:opengl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cf10000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf10000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0eef4,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
fixme:dbghelp:sffip_cb NIY on 'C:\build\buildWoW\WoW\bin\Wow.pdb'
```

---

### Post by trorion on 2006-03-11
[QUOTE=trorion]When I launch it crashes (d3d, opengl, noflag with WoW.exe; Launcher.exe will give an error, launcher then crash) gives me a feedback manager (maybe I should send it to Blizzard explaining that I need them to start supporting WoW though linux...).  Looks to me like it's a problem with my GLX?  If so is there a way I can patch without removing the existing wine?  If not how can I completely remove wine before attempting again?
```
trorion@desktop:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe --enable-opengl
Xlib:  extension "GLX" missing on display ":0.0".
err:opengl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cf10000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf10000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0eef4,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
fixme:dbghelp:sffip_cb NIY on 'C:\build\buildWoW\WoW\bin\Wow.pdb'
```[/QUOTE]

This problem was caused by a bad video driver.  My video card was nVidia and I used the How To at [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+latest+nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+latest+nvidia) now my problem is gone.  Smokin' action!

---

### Post by slag on 2006-03-12
For those people having the following problem:
```

Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
```

Try running the following command before compiling wine from source.
```

sudo apt-get build-dep wine
```

I had wine running perfectly a week ago, and I'm getting the above error now.  I realized that I forgot to build the wine dependencies, and that's the ONLY different step.  Give it a try, I'm almost sure it will resolve the problem.  When compiling wine there was a warning about the X-developer libraries, and I think build-dep wine gets those installed for you.

---

### Post by slag on 2006-03-12
Here's that warning I was talking about when configuring the wine source:
```
*** Warning: X development files not found. Wine will be built without
*** X support, which currently does not work, and would probably not be
*** what you want anyway. You will need to install devel packages of
*** Xlib/Xfree86 at the very least.
```

And "sudo apt-get build-dep wine" definitely does the trick.

---

### Post by aqualad on 2006-03-12
When I try to run the patches I get no response and end up having to break it with Ctrl+c, does anyone know why these patches are unresponsive? command:
```
aqualad@aqualad:/mnt/shared/Games/WoW$ patch -p1 wine-wow-fixes.patch
``` Then I Ctrl-C break because nothing happens after many minutes, then I try the other ```

aqualad@aqualad:/mnt/shared/Games/WoW$ patch -p1 wine-cvs-glx.diff
```
Still no response.

---

### Post by trorion on 2006-03-12
Works great but just 1 question..
How do I stop wine from using <alt + left_click> from moving my screen?  I would like to be able to alt-click for self casts but when I do that it moves my window (which is, incidentally, very cool).

---

### Post by ffadmraven on 2006-03-12
[QUOTE=aqualad]When I try to run the patches I get no response and end up having to break it with Ctrl+c, does anyone know why these patches are unresponsive? command:
```
aqualad@aqualad:/mnt/shared/Games/WoW$ patch -p1 wine-wow-fixes.patch
``` Then I Ctrl-C break because nothing happens after many minutes, then I try the other ```

aqualad@aqualad:/mnt/shared/Games/WoW$ patch -p1 wine-cvs-glx.diff
```
Still no response.[/QUOTE]


Did you make sure that the patches were in the top wine directory where the source files are?

---

### Post by biggi_mat on 2006-03-17
hi,
i have a problem with wow myself too.  here it is:
[email]biggi_mat@kista:~/.wine[/email]/drive_c/World of Warcraft$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7bf10000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bf10000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7faeeedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7faeee58,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  398
  Current serial number in output stream:  399
[email]biggi_mat@kista:~/.wine[/email]/drive_c/World of Warcraft$ X Error of failed request:  BadDrawable (invalid Pixmap or Window paramete r)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Resource id in failed request:  0x0
  Serial number of failed request:  122
  Current serial number in output stream:  124
[email]biggi_mat@kista:~/.wine[/email]/drive_c/World of Warcraft$


all that happens during that thing is that my screen resolution goes from my standard 1600x1200 to 1024x786.
any ideas what goes wrong? 

thanks for answers.

edit: when i installed wow it was working just good, then i upgraded with new patch (1.9.x) and now that happens.

---

### Post by tezzarist on 2006-03-18
I can't get "sudo apt-get build-dep wine" working just comes with this:

```
sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine

```

I need to get this working I've tried without but then I get:
 
```
*** Warning: X development files not found. Wine will be built without
*** X support, which currently does not work, and would probably not be
*** what you want anyway. You will need to install devel packages of
*** Xlib/Xfree86 at the very least.
```
 
I read something earlier on how to fix this something about having "universe enabled" to get it to work

Please help

---

### Post by tezzarist on 2006-03-18
Ok I figured it out by uncommenting the 2 universe lines in apt/sources.list

---

### Post by stu on 2006-03-19
My compile of wine 0.9.6 went through fine, and I did the ldconfig step and installed the 2 dlls no problem along with the Mozilla controls as well. Winecfg works fine, and I set my options...

But when I try to run WoW.exe, it tells me that opengl32.dll cannot be found... I guess my compile didn't build it for some reason?

---

### Post by larsemil on 2006-03-19
[QUOTE=stu]My compile of wine 0.9.6 went through fine, and I did the ldconfig step and installed the 2 dlls no problem along with the Mozilla controls as well. Winecfg works fine, and I set my options...

But when I try to run WoW.exe, it tells me that opengl32.dll cannot be found... I guess my compile didn't build it for some reason?[/QUOTE]



i get this error aswell. and we are not alone. but i've not found any soloution. anyone else?

---

### Post by larsemil on 2006-03-19
[QUOTE=larsemil]i get this error aswell. and we are not alone. but i've not found any soloution. anyone else?[/QUOTE]


i got it working!

doing a sudo apt-get build-dep wine before compiling did the trick and i got a proper opengl32.dll. smooth. 


so now the question is: how do i increase the performance, its a bitt laggy compared to how it was in winxp. sound and graphic not going with the flow needed for proper gameplay.

---

### Post by philth on 2006-03-20
Not sure if anyone else had this but i got an OPENGL.dll missing and corrected it with running ./configure --with-opengl instead of just ./configure

I an using  a nvidia card

---

### Post by illurim on 2006-03-20
Update [21-Mar-2006]: I removed my original installation of wine and reinstalled it from source compilation, as per the absolute letter of the instructions in the guide. Lesson learned.

Update [20-Mar-2006]: I read an earlier post in this thread that suggested a video driver update. I followed the directions from the link provided in that post, but still no dice.

Hi all,

Bit of a Linux newbie. Total Ubuntu newbie. But, doing my best to follow posts and directions, etc.

I have a similar problem to a previous poster (biggi_mati). Unfortunately, I don't have the where-with-all to figure out the rather arcane error messages, though I wish I did. That said, I'm hoping someone will be able to offer some assistance.

WoW was working wonderfully (in so far as I could tell) up until I patched to 1.9. I did a clean install of WoW. I got the logon screen, logged in, and got the patch message. I patched to 1.9 and now nothing loads.

The behaviour that I'm seeing is the screen seems to flicker very briefly, I see a "World of Warcraft" window in my window manager down the bottom of the screen, but then it disappears and I'm left with the following (error?) message:

```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c5d0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c5d0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0ee58,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  385
  Current serial number in output stream:  386


```If anyone can provide some assistance, I would be most grateful.

---

### Post by Shadou on 2006-03-20
[QUOTE=thieves.honor]if people are having problems getting the dependencies for wine, then one idea is to get auto-apt from the repositories.  

then run:
sudo auto-apt update
sudo auto-apt updatedb
sudo auto-apt update-local
sudo auto-apt run ./configure

it will go through, download and install all the dependencies that are needed.[/QUOTE]


I love you, thieves. I hope this works - looks promising.

---

### Post by jkeyes0 on 2006-03-20
I've got Ubuntu 5.10 on my Dell Inspiron 8600 laptop, copied WoW over from an existing installation (from the same laptop, separate hard drive, ironically enough), and got WoW to run. I logged in, saw my characters, everything was going well, and when I hit Enter World, the screen changed to the loading screen, the bar went across the bottom, and the screen became lighter, and lighter, until everything was white. Nothing would respond, so I rebooted, had to delete my /home/username/.ICEauthority file to actually get loaded, but no real problems.

I'm going to try one more time, but I don't have the best feeling about this. Anyone familiar with the screen going light and the system locking up?

EDIT: Nevermind. Not sure what I did exactly, but I removed -opengl from the launcher line, and it let me in. I exited, put the -opengl back in, and it works still. FPS are not great, but better than nothing. I might try it on my system at home at a later point (I have a spare hard drive for it too) to see if better hardware makes the difference. I have an ATI card in my laptop, and an ATI card in my desktop (X800 pro desktop, 9600 pro turbo in laptop).

EDIT 2: I think the problem may have had something to do with the "SET gxApi "opengl"" line in the wtf file. Well. maybe not.

---

### Post by jkeyes0 on 2006-03-20
Ok, I keep going back and forth. Sometimes it works, sometimes it doesn't. Any ideas?

Edit again: I think it has something to do with the resolution. I'm on a widescreen laptop, so I normally set it to 1280x800, but I told it to autodetect hardware (through the wtf file) and it set it to 1024x768 and worked. I then manually set it to 1280x768, and it still works, so I'm not going to question it. Could it have something to do with the monitor?

---

### Post by Goleta on 2006-03-20
May I suggest that [https://wiki.ubuntu.com/WorldofWarcraft](https://wiki.ubuntu.com/WorldofWarcraft) be substituted with this post. Seems like the original author of the wiki post quit. :)
> WARNING #2: This howto is no longer being maintained by it's original author, and hence it might no longer work with recent releases of WoW
This seems better and more complete. Will help future users find information. Thank you

---

### Post by Bluehill on 2006-03-20
Hi,
Thanks for making such a comprehensive and accurate guide for successfully installing WoW on Unbuntu. I, being a relative linux noob, was skeptical whether or not I would be able to handle such a daunting task. I had been using Ubuntu for some time and absolutely loved it and WoW was the only thing keeping me from completely uninstalling Windows XP. 

I follow your guide step by step, substituting the [latest Wine build ]("http://prdownloads.sourceforge.net/wine/wine-0.9.10.tar.bz2?download") for the one you used. Also, instead of installing from a previous windows installation or installation CD's I  was able to install using the [WoW trial client]("http://www.fileplanet.com/158404/download/World-of-Warcraft-Trial-%5BCLOSED%5D"). The trial period is closed, but if you have an existing account you can just install and enter your account information. I will add that I did receive installation error messages while patching WoW, but they can be ignored.

Everything works, including all in game video settings. I'm very pleased to say the least. I will add that it's important you follow the instructions on the first page precisely as missing one step can botch your installation and waste a lot of time (as I found out the hard way).

Needless to say Windows is no longer installed.:mrgreen: 

Cheers,

Bluehill

---

### Post by aqualad on 2006-03-21
ARGH! KILL ME!

New problem.  Thieve's method of using auto-apt seemed to be doing something, because I had sucessfully gotten through everything but the final command

```
sudo auto-apt run ./configure
```

I have found another problem with my installation.  Whenever it asks me to download and install something and I say yes, it goes through the process of downloading and then it seems to start installing, but always comes up with the same prompt/error:

This is towards the end of the process:

```
make: *** [/etc/selinux/./policy/policy.] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2

```

Then this is the final response before I must hit enter and go back to the other prompt.

```
Errors were encountered while processing:
 selinux-policy-default
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed [Z - exec shell to fix this situation]

```

So it looks like my problem is selinux-policy-default, so I went into PM and tried getting stuff for it, like the dev and tools and stuff, but they get this error in PM:

[quote=PackageManager]Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2[/quote]

I get the same error as above when I try to reinstall selinux-policy-default

I found the package manually but am unsure of how to install it without a ./configure, make depend && make, sudo make install  It has a file called Makefile though.

If there is anything I can do to fix this please help, this is all so very frustrating:evil:

---

### Post by illurim on 2006-03-21
Update [22-Mar-2006]: I have resolved the sound issue, though I'm not entirely sure how. I should have written down the settings I fiddled with, but the short of it is, I toyed around with the default sound device settings (switched from HA Intel to MUART - rebooted, switched again, fiddled with the volume control setting which allowed me to switch between 2 other settings and rebooted again and it worked fine after that. I'll try to post more detail when I get home from work and can actually list the proper settings.

Update [21-Mar-2006]: I managed to find a post elsewhere, unrelated to wine, but similar sort of error message and ran their fix:

```

mkdir -p $HOME/.kde/socket-`hostname`

```

It allowed me to use the Audio tab in winecfg and select options. Sound still didn't work properly with just OSS checked, so I ended up checking ALSA as well. Sound worked in the game then, but it's very jittery. There are also a few timing issues (i.e. I click on the auction house and the bell that dings comes up seconds after it should). Not a major drama, but still looking for any assistance toward resolving this one. I'll post back here with an update if I manage to resolve it.

Hi all,

I've now got my WoW installation working under Wine. However, I now suffer from a new problem, seemingly more related to Wine than WoW. I have no sound. However, when I go into the winecfg and click on Audio, Wine actually exits with the following:

```

Creating link /home/illurim/.kde/socket-erilaz.
can't create mcop directory

```

Which is odd, since I'm using gnome, not kde. I have no idea what it's trying to do or how to fix it. I've searched through the WineHQ site, but if there's something there, I can't find it. I did a search on google for the "can't create mcop directory" but very little that actually made sense to me exists.

Is anyone able to provide assistance, please?

---

### Post by tommyd on 2006-03-21
Hello.  I got the game working (wine 0.9.10/Breezy/Nvidia 5700).  Followed the tuturial to the T.  My problem is that the performance is awful when compared to windows.  This is one of the only reasons I even still have to use that evil OS.  Anyways.  I've looked around and always find posts with people having performance problems but never any answers.  My fps are significantly lower than windows and my mouse is really jerky (it is a logitech mx500 and I have used logitech_applet to set the dpi and everything).  Any help would be appreciated.

---

### Post by jkeyes0 on 2006-03-23
you know, I was really excited to get WoW working in linux as well, but my FPS is just crappy. I'm getting about 9fps on average (this is my laptop, with an ATI Radeon 9600 Mobility Pro Turbo card in it, if that matters...). I've got the ATi drivers set up appropriately (as far as I know).

Anyone have ideas on how to speed up the game in wine?

---

### Post by alinuxfan on 2006-03-23
i am not sure what I am getting for framerates but it is enough to play.  I'll log in and check here in a bit and see.

---

### Post by jkeyes0 on 2006-03-23
I may have found my problem. I ran glxgears to get my frames per second, and it was something like 100 - 140fps... as I've seen from others, it should be somewhere around 2000. Looks like I need to work harder on my video card / monitor settings.

---

### Post by alinuxfan on 2006-03-23
I am have told that glxgears isn't a good benchmark, but yeah your numbers should be above that.  
My fix was to install a nvidia card and now everything is smooth (It was a major upgrade that I needed to do anyway)
I just never had any luck with my ATI cards.   I know that probably isn't the option you are headed towards.  good luck getting your video card set up correctly

---

### Post by jkeyes0 on 2006-03-24
should the glxgears fps be done in fullscreen mode or not? When I'm not running it fullscreen, I get about 2500fps, but when it is fullscreen, it's 100fps. maybe that's the issue... I was doing it wrong?

---

### Post by larsemil on 2006-03-24
to me it sounds that all users with a aticard are the ones with crappy performance. is the atidriver really that bad?

---

### Post by Talikar on 2006-03-24
[QUOTE=larsemil]to me it sounds that all users with a aticard are the ones with crappy performance. is the atidriver really that bad?[/QUOTE]
Simple answer- Yes.

The ATi drivers suck. First off, their automatic installer will not "create" a configuration file if it is not already present. It only seems to reconfigure a pre-made one.

Second, it doesn't even do that properly, as most the settings inside disallow a normal user from using the drivers with Direct Rendering at all; at least it was the case for me.

Third, with it installed perfectly (or so one thinks) something seems busted. For example, Nexuiz is missing text, inside the game has nothing but a black screen... At least your gun shows.... Another example, Doom 3 is missing the menu itself. Not sure how to fix both, probably need to poke around the configuration file some more...

I don't see why they don't just port the windows drivers to linux instead of slowly making new drivers for linux. Unless of course they are porting them, in which case, how many people are working on the linux drivers? one? ~ Another reason the drivers are really bad; ati doesn't love linux.

---

### Post by Plastic Snake on 2006-03-24
Well, I've got the actual game running thanks to this Howto, but I have a rather large problem. I was on a wind rider when I logged last (on windows), and then I decided to switch over to linux. It worked fine as I was flying until I got to Orgrimmar, and then it promptly crashed. Now, whenever I try to log in, it crashes, making the game entirely unplayable. Any suggestions?

Edit: Realized I completely forgot the WoW patch for wine. Works perfectly now!

---

### Post by tommyd on 2006-03-25
Well, I installed the latest nVidia driver and my fps seem to be close to what I get in windows, but the feel of the pointer when using the mouse is jerky.  That is the biggest problem now.  That and sound.

---

### Post by jkeyes0 on 2006-03-25
Well, I've got Ubuntu on my desktop, and for some reason WoW with Wine runs just as poorly as it does on my laptop (desktop has an ATi Radeon X800 Pro, laptop has a 9600 Pro).

Frustrated, but not giving up. Anyone know any sneaky hints that will make this work?

---

### Post by erthian on 2006-03-25
[QUOTE=moccah]You can try to run 
```
 wine WoW.exe -d3d 
```

In my experience this will let you change Video settings in WoW.[/QUOTE]

I followed this guide, and i couldn't get my frame rate up at all, and it would crash with the memory error every one is getting.  

I ran it with -d3d and dropped down some settings, and its working great now.  I dont know what difference that made, but I can even put my settings back up now, and it still runs smooth.

I am running two monitors, and when I drag it from one to the other it still crashes on me, with the memory error.  I would like to figure out how to load a different xorg.conf file with just one monitor just for playing games.. hmm.

---

### Post by jhartford on 2006-03-26
How do you copy WoW into Linux from the Windows partition?

---

### Post by Grog140 on 2006-03-30
How on earth do I install this so Wine can run WoW?

When trying the cd's I get the insert disk thing, I have copied the cd's but the message still comes up and I dont know how I would make wine think it switched or something. I also have a installed WoW directory however I cannot run the WoW.exe with wine.

Please tell me what to do :)

---

### Post by ffadmraven on 2006-03-31
[QUOTE=Grog140]How on earth do I install this so Wine can run WoW?

When trying the cd's I get the insert disk thing, I have copied the cd's but the message still comes up and I dont know how I would make wine think it switched or something. I also have a installed WoW directory however I cannot run the WoW.exe with wine.

Please tell me what to do :)[/QUOTE]


Check to make sure the directx folder on disk one got copied to where you copied the cd's to, I had this same problem, and that was the cause.

---

### Post by justleen on 2006-03-31
[QUOTE=Grog140]How on earth do I install this so Wine can run WoW?

When trying the cd's I get the insert disk thing, I have copied the cd's but the message still comes up and I dont know how I would make wine think it switched or something. I also have a installed WoW directory however I cannot run the WoW.exe with wine.

Please tell me what to do :)[/QUOTE]

If you already have it installed, you can simply copy it over.
Make sure you have configured Wine as in Fist Post too.
Assuming you have it installed on a window dir (on hda1):
```

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
cp -Rv  /dev/hda1 /media/windows/Program \Files/World\ of\ Warcraft/ /home/username/.wine/drive_c/Program\ Files/

```
That will copy everything over, no need to install it under linux/wine again.

After this copy, make sure you have edited the /WTF/Config.cfg file according to First Post.. 


Once thats done, you can execute it with wine WoW.exe -opengl

---

### Post by Grog140 on 2006-03-31
Alright, I found the problem with getting it running, and it was running fine (the menue was at least) BUT!

I installed the patch 1.10 and now The majority of the visuals are just black except for the buttons, menu bars and minimap.

And I could see the visuals such as the gate in the beginning log in part before I updated.

---

### Post by cerebrix on 2006-04-01
a ton of things changed in the renderer.  its probobly going to take a couple of weeks to get wine's code adjusted to compensate for it.  patience my young undead priest, patience

---

### Post by Gizida on 2006-04-02
Anyone succeeded in making it work with a i810 chipset? I get ~500fps in glxgears (yes i know this is not a benchmark) and the game runs pretty smooyhly under windows. but with wine i get something like 1fps!!!
I use the ubuntu drivers wich come with dapper. Will installing the dri snapshots solve the problem?

---

### Post by pataphysician on 2006-04-05
EDIT: new problem.

when i run wine for the first time i get:

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:module:load_builtin_dll failed to load .so lib for builtin L"ddraw.dll": libSM.so.6: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
wine: '/home/mike/.wine' created successfully.

```

this happens when i run the mozillacontrol executable as well. is there a file i need to edit manually?

---

### Post by larsemil on 2006-04-05
[QUOTE=Grog140]Alright, I found the problem with getting it running, and it was running fine (the menue was at least) BUT!

I installed the patch 1.10 and now The majority of the visuals are just black except for the buttons, menu bars and minimap.

And I could see the visuals such as the gate in the beginning log in part before I updated.[/QUOTE]

1.10 works fine for me. its just crappy fps as usual. 

anyone wanna have my ati card? i change it for at nvidia.. :)

---

### Post by jkeyes0 on 2006-04-06
[QUOTE=pataphysician]EDIT: new problem.

when i run wine for the first time i get:

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:module:load_builtin_dll failed to load .so lib for builtin L"ddraw.dll": libSM.so.6: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
wine: '/home/mike/.wine' created successfully.

```

this happens when i run the mozillacontrol executable as well. is there a file i need to edit manually?[/QUOTE]



Try this:
```

sudo apt-get build-dep wine

```

---

### Post by jkeyes0 on 2006-04-06
sorry, double post...

---

### Post by pataphysician on 2006-04-06
[QUOTE=jkeyes0]Try this:
```

sudo apt-get build-dep wine

```[/QUOTE]

turns out that not only was wine not working, but x was broken entirely after the install ([http://ubuntuforums.org/showthread.php?t=155819)](http://ubuntuforums.org/showthread.php?t=155819)). ended up removing wine and, with the help of a user named bimberi in #ubuntu, got x working again. people keep telling me to check in /usr/lib for various files, but for me they always end up being in /usr/X11R6/lib. i'm guessing this is the problem. once i install wine the system expects things to be in /usr/lib like they are for everyone else. i'll continue to mess around with it and hope i don't hose the whole thing again. thanks for the reply!

---

### Post by Zer0d on 2006-04-06
This guide fixed my problems:
[http://appdb.winehq.org/appview.php?versionId=4031]("http://appdb.winehq.org/appview.php?versionId=4031")
If you have problems, give it a try ;)

---

### Post by Zer0d on 2006-04-07
What does these messages mean? Can some of them decrease the preformance, and howto fix?

```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c5d0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c5d0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbceedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6e8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf158,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wgl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
```

---

### Post by Frogzoo on 2006-04-08
From: [http://appdb.winehq.org/appview.php?versionId=4031](http://appdb.winehq.org/appview.php?versionId=4031).

"1.9.x In this patch Blizzard added the new raid Dungeon of Anhq'arai. Other features can be found here and details here

What works
Installing, playing.  Everything works in-game. Opengl/wgl.c do not need patching anymore, with CVS.  The game is almost playable without patches, once you've made the necessary changes in the game directory. "

Maybe update the front page to show that the glx patch isn't required from 0.9.9 onwards.

Also, perhaps mention a warning that prelink can break wine (it messes up ld-2.3.5.so). The fix is to remove prelink and reinstall linux-kernel-686 and initramfs-tools

There's a mention over at [http://appdb.winehq.org/appview.php?versionId=4031](http://appdb.winehq.org/appview.php?versionId=4031).
of new WoW patches

For 0.9.9, 0.9.10
[http://rapidshare.de/files/14329411/wow.new.patch.html](http://rapidshare.de/files/14329411/wow.new.patch.html)

For 0.9.11
[http://rapidshare.de/files/17077972/wow.patch.0.9.11.html](http://rapidshare.de/files/17077972/wow.patch.0.9.11.html)

---

### Post by Tea on 2006-04-09
Hi, I'm having some problems with WINE.

I'm using 0.9.6, and when I try to run "winecfg" or "wine (placeapphere)" I get this junk.

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

I have tried "sudo apt-get build-dep wine" with nothing coming out of it, but I had them all installed. 

Any Ideas?

EDIT: Ok, got around this by just using a normal installation of WINE< we'll see how it works later. Anyway, silly newb question here....

When it asked me to put in disk 2, what do I do? It dosent "see" that I put it in.

---

### Post by justleen on 2006-04-10
[QUOTE=Tea]
When it asked me to put in disk 2, what do I do? It dosent "see" that I put it in.[/QUOTE]


umount / mount the disk, wine will pick it up.

---

### Post by K-Zodron on 2006-04-10
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe" failed, status c0000135

I get that after I have dl:ed the patch of 350mb with blizzard downloader...I have MFC42.dll, MFC42.DLL, mfc42.dll in both /drive_c/windows/System32/ and .../system32

Whats wrong ? :X

---

### Post by justleen on 2006-04-11
[QUOTE=K-Zodron]err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe" failed, status c0000135

I get that after I have dl:ed the patch of 350mb with blizzard downloader...I have MFC42.dll, MFC42.DLL, mfc42.dll in both /drive_c/windows/System32/ and .../system32

Whats wrong ? :X[/QUOTE]

i assume oyu used the blizz downloader to dl the update? Once its finished downloading, quit the game, go to the /drive_c/prog files/WoW. you should see the patch file there
just run $wine wow-patch.xx.xx.exe   to update the game. once done start the game again as usual..

---

### Post by K-Zodron on 2006-04-11
```
****@ubuntu:~/Desktop$ wine WoW-1.10.0-enGB-patch.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe" failed, status c0000135
```


Thats exactly where I get this error :/ I don't get it, it is in System32 why doesn't it find it? :S

---

### Post by justleen on 2006-04-11
[QUOTE=K-Zodron]```
****@ubuntu:~/Desktop$ wine WoW-1.10.0-enGB-patch.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\BNUpdate.exe" failed, status c0000135
```


Thats exactly where I get this error :/ I don't get it, it is in System32 why doesn't it find it? :S[/QUOTE]


try coping the dll files in /windows/system too, so if that helps...
or, delete the files, and copy them again?

i had this once.. in the end i solved this by
```

$ mv .wine/drive_c/Prog files/WoW  /home/user/
$rm -rf .wine
$wine
$mv /home/user/wow .wine/drive_c/Prog files/
$cp *.dll .wine/drive_c/windows/system32

```

(if you move the wow dir, its instant, so you dont ghave to wait till it has moved the 4GB of data..as long as its on the same drive ofcourse)

---

### Post by K-Zodron on 2006-04-11
Yay, moved the mfc42.dll to .../system/ and the patcher started...lets see what error appears next, heh :P

Thanks!

---

### Post by Tea on 2006-04-11
Ok, got it installed, but I'm getting horrible FPS. Do I need to install new drivers for my video card? 

I have a highendish system, and I get 60 fps normally under windows. Thanks.

EDIT: Ok, I get past the login screen now, start loging in, and then everything goes black. I have a radeon x800xt pe coming from a fresh install. Oh, and at the login screen, the performance is still horrible.

---

### Post by justleen on 2006-04-12
[QUOTE=Tea]Ok, got it installed, but I'm getting horrible FPS. Do I need to install new drivers for my video card? 

I have a highendish system, and I get 60 fps normally under windows. Thanks.

EDIT: Ok, I get past the login screen now, start loging in, and then everything goes black. I have a radeon x800xt pe coming from a fresh install. Oh, and at the login screen, the performance is still horrible.[/QUOTE]

Depends what card you have? For Ati or Nvidia cards its best to install the drivers..

---

### Post by Tea on 2006-04-12
I have the flgrx drivers installed, and the card is an ATI Saphire X800XT PE (AGP). I can get up to 30fps when I run everthing on low in -d3d mode, but in -opengl it gets cut in half, not to mention that the game looks horrible, with grainy textures etc.

Also of note, when I load the game, and get a "Character with that name allready exists" message, the game suddenly slows to a crawl.

---

### Post by geeknation on 2006-04-12
I just followed the tutorial and got it working without any problems. Just updated my nVidia driver and it's looking quite good!:D

No more booting into Windows for me!

---

### Post by rorschach on 2006-04-12
[QUOTE=Tea]Hi, I'm having some problems with WINE.

I'm using 0.9.6, and when I try to run "winecfg" or "wine (placeapphere)" I get this junk.

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
[/QUOTE]

I have this exact issue when I try to follow the instructions on the winehq how-tonfor 0.9.11.
I am now going back through and double-checking each step
any ideas what caused the error?

---

### Post by rorschach on 2006-04-13
Well.
I went through and followed the steps presented on the WineHQ forum... unsuccessfully.

Everything *looks* fine... until I try to invoke winecfg. Then I get the error above (err:imagelist:ImageList_ReplaceIcon no color!), and no window pops up.
if I try to start the install for WoW - same thing, though I do hear the WoW sounds in the background (with no problems)

So - I'm guessing this is a display issue - anyone want to help?

---

### Post by Rakanishu on 2006-04-18
Hi.
I'm having some problems in the beginning of this guide.

I have completely uninstalled Wine through Synaptic.

I have checked in Synaptic that I hav the build-essential package.

But when I issue the command:
```
sudo apt-get build-dep wine
```
I get the message:
```
The build-depends cannot be satisfied because the package bicu-34.dev cannot be found.
```

Furthermore, when I try to extract the downloaded wine source, I get this message:
```
tar: This doesn't look like a tar archive
tar: Jumping to next header
tar: Read 1982 byte from wine-0.9.6.tar.bz2 
```

Plus, I get another error when I try to use the patches:
```
Can't find file to patch at input line 4
``` 
with the 
```
wine-cvs-glx.diff
```
and
```
Can't find file to patch at input line 3 with the 
wine-wow-fixes.patch
```

Very thankful for any help!

---

### Post by Rakanishu on 2006-04-18
I succeeded downloading and extracting a newer version of Wine, and I managed to patch it up.
But the problem with 'sudo apt-get build-dep wine' still remains.
The command line is telling me that it cannot find the package 'lib icu-34.dev'
I have checked for it in Synaptic and googled for it without any results.

Thanks for any help!

---

### Post by Caudata on 2006-04-19
I'm trying to install wine now after using the apt comman to build dependencies I recieved the following: 
[HTML] sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
Note, selecting libfontconfig1-dev instead of libfontconfig-dev
E: Build-dependencies for wine could not be satisfied. [/HTML]

Anyhoo I got annnoyed and tried doing it all manually and during the "make" process I had the following error:
[HTML] /home/caudata/downloads/wine/wine/dlls/x11drv/xim.c:576: undefined reference to `XCreateIC'
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/caudata/downloads/wine/wine/dlls/x11drv'
make[1]: *** [x11drv] Error 2
make[1]: Leaving directory `/home/caudata/downloads/wine/wine/dlls'
make: *** [dlls] Error 2 [/HTML]

Anyone have a clue what to do at this point in the build obviously I'm missing "winex11.drv.so". Any ideas what it is, or how to fix the problem. Thanks for any help, later!

---

### Post by Caudata on 2006-04-20
Just great I did a search for "winex11.drv.so" and at least found it, but as part of the WINE package in ubuntu. Though that really doesn't help me any. The search listed this as it's path: usr/lib/wine/winex11.drv.so. Oh well more searching.

---

### Post by K-Zodron on 2006-04-28
Aff...problems problems problems...

I get the error #132 when the agreement screen should appear =/ I have followed this tutorial 100% and it works fine with wine Wow.exe -d3d (Without textures, quite limited screensize, laggyyyy) 

I get the 2 first screens ("10 years of warcraft..." and the map pic~~), then it crashes :<

I get this into my command prompt (Before the crash I assume):

```

fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d620000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d620000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fafeef4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff460,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff170,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff668,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff668,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff668,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff668,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff654,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff170,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x10022): stub
wine-pthread: r200_swtcl.c:103: r200SetVertexFormat: Assertion `VB->AttribPtr[VERT_ATTRIB_POS] != ((void *)0)' failed.
fixme:dbghelp:sffip_cb NIY on 'C:\build\buildWoW\WoW\bin\Wow.pdb'
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

---

### Post by saxin on 2006-04-29
I have a problem with the mousebug in World of Warcraft, so I hope some of you can help me. I want to know if it's possible to edit a file or something that will fix the mousebug, instead of using the patches?

---

### Post by makisupa123 on 2006-04-30
Built a new deb, copied WoW from a XP installation, and got it running.  My FPS is about half of what i get in windows.  It is running in openGL mode.  25 as an average until spinning...then it goes down to about 15 or so.  Is there any tweaks that i haven't seen in any of these threads that will help?  Is there certian modules in xorg that need to be loaded that will help (of the top of my head i have GLcore, dri, and glx loaded).  


Using a nvidia 6600 256 mb, 1 GB ram, with a sempron 2800.  Like i said, in windows get about 45-50 with drops into the high 30's.  Any ideas?


Thanks,

Mak.

---

### Post by nazgum on 2006-05-02
[QUOTE=Caudata]Just great I did a search for "winex11.drv.so" and at least found it, but as part of the WINE package in ubuntu. Though that really doesn't help me any. The search listed this as it's path: usr/lib/wine/winex11.drv.so. Oh well more searching.[/QUOTE]

Installing xlibs-dev and libxft-dev from synaptic fixes this problem.

You should also install libxml2-dev, libxslt1-dev, libfreetype6-dev, fontforge **and any other x-libraries that show a 'no' when you do ./configure** if you don't have them.

Then re-run ./configure, make depend && make

edit:  added bold section

cheers.

---

### Post by kano on 2006-05-03
This thread inspired me to come back to Linux, after having to use Windows for the past year to play WoW. :)

Using a nvidia geforce3 ti500, wine 0.9.6 compiled with these patches under breezy my performance was quite a bit lower compared to windows. (avg. 10-15fps in zones where I was generally not near many other people)

Installed Dapper, (latest xorg, nvidia drivers) and built wine 0.9.9 using the patches linked in the first post and now I'm getting a solid 25-30fps even in crowded areas like IF. I've seen it jump up to 50fps inside buildings in IF, which never happened in windows.
My latency has also improved greatly, from 180-200ms avg in windows to 69-79ms in linux. 

Overall, the game plays better for me under Linux than it did in windows. Much kudos for kidcharles, excellent guide.  :KS

---

### Post by Mon on 2006-05-04
I was wondering if anyone here can play music through xmms/rhythmbox/whatever when playing WoW. I use Cedega, and well, i can't :(. WoW seems to need complete access to /dev/dsp, this means no esound daemon which my music player needs. Disabling esd in the media player and setting it to Alsa (just like Cedega) doesn't help either.
Can anyone confirm wine also has/doesn't have this problem?

Hmm i just read that you need a card which supports hardware mixing, such as a SB Live or Audigy. Does anyone have such a card? If you do, can you use wine + <insert favorite musicplayer> both over Alsa together?

---

### Post by glaze on 2006-05-05
[QUOTE=Mon]I was wondering if anyone here can play music through xmms/rhythmbox/whatever when playing WoW. I use Cedega, and well, i can't :(. WoW seems to need complete access to /dev/dsp, this means no esound daemon which my music player needs. Disabling esd in the media player and setting it to Alsa (just like Cedega) doesn't help either.
Can anyone confirm wine also has/doesn't have this problem?

Hmm i just read that you need a card which supports hardware mixing, such as a SB Live or Audigy. Does anyone have such a card? If you do, can you use wine + <insert favorite musicplayer> both over Alsa together?[/QUOTE]

I'm using SB Live! and listening to music while gaming works fine. Beep-media-player's output is set to ALSA.

---

### Post by Mon on 2006-05-06
[QUOTE=glaze]I'm using SB Live! and listening to music while gaming works fine. Beep-media-player's output is set to ALSA.[/QUOTE]

Thanks this was the reaction i hoped for. However a friend of mine also has a SB Live! but can't play music (yet) using Alsa. I hope he did something wrong.. I'm planning on buying a Live! this week if it should work.

Does this mean i can ditch ESD completely? Or does Gnome (and KDE) need a deamon to write audio to instead of just letting Alsa handle it?

---

### Post by mcletter on 2006-05-06
I followed all the steps, seemed to work great. Then installed WoW on another Windows computer and copied files over to this one, tried to run WoW with wine WoW.exe -opengl, and got this..

```
seth@ubuntu:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
wine: Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process, aborting
wine: Unimplemented function KERNEL32.dll.IsWow64Process called at address 0x5ed09ec5 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function KERNEL32.dll.IsWow64Process called in 32-bit code (0x7bebf246).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7bebf246 ESP:7faffbc4 EBP:7faffc1c EFLAGS:00200212(   - 00      - -IA1)
 EAX:5eda22da EBX:7bef41b0 ECX:7fd60020 EDX:7fdb7b10
 ESI:7faffbc4 EDI:00000001
Stack dump:
0x7faffbc4:  80000100 00000001 00000000 5ed09ec5
0x7faffbd4:  00000002 5eda2576 5eda22da 7fec2000
0x7faffbe4:  7faffc04 7beb209c 7fd60000 00000000
0x7faffbf4:  00000020 7bef41b0 7fce09a0 7f85ceae
0x7faffc04:  7faffc18 7beb216b 5edac720 00000000
0x7faffc14:  00000002 7fce09a0 7faffd74 5ed09ec5
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7bebf246 stub_entry_point+0x56(dll=0x5eda2576, name=0x5eda22da) [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:181] in ntdll (0x7bebf246)
fixme:dbghelp:sffip_cb NIY on 'opengl32.pdb'
  2 0x5ed09ec5 in opengl32 (+0x9ec5) (0x5ed09ec5)
  3 0x5ed0a366 EntryPoint+0x44 in opengl32 (0x5ed0a366)
  4 0x7bebf1e5 call_dll_entry_point+0x15 in ntdll (0x7bebf1e5)
  5 0x7bebff9a MODULE_InitDLL+0x13a [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:816] in ntdll (0x7bebff9a)
  6 0x7bec089c process_attach+0x9c [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:891] in ntdll (0x7bec089c)
  7 0x7bec0872 process_attach+0x72 [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:883] in ntdll (0x7bec0872)
  8 0x7bec2e05 LdrInitializeThunk+0x345(main_file=0x1c, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:2001] in ntdll (0x7bec2e05)
  9 0x7fcce53d start_process+0x8d(arg=0x0) [/home/seth/Apps/wine-0.9.6/dlls/kernel/process.c:1017] in kernel32 (0x7fcce53d)
  10 0xb7ee4c97 wine_switch_to_stack in libwine.so.1 (0xb7ee4c97)
0x7bebf246 stub_entry_point+0x56 [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:181] in ntdll: jmp     0x7bebf240 stub_entry_point+0x50 [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:181] in ntdll
181         for (;;) RtlRaiseException( &rec );
Modules:
Module  Address                 Debug info      Name (75 modules)
PE      0x00400000-00afd000     Deferred        wow
PE      0x10000000-10069000     Deferred        divxdecoder
PE      0x5ed00000-5edcc000     Export          opengl32
ELF     0x7be8b000-7bf00000     Stabs           ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e759000-7e7d0000     Deferred        winex11<elf>
  \-PE  0x7e770000-7e7d0000     \               winex11
PE      0x7e7d0000-7e7f2000     Deferred        glu32
ELF     0x7f0a5000-7f0d5000     Deferred        uxtheme<elf>
  \-PE  0x7f0b0000-7f0d5000     \               uxtheme
ELF     0x7f119000-7f122000     Deferred        libxcursor.so.1
ELF     0x7f135000-7f151000     Deferred        ximcp.so.2
ELF     0x7f151000-7f170000     Deferred        libexpat.so.1
ELF     0x7f170000-7f19e000     Deferred        libfontconfig.so.1
ELF     0x7f19e000-7f1b2000     Deferred        libz.so.1
ELF     0x7f1b2000-7f21c000     Deferred        libfreetype.so.6
ELF     0x7f21c000-7f240000     Deferred        msacm32<elf>
  \-PE  0x7f220000-7f240000     \               msacm32
PE      0x7f240000-7f2cf000     Deferred        fmod
ELF     0x7f2de000-7f35f000     Deferred        winmm<elf>
  \-PE  0x7f2f0000-7f35f000     \               winmm
ELF     0x7f35f000-7f37a000     Deferred        imm32<elf>
  \-PE  0x7f370000-7f37a000     \               imm32
ELF     0x7f37a000-7f43a000     Deferred        libx11.so.6
ELF     0x7f43a000-7f453000     Deferred        libice.so.6
ELF     0x7f453000-7f496000     Deferred        ddraw<elf>
  \-PE  0x7f470000-7f496000     \               ddraw
ELF     0x7f496000-7f4b0000     Deferred        crtdll<elf>
  \-PE  0x7f4a0000-7f4b0000     \               crtdll
ELF     0x7f4c2000-7f4eb000     Deferred        ws2_32<elf>
  \-PE  0x7f4d0000-7f4eb000     \               ws2_32
ELF     0x7f4eb000-7f504000     Deferred        wsock32<elf>
  \-PE  0x7f4f0000-7f504000     \               wsock32
ELF     0x7f504000-7f522000     Deferred        iphlpapi<elf>
  \-PE  0x7f510000-7f522000     \               iphlpapi
ELF     0x7f522000-7f569000     Deferred        rpcrt4<elf>
  \-PE  0x7f530000-7f569000     \               rpcrt4
ELF     0x7f569000-7f5f0000     Deferred        ole32<elf>
  \-PE  0x7f580000-7f5f0000     \               ole32
ELF     0x7f5f0000-7f646000     Deferred        shlwapi<elf>
  \-PE  0x7f600000-7f646000     \               shlwapi
ELF     0x7f646000-7f705000     Deferred        shell32<elf>
  \-PE  0x7f660000-7f705000     \               shell32
ELF     0x7f705000-7f741000     Deferred        advapi32<elf>
  \-PE  0x7f710000-7f741000     \               advapi32
ELF     0x7f741000-7f7c8000     Deferred        gdi32<elf>
  \-PE  0x7f750000-7f7c8000     \               gdi32
ELF     0x7f7c8000-7f8e1000     Deferred        user32<elf>
  \-PE  0x7f7e0000-7f8e1000     \               user32
ELF     0x7f8e1000-7f990000     Deferred        comctl32<elf>
  \-PE  0x7f8f0000-7f990000     \               comctl32
ELF     0x7f990000-7f9f0000     Deferred        msvcrt<elf>
  \-PE  0x7f9a0000-7f9f0000     \               msvcrt
ELF     0x7fb03000-7fb10000     Deferred        libxext.so.6
ELF     0x7fb11000-7fb19000     Deferred        libxrender.so.1
ELF     0x7fb19000-7fb1d000     Deferred        libxdmcp.so.6
ELF     0x7fc65000-7fd60000     Stabs           kernel32<elf>
  \-PE  0x7fc80000-7fd60000     \               kernel32
ELF     0x7fe70000-7fe73000     Deferred        libxrandr.so.2
ELF     0x7fe73000-7fe7a000     Deferred        libsm.so.6
ELF     0x7fe7a000-7fe85000     Deferred        libnss_files.so.2
ELF     0x7fe85000-7fe8f000     Deferred        libnss_nis.so.2
ELF     0x7fe8f000-7fea5000     Deferred        libnsl.so.1
ELF     0x7fea5000-7feaf000     Deferred        libnss_compat.so.2
ELF     0x7febc000-7fec0000     Deferred        libxfixes.so.3
ELF     0x7fec0000-7fec2000     Deferred        xlcutf8load.so.2
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7d9a000-b7d9e000     Deferred        libdl.so.2
ELF     0xb7d9e000-b7ecc000     Deferred        libc.so.6
ELF     0xb7ecd000-b7ee0000     Deferred        libpthread.so.0
ELF     0xb7ee0000-b7efa000     DIA             libwine.so.1
ELF     0xb7efa000-b7efd000     Deferred        libxau.so.6
ELF     0xb7f0f000-b7f25000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

```

---

### Post by FuzzBarber on 2006-05-07
Ok, im really new with using ubuntu. I know only few commands and i have had some problems with WoW. It starts with no problems, but after some time it gives this error: 

fixme:dbghelp:pool_alloc OOM
wine-pthread: storage.c:246: hash_table_init: Assertion `ht->buckets' failed.
wine: Unhandled page fault on write access to 0x00000ffc at address 0x7e6f1fc1 (thread 0010), starting debugger...
WineDbg starting on pid 0xf
Unhandled exception: page fault on write access to 0x00000ffc in 32-bit code (0x7e6f1fc1).

.. i have no idea what it means. Any help will be appreciated.

---

### Post by mcletter on 2006-05-08
Sorry, trying to bump the thread.. My problem is two posts up..

Please if anyone could help, I've run out of ideas.. Thanks

---

### Post by indigochild on 2006-05-08
[QUOTE=tezzarist]I can't get "sudo apt-get build-dep wine" working just comes with this:

```
sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine

```
[/QUOTE]

I had this same problem.. it is just not having the proper repositories searched by apt.  Adding the wine repositories directly through synaptic didnt work for me (it couldnt download the repo headers).

Just add the following lines to /etc/apt/sources.lis

( Edited snippet with the proper repo's)

For Ubuntu Dapper (6.06):
```

deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

```

For Ubuntu Breezy (5.10):
```

deb http://wine.budgetdedicated.com/apt breezy main
deb-src http://wine.budgetdedicated.com/apt breezy main

```

then call 'sudo apt-get update' to refresh your repository listings.

After that, 'sudo apt-get build-dep wine' worked for me.

---

### Post by mhearn on 2006-05-09
[QUOTE=mcletter]
Backtrace:
=>1 0x7bebf246 stub_entry_point+0x56(dll=0x5eda2576, name=0x5eda22da) [/home/seth/Apps/wine-0.9.6/dlls/ntdll/loader.c:181] in ntdll (0x7bebf246)
fixme:dbghelp:sffip_cb NIY on 'opengl32.pdb'
  2 0x5ed09ec5 in opengl32 (+0x9ec5) (0x5ed09ec5)
[/QUOTE]

Don't use an opengl32.dll from Windows, you must use the Wine builtin copy.

> 
fixme:dbghelp pool_alloc OOM
wine-pthread: storage.c:246: hash_table_init: Assertion `ht->buckets' failed.
wine: Unhandled page fault on write access to 0x00000ffc at address 0x7e6f1fc1 (thread 0010), starting debugger...


You ran out of memory whilst WoW was performing an anti-reverse-engineering scan. This is probably a bug in Wine or WoW itself, but might simply be due to you not having enough memory. Unload some apps and try again.

-mike

---

### Post by Peetke on 2006-05-09
indigochild:

```
deb http://wine.budgetdedicated.com/apt breezy main
```
Or Dapper:
```
deb http://wine.budgetdedicated.com/apt dapper main
```

See: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by mcletter on 2006-05-10
[QUOTE=mhearn]Don't use an opengl32.dll from Windows, you must use the Wine builtin copy.



You ran out of memory whilst WoW was performing an anti-reverse-engineering scan. This is probably a bug in Wine or WoW itself, but might simply be due to you not having enough memory. Unload some apps and try again.

-mike[/QUOTE]

Hmm, Seems like a bug in Wine to me, I've got a gig of ram and was only running firefox and gAIM at the time, but I will try that too. THanks :)

Will post after I give it a shot.

---

### Post by The Only Joey on 2006-05-12
Hey,

i have a little question.
Can someone make a wine package with the mouse patch applied?
Im not that great with compiling and patching.

Thanks!

---

### Post by Technoviking on 2006-05-13
Wine 0.9.13 is out, anyone know if it is patched for WoW.

---

### Post by Rody on 2006-05-13
i hope so i have the issue that i cant select anything with my mouse, and the "apt-get build-dep wine"  
0 upgraded, 123 newly installed, 0 to remove and 0 not upgraded.
E: Package libicu28-dev has no installation candidate
E: Failed to process build dependencies

I will figure a way around this eventualy but it may take a while. I have been away from linux for about 5-6 years and some things have changed alot and others seem to have stayed the same.

MSI dimond plus
Gforce 7800 512mb
2ghz ram
sblive 5.1
lots of storage.
Dapper 6.06 beta.

---

### Post by YokoZar on 2006-05-13
[QUOTE=Rody]i hope so i have the issue that i cant select anything with my mouse, and the "apt-get build-dep wine"  
0 upgraded, 123 newly installed, 0 to remove and 0 not upgraded.
E: Package libicu28-dev has no installation candidate
E: Failed to process build dependencies

I will figure a way around this eventualy but it may take a while. I have been away from linux for about 5-6 years and some things have changed alot and others seem to have stayed the same.

MSI dimond plus
Gforce 7800 512mb
2ghz ram
sblive 5.1
lots of storage.
Dapper 6.06 beta.[/QUOTE]
You're using the obsolete apt repository: [http://ubuntuforums.org/showthread.php?t=172648](http://ubuntuforums.org/showthread.php?t=172648)

---

### Post by Rody on 2006-05-14
Thanks. i figured that out about 5 minutes after i posted.

rody

---

### Post by Rody on 2006-05-14
I just finished compiling it and loaded it up... It is not patched for wow and for some reason it wanted to put my sound files in /.kde very odd. I am very new to this so i am gona stumble along. I am compiling 0.9.12 with wow patch now, we will see how it works.

rody

---

### Post by Alexeon Lanar on 2006-05-14
I was about to install wine, but decided against it (after all, I already have windows on my PC.) Problem is that I decided this after I ran apt-get build-dep wine....

How can I erase those files from my PC?
I dont want to try erasing it myself since I dont want to do something dumb and erase important files.

---

### Post by unknownclient on 2006-05-14
I just wanted to post my experience with wine and wow. I had wow running under wine 9.6 then switched back to winblows. Recently I moved back to ubuntu. I was unable to get wow 1.10.x to work with wine 9.6. I used the how to on the winehq site and this thread to get wow working again. First I used wine 10 with the patch from winehq. I applied the patch and compiled and installed wine. Second before running wine, I made the file ld.so.conf and ran the command this how to instructs you to do. Then I ran wine and it created the .wine folder. I placed the dll files in system32 and then ran Mozilla control under wine. I copied the tome files from the cds onto my hard drive and ran the install off my hard drive. Then I downloaded and installed the update from fileplanet.com. I changed my wtf in the wow directory to what this how to suggests. But I found that the "set=glxopengl" made the game run slower. Right now I am getting an average of 36 FPS in IF or SW.  Long live the Linux OS!!

---

### Post by Rody on 2006-05-16
[QUOTE=unknownclient] But I found that the "set=glxopengl" made the game run slower. Right now I am getting an average of 36 FPS in IF or SW.  Long live the Linux OS!![/QUOTE]


SET gxApi "opengl"

i think is the correct option, unless i am looking in the wrong spot.

---

### Post by saxin on 2006-05-16
I have installed World of Warcraft with help from this guide. I have one problem that I hope you can help me with. When I try to start the game with wine WoW.exe -opengl I get this message: 

"World of Warcraft was unable to start up 3D acceleration."

I guess it have something to do with my xorg.conf file, but I'm not sure what it is, or even if this file is configured wrong. 
This problem is not happening everytime I try. If I reboot, I can generally play. But if I try to start the game some hours after I logged in, I can't.

Here is my xorg.conf file:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"H750"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"H750"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Alexeon Lanar on 2006-05-17
I know I already asked this, but what command do I put on the terminal to erase all the files downloaded by sudo apt-get build-dep wine?
I decided I didnt want wine because I am running out of space, and dont really need it. Please help me.

---

### Post by Grog140 on 2006-05-21
Is there anything that will install the correct dependencies for wine in dapper?

"sudo apt-get build-dep wine" doesn't work.

---

### Post by Rody on 2006-05-21
The WineHQ APT repository at sourceforge is now officially obsolete - it was slow, would time out frequently, and could only handle one version of a package at a time.

If you have added one of the following lines in your /etc/apt/sources.list, you need to remove it:

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/

Instead, use one of the following two lines:

For Ubuntu Dapper (6.06):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

For Ubuntu Breezy (5.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main

Budgetdedicated.com has nicely provided us with the new APT repository, which has a ton of bandwidth and allows for different distributions, as well as more obvious upgrading (to go from breezy to dapper, simply change the word breezy to dapper just as you would with the official repositories).

These instrusctions are also available at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

If you have any Wine-related questions, feel free to post them here. It would also be nice if this thread were stickied.
YokoZar is offline Report Bad Post   	Reply With Quote Quick reply to this message Multi-Quote with this Post

---

### Post by wmoshier on 2006-05-21
I am running into this problem:

~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\windows\\system32\\GLU32.dll") not found
err:module:import_dll Library GLU32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135
[email]david@david-laptop:~/.wine[/email]/drive_c/Program Files/World of Warcraft$ wine WoW.exe
wine: Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process, aborting
wine: Unimplemented function KERNEL32.dll.IsWow64Process called at address 0x5ed09ec5 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function KERNEL32.dll.IsWow64Process called in 32-bit code (0x7ff97f27).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7ff97f27 ESP:7fb9fb10 EBP:7fb9fb74 EFLAGS:00000212(   - 00      - -IA1)
 EAX:5eda22da EBX:7ffd52a4 ECX:7fcf0020 EDX:00000000
 ESI:7fb9fb1c EDI:00000001
Stack dump:
0x7fb9fb10:  00000002 7fb9fb54 7fc7dcc1 80000100
0x7fb9fb20:  00000001 00000000 5ed09ec5 00000002
0x7fb9fb30:  5eda2576 5eda22da 7fcf0000 00000000
0x7fb9fb40:  00000020 7ffd52a4 7fc6ec45 00000001
0x7fb9fb50:  7fb9fb70 7ff8945b 5edac720 00000000
0x7fb9fb60:  00000000 00060000 00102000 00000002
Backtrace:
=>1 0x7ff97f27 stub_entry_point+0x4c(dll=0x5eda2576, name=0x5eda22da) [/home/david/downloads/wine/dlls/ntdll/loader.c:184] in ntdll (0x7ff97f27)
  2 0x5ed09ec5 in opengl32 (+0x9ec5) (0x5ed09ec5)
  3 0x5ed0a366 in opengl32 (+0xa366) (0x5ed0a366)
  4 0x7ff97ed5 call_dll_entry_point+0x15 in ntdll (0x7ff97ed5)
  5 0x7ff993c8 MODULE_InitDLL+0x167(wm=<register not in topmost frame>) [/home/david/downloads/wine/dlls/ntdll/loader.c:826] in ntdll (0x7ff993c8)
  6 0x7ff996ba process_attach+0x98(wm=<register not in topmost frame>) [/home/david/downloads/wine/dlls/ntdll/loader.c:901] in ntdll (0x7ff996ba)
  7 0x7ff9968e process_attach+0x6c(wm=<register not in topmost frame>) [/home/david/downloads/wine/dlls/ntdll/loader.c:893] in ntdll (0x7ff9968e)
  8 0x7ff9c647 LdrInitializeThunk+0x372(unknown1=0x0, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/david/downloads/wine/dlls/ntdll/loader.c:2142] in ntdll (0x7ff9c647)
  9 0x7fc5b77b start_process+0xaf(arg=0x0) [/home/david/downloads/wine/dlls/kernel/process.c:820] in kernel32 (0x7fc5b77b)
  10 0xb7edf2e3 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7edf2e3)
0x7ff97f27 stub_entry_point+0x4c [/home/david/downloads/wine/dlls/ntdll/loader.c:184] in ntdll: subl    $4,%esp
184         for (;;) RtlRaiseException( &rec );
Modules:
Module  Address                 Debug info      Name (65 modules)
PE      0x00400000-00afd000     Deferred        wow
PE      0x10000000-10069000     Deferred        divxdecoder
PE      0x5ed00000-5edcc000     Export          opengl32
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7e7d0000-7e7f2000     Deferred        glu32
ELF     0x7f1a1000-7f1d2000     Deferred        uxtheme<elf>
  \-PE  0x7f1b0000-7f1d2000     \               uxtheme
ELF     0x7f1d2000-7f24a000     Deferred        winex11<elf>
  \-PE  0x7f1e0000-7f24a000     \               winex11
ELF     0x7f24a000-7f270000     Deferred        msacm32<elf>
  \-PE  0x7f250000-7f270000     \               msacm32
PE      0x7f270000-7f2ff000     Deferred        fmod
ELF     0x7f300000-7f308000     Deferred        libxrender.so.1
ELF     0x7f308000-7f390000     Deferred        winmm<elf>
  \-PE  0x7f310000-7f390000     \               winmm
ELF     0x7f390000-7f3ac000     Deferred        imm32<elf>
  \-PE  0x7f3a0000-7f3ac000     \               imm32
ELF     0x7f3ac000-7f492000     Deferred        libx11.so.6
ELF     0x7f492000-7f4d6000     Deferred        ddraw<elf>
  \-PE  0x7f4b0000-7f4d6000     \               ddraw
ELF     0x7f4d6000-7f4f0000     Deferred        crtdll<elf>
  \-PE  0x7f4e0000-7f4f0000     \               crtdll
ELF     0x7f503000-7f52d000     Deferred        ws2_32<elf>
  \-PE  0x7f510000-7f52d000     \               ws2_32
ELF     0x7f52d000-7f547000     Deferred        wsock32<elf>
  \-PE  0x7f530000-7f547000     \               wsock32
ELF     0x7f547000-7f566000     Deferred        iphlpapi<elf>
  \-PE  0x7f550000-7f566000     \               iphlpapi
ELF     0x7f566000-7f5b2000     Deferred        rpcrt4<elf>
  \-PE  0x7f580000-7f5b2000     \               rpcrt4
ELF     0x7f5b2000-7f647000     Deferred        ole32<elf>
  \-PE  0x7f5d0000-7f647000     \               ole32
ELF     0x7f647000-7f6a3000     Deferred        shlwapi<elf>
  \-PE  0x7f660000-7f6a3000     \               shlwapi
ELF     0x7f6a3000-7f780000     Deferred        shell32<elf>
  \-PE  0x7f6c0000-7f780000     \               shell32
ELF     0x7f780000-7f7c1000     Deferred        advapi32<elf>
  \-PE  0x7f790000-7f7c1000     \               advapi32
ELF     0x7f7c1000-7f841000     Deferred        gdi32<elf>
  \-PE  0x7f7d0000-7f841000     \               gdi32
ELF     0x7f841000-7f96e000     Deferred        user32<elf>
  \-PE  0x7f860000-7f96e000     \               user32
ELF     0x7f96e000-7fa2f000     Deferred        comctl32<elf>
  \-PE  0x7f980000-7fa2f000     \               comctl32
ELF     0x7fa2f000-7fa90000     Deferred        msvcrt<elf>
  \-PE  0x7fa40000-7fa90000     \               msvcrt
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb3000-7fbbc000     Deferred        libxcursor.so.1
ELF     0x7fbef000-7fcf0000     Stabs           kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe02000-7fe06000     Deferred        libxfixes.so.3
ELF     0x7fe06000-7fe09000     Deferred        libxau.so.6
ELF     0x7fe09000-7fe13000     Deferred        libnss_files.so.2
ELF     0x7fe13000-7fe1c000     Deferred        libnss_nis.so.2
ELF     0x7fe1c000-7fe31000     Deferred        libnsl.so.1
ELF     0x7fe31000-7fe3a000     Deferred        libnss_compat.so.2
ELF     0x7fe4a000-7fe6c000     Deferred        libm.so.6
ELF     0x7fe6c000-7ff62000     Deferred        libwine_unicode.so.1
ELF     0x7ff62000-7ffe0000     Stabs           ntdll<elf>
  \-PE  0x7ff70000-7ffe0000     \               ntdll
ELF     0xb7d89000-b7d8c000     Deferred        libdl.so.2
ELF     0xb7d8c000-b7ebb000     Deferred        libc.so.6
ELF     0xb7ebb000-b7ecd000     Deferred        libpthread.so.0
ELF     0xb7eda000-b7ef4000     DIA             libwine.so.1
ELF     0xb7ef7000-b7f0d000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        00000009    0 <==


PLEASE help. I am at a loss for what to do now.

---

### Post by Grog140 on 2006-05-21
Alright, I have wine installed in dapper now.

But World of Warcraft is running as if my graphics card isn't installed (which it is)

I am thinking its a dapper problem because I had it working in breezy.

---

### Post by Grog140 on 2006-05-22
I have figured out what my problem is. I installed the nvidia-glx driver properly but when I do a "glxinfo | grep rendering" it says I do not have direct rendering. Where in breezy I did.

Really the only thing thats different is that I have XGL/compiz installed. But Iam positive that the drivers are installed.

](*,)

---

### Post by cjdaweasel on 2006-05-24
I keep getting this whenever I run WoW.

[B]root@Whatever:~/.wine/drive_c/wow# wine WoW.exe -opengl
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff26c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fafeef8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff704,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff704,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff6a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff68c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fafee74,0x00000000), stub![/B]

It has a small pop up window as well that says "Your 3D accelerator card is not supported by World of Warcraft. Please install a 3D accelerator card with dual-TMU support." Thing about this is, I have had WoW running on this video card in windows. Works quite well actually. Any thoughts?

---

### Post by Andrew-buntu on 2006-05-24
[QUOTE=Grog140]I have figured out what my problem is. I installed the nvidia-glx driver properly but when I do a "glxinfo | grep rendering" it says I do not have direct rendering. Where in breezy I did.

Really the only thing thats different is that I have XGL/compiz installed. But Iam positive that the drivers are installed.

](*,)[/QUOTE]

XGL uses a different OpenGL library than the nvidia/ati ones (the mesa libraries) so you can't get direct rendering while running XGL.  So you can't play WoW.  Just start it up in a new Xserver that has direct rendering (use xinit) and you'll be fine.
I followed instructions I found on this forum to set up an XGL session through GDM so I can choose XGL or plain ol' Xorg when I log in.  That's another way you can play WoW and use XGL.

---

### Post by GIBson3 on 2006-05-26
So wine 0.9.7 worked well (minus the no ingame object interaction, even after the patch to "fix it")

From the Above mentioned Repo's I installed 0.9.13, Now when I run I get a black wine Window, with the WoW "ui" controlls flickering, but the Background with the Dark-Portal scene isn't showing...  The Console is telling me...

```

sean@edge:~/c/Program Files/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c260000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c260000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fafeedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7faff158,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wgl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
sean@edge:~/c/Program Files/World of Warcraft$

```

The System is 
Pentium 3 1.0ghz
512 MB Ram
Geforce 3 64meg
Breezy...

(it's sad that WoW runs as good in Breezy on 1/2 the hardware as it does on my windows p4 2.4 +1 gig + GF4 ti-4600)

~Sean

---

### Post by jsmtech on 2006-05-26
I am interested in learning more about WINE. Does anyone know how to get age of empire 2 working with WINE?

---

### Post by iamhowdy on 2006-05-27
[QUOTE=GIBson3]So wine 0.9.7 worked well (minus the no ingame object interaction, even after the patch to "fix it")

From the Above mentioned Repo's I installed 0.9.13, Now when I run I get a black wine Window, with the WoW "ui" controlls flickering, but the Background with the Dark-Portal scene isn't showing...  The Console is telling me...

```

sean@edge:~/c/Program Files/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c260000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c260000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fafeedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faff63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7faff158,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wgl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
sean@edge:~/c/Program Files/World of Warcraft$

```

The System is 
Pentium 3 1.0ghz
512 MB Ram
Geforce 3 64meg
Breezy...

(it's sad that WoW runs as good in Breezy on 1/2 the hardware as it does on my windows p4 2.4 +1 gig + GF4 ti-4600)

~Sean[/QUOTE]

Run: wine WoW.exe -opengl
Wine doesn't work so well with Direct3D rendering in WoW yet.

---

### Post by GIBson3 on 2006-05-27
[QUOTE=iamhowdy]Run: wine WoW.exe -opengl
Wine doesn't work so well with Direct3D rendering in WoW yet.[/QUOTE]

opengl is specified in my config.wtf it's worked Fine until 0.9.13 from the Repo....

---

### Post by Joetheodd on 2006-05-30
I'm having trouble running WoW (hm, seems we all are). I didn't configure with opengl (oops) and so I just downloaded opengl.dll and glu32.dll. Now I get this:

```
joe@foobar:~/.wine/drive_c/Program Files/World of Warcraft $ wine WoW -d3d
wine: Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process, aborting
wine: Unimplemented function KERNEL32.dll.IsWow64Process called at address 0x5ed09ec5 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function KERNEL32.dll.IsWow64Process called in 32-bit code (0x7bebb178).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7bebb178 ESP:7fb1fba8 EBP:7fb1fc00 EFLAGS:00000202(   - 00      - - I1)
 EAX:5eda22da EBX:7befd134 ECX:7fd90020 EDX:00000050
 ESI:7fb1fba8 EDI:00000001
Stack dump:
0x7fb1fba8:  80000100 00000001 00000000 5ed09ec5
0x7fb1fbb8:  00000002 5eda2576 5eda22da 7fb1fbe8
0x7fb1fbc8:  7f865e91 7fd90000 00000002 00000020
0x7fb1fbd8:  7fee4000 7befd134 7fd0cee0 00000001
0x7fb1fbe8:  7fb1fbfc 7beac635 5edac720 00000000
0x7fb1fbf8:  00000002 7fd0cee0 7fb1fd58 5ed09ec5
Backtrace:
=>1 0x7bebb178 stub_entry_point(dll=0x5eda2576, name=0x5eda22da) [loader.c:181] in ntdll (0x7bebb178)
fixme:dbghelp:sffip_cb NIY on 'opengl32.pdb'
  2 0x5ed09ec5 in opengl32 (+0x9ec5) (0x5ed09ec5)
  3 0x5ed0a366 EntryPoint+0x44 in opengl32 (0x5ed0a366)
  4 0x7bebb115 call_dll_entry_point+0x15 in ntdll (0x7bebb115)
  5 0x7bebc709 MODULE_InitDLL+0x99(wm=0x7fd91030, reason=0x1, lpReserved=0x1) [/home/joe/wine-0.9.6/dlls/ntdll/loader.c:821] in ntdll (0x7bebc709)
  6 0x7bebc99e process_attach(wm=0x7fd91030, lpReserved=0x1) [/home/joe/wine-0.9.6/dlls/ntdll/loader.c:891] in ntdll (0x7bebc99e)
  7 0x7bebcab5 process_attach+0x1c5(wm=0x7fd904f8, lpReserved=0x1) [/home/joe/wine-0.9.6/dlls/ntdll/loader.c:883] in ntdll (0x7bebcab5)
  8 0x7bebf31c LdrInitializeThunk+0x1dc(main_file=0x1c, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/joe/wine-0.9.6/dlls/ntdll/loader.c:2001] in ntdll (0x7bebf31c)
  9 0x7fcf8d9b start_process+0xbb(arg=0x0) [/home/joe/wine-0.9.6/dlls/kernel/process.c:1017] in kernel32 (0x7fcf8d9b)
  10 0xb7ecb28b wine_switch_to_stack in libwine.so.1 (0xb7ecb28b)
0x7bebb178 stub_entry_point+0x58 [loader.c:181] in ntdll: subl  $4,%esp
Unable to open file 'loader.c'
Modules:
Module  Address                 Debug info      Name (71 modules)
PE      0x00400000-00acd000     Deferred        wow
PE      0x10000000-10069000     Deferred        divxdecoder
PE      0x5ed00000-5edcc000     Export          opengl32
PE      0x68b20000-68b40000     Deferred        glu32
ELF     0x7be85000-7bf00000     Stabs           ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7f0c1000-7f0f3000     Deferred        uxtheme<elf>
  \-PE  0x7f0d0000-7f0f3000     \               uxtheme
ELF     0x7f0f3000-7f0fc000     Deferred        libxcursor.so.1
ELF     0x7f108000-7f124000     Deferred        ximcp.so.2
ELF     0x7f124000-7f1a4000     Deferred        winex11<elf>
  \-PE  0x7f130000-7f1a4000     \               winex11
ELF     0x7f1a4000-7f1c3000     Deferred        mpr<elf>
  \-PE  0x7f1b0000-7f1c3000     \               mpr
ELF     0x7f1c3000-7f209000     Deferred        wininet<elf>
  \-PE  0x7f1d0000-7f209000     \               wininet
ELF     0x7f209000-7f230000     Deferred        msacm32<elf>
  \-PE  0x7f210000-7f230000     \               msacm32
PE      0x7f230000-7f2c0000     Deferred        fmod
ELF     0x7f2c8000-7f34d000     Deferred        winmm<elf>
  \-PE  0x7f2d0000-7f34d000     \               winmm
ELF     0x7f34d000-7f36a000     Deferred        imm32<elf>
  \-PE  0x7f350000-7f36a000     \               imm32
ELF     0x7f36a000-7f42a000     Deferred        libx11.so.6
ELF     0x7f42a000-7f470000     Deferred        ddraw<elf>
  \-PE  0x7f440000-7f470000     \               ddraw
ELF     0x7f489000-7f4b3000     Deferred        ws2_32<elf>
  \-PE  0x7f490000-7f4b3000     \               ws2_32
ELF     0x7f4b3000-7f4cd000     Deferred        wsock32<elf>
  \-PE  0x7f4c0000-7f4cd000     \               wsock32
ELF     0x7f4cd000-7f4eb000     Deferred        iphlpapi<elf>
  \-PE  0x7f4d0000-7f4eb000     \               iphlpapi
ELF     0x7f4eb000-7f535000     Deferred        rpcrt4<elf>
  \-PE  0x7f500000-7f535000     \               rpcrt4
ELF     0x7f535000-7f5ca000     Deferred        ole32<elf>
  \-PE  0x7f550000-7f5ca000     \               ole32
ELF     0x7f5ca000-7f627000     Deferred        shlwapi<elf>
  \-PE  0x7f5e0000-7f627000     \               shlwapi
ELF     0x7f627000-7f6f7000     Deferred        shell32<elf>
  \-PE  0x7f640000-7f6f7000     \               shell32
ELF     0x7f6f7000-7f737000     Deferred        advapi32<elf>
  \-PE  0x7f700000-7f737000     \               advapi32
ELF     0x7f737000-7f7ba000     Deferred        gdi32<elf>
  \-PE  0x7f750000-7f7ba000     \               gdi32
ELF     0x7f7ba000-7f8eb000     Deferred        user32<elf>
  \-PE  0x7f7d0000-7f8eb000     \               user32
ELF     0x7f8eb000-7f9af000     Deferred        comctl32<elf>
  \-PE  0x7f8f0000-7f9af000     \               comctl32
ELF     0x7f9af000-7fa10000     Deferred        msvcrt<elf>
  \-PE  0x7f9c0000-7fa10000     \               msvcrt
ELF     0x7fb23000-7fb30000     Deferred        libxext.so.6
ELF     0x7fb32000-7fb36000     Deferred        libxfixes.so.3
ELF     0x7fc89000-7fd90000     Stabs           kernel32<elf>
  \-PE  0x7fca0000-7fd90000     \               kernel32
ELF     0x7fea0000-7fea4000     Deferred        libxdmcp.so.6
ELF     0x7fea4000-7fea7000     Deferred        libxau.so.6
ELF     0x7fea7000-7feb1000     Deferred        libnss_files.so.2
ELF     0x7feb1000-7feba000     Deferred        libnss_nis.so.2
ELF     0x7feba000-7fecf000     Deferred        libnsl.so.1
ELF     0x7fecf000-7fed8000     Deferred        libnss_compat.so.2
ELF     0x7fed9000-7fee1000     Deferred        libxrender.so.1
ELF     0x7fee1000-7fee4000     Deferred        xlcdef.so.2
ELF     0x7fee6000-7fee8000     Deferred        iso8859-1.so
ELF     0x7fee8000-7ff0a000     Deferred        libm.so.6
ELF     0x7ff0a000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7d82000-b7d85000     Deferred        libdl.so.2
ELF     0xb7d85000-b7eb3000     Deferred        libc.so.6
ELF     0xb7eb4000-b7ec6000     Deferred        libpthread.so.0
ELF     0xb7ec6000-b7ee0000     DIA             libwine.so.1
ELF     0xb7eef000-b7f05000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
```

Any takers?

---

### Post by eqisow on 2006-05-30
Are you guys that are having problems compiling Wine yourself? There are patches that are needed to be able to run WoW in Wine, so it is necessary to do this.

If you are compiling it yourself, are you following the instructions on this thread? If so, they are quite dated. Up-to-date instructions for compiling Wine can be found on the wiki, [here]("https://wiki.ubuntu.com/BuildingWineFromSource").

If you are running Dapper, I have built a pre-patched debian package that you can use instead. You can find that [here]("https://wiki.ubuntu.com/Wine") under "Latest version of Wine with WoW patch".

Also, as another poster said, there are issues running 3D applications while XGL is running.

Edit: I recomend changing this thread to redirect to the [World of Warcraft]("https://wiki.ubuntu.com/WorldofWarcraft") page on the wiki.

---

### Post by GIBson3 on 2006-05-30
[QUOTE=eqisow]Are you guys that are having problems compiling Wine yourself? There are patches that are needed to be able to run WoW in Wine, so it is necessary to do this.

If you are compiling it yourself, are you following the instructions on this thread? If so, they are quite dated. Up-to-date instructions for compiling Wine can be found on the wiki, [here]("https://wiki.ubuntu.com/BuildingWineFromSource").

If you are running Dapper, I have built a pre-patched debian package that you can use instead. You can find that [here]("https://wiki.ubuntu.com/Wine") under "Latest version of Wine with WoW patch".

Also, as another poster said, there are issues running 3D applications while XGL is running.

Edit: I recomend changing this thread to redirect to the [World of Warcraft]("https://wiki.ubuntu.com/WorldofWarcraft") page on the wiki.[/QUOTE]

Aye, Built from source (and patched) and it works fine, I made the mistake of thinking that since the Repo was listed in a Forum about wow that the Binary was built with said patch, I was mistaken...

---

### Post by Joetheodd on 2006-05-30
[QUOTE=eqisow]Are you guys that are having problems compiling Wine yourself? There are patches that are needed to be able to run WoW in Wine, so it is necessary to do this.

If you are compiling it yourself, are you following the instructions on this thread? If so, they are quite dated. Up-to-date instructions for compiling Wine can be found on the wiki, [here]("https://wiki.ubuntu.com/BuildingWineFromSource").

If you are running Dapper, I have built a pre-patched debian package that you can use instead. You can find that [here]("https://wiki.ubuntu.com/Wine") under "Latest version of Wine with WoW patch".

Also, as another poster said, there are issues running 3D applications while XGL is running.

Edit: I recomend changing this thread to redirect to the [World of Warcraft]("https://wiki.ubuntu.com/WorldofWarcraft") page on the wiki.[/QUOTE]
Compiled from source after patching, following those directions to the letter. I'll check out that wikipage.

---

### Post by Joetheodd on 2006-05-30
[QUOTE=Joetheodd]Compiled from source after patching, following those directions to the letter. I'll check out that wikipage.[/QUOTE]

I tried the instructions from the wikipage, but when it comes to patching..

```
joe@foobar:~/wine-0.9.14/wine $ patch -p0 < ../wow.new.patch.0.9.13-1
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- wine/libs/wine/mmap.c.orig 2006-05-11 17:02:13.000000000 +0100
|+++ wine/libs/wine/mmap.c      2006-05-19 22:08:03.000000000 +0100
--------------------------
File to patch: ./wine/libs/wine/mmap.c
./wine/libs/wine/mmap.c: No such file or directory
Skip this patch? [y] n
File to patch: ./libs/wine/mmap.c
patching file ./libs/wine/mmap.c
Hunk #1 succeeded at 161 (offset -22 lines).
Hunk #2 FAILED at 210.
1 out of 2 hunks FAILED -- saving rejects to file ./libs/wine/mmap.c.rej
can't find file to patch at input line 41
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- wine/loader/preloader.c.orig       2006-05-11 17:02:13.000000000 +0100
|+++ wine/loader/preloader.c    2006-05-19 22:14:22.000000000 +0100
--------------------------
File to patch: ./loader/preloader.c
patching file ./loader/preloader.c
Hunk #1 FAILED at 109.
1 out of 1 hunk FAILED -- saving rejects to file ./loader/preloader.c.rej
```

I might as well just install dapper, because theres the pre-built package.

---

### Post by Grog140 on 2006-05-31
Does anyoen else find that the curser response is delayed while running under wine? This is the biggest thing preventing me from wiping my Windows partition unfortunatly. There is like a 1/16 of a second delay and it gets quite annoying.

Or am I just going to have to grin and bare it untill Blizzard releases a Linux version of WoW? (HA, like that will happen)

---

### Post by urvaius on 2006-05-31
I just got this to work. thank you so much for doing this. i have not been able to get the patcher but i just patched my windows copy and copied all the files to my linux drive and it works great. funny all my windows is used for now is to patch wow hehe.

---

### Post by GIBson3 on 2006-05-31
[QUOTE=Grog140]Does anyoen else find that the curser response is delayed while running under wine? This is the biggest thing preventing me from wiping my Windows partition unfortunatly. There is like a 1/16 of a second delay and it gets quite annoying.

Or am I just going to have to grin and bare it untill Blizzard releases a Linux version of WoW? (HA, like that will happen)[/QUOTE]

Actually in the Early days of Closed Beta there was a Linux Client IIRC... However it was phenomonally buggy and disappeared after one of the early beta patches.... so while I'm "stupidly" optomistic for a native binary, I recommend not holding your breath ;P

On a side note anyone else having a "spastic camera" issue from time to time?  I have a feeling it relates to getting too close to the Verticle axis when moving the camera...

---

### Post by eqisow on 2006-05-31
Grog140, I haven't noticed the mouse issue and I'm afraid I don't know what might cause it. :(

urvaius, you're welcome. I'm glad I could help! Btw, there are plenty of sites that you can download patches from. You can probably also find them via BitTorrent. There's really no need to keeps Windows around just for patching.

---

### Post by Grog140 on 2006-05-31
I re-installed and fixed the mosue thign but I want to put my relolution to 800x600 but it isnt an option for some reason. There is only 1024x768.

Does anyone know whats up?

Also when I log into my character a pacth download thing comes up that never used to.

I fix one problem and cause 2 others...grr

EDIT:I got those things fixed but I got another problem, lol. None of my game settings are saving. No key bindings, video settings, nothing! Actually They did save once but they aren't saving anymore....hmm For instance my terrain setting are set to the way I want but whenever I log in it ALWAYS goes into 1024x768 instead of what I set (800x600)

---

### Post by eqisow on 2006-06-01
@Grog140

You don't have WoW installed in root do you? I know it seems silly, and it might not even run at all that way, but you have to check the obvious. :)

Other than that, I'm not sure. I've never run into the problem. You could always go into your WoW folder and edit your config.wtf file in the WTF folder. You can set and save your resolution here.

Change *SET gxResolution "1024x768"* to *SET gxResolution "800x600"*.

If you go into the Account folder inside the WTF folder, you can even edit you macros and other account specific settings if need be.

---

### Post by sornen on 2006-06-03
With the upgrade to 6.10 I get intermittent freezing in wow which lasts 1 to 3 s every 10 to 15 s.  Not sure what could be the cause of the problem.

Wow was working fine with 5.10.

---

### Post by eqisow on 2006-06-03
You mean 6.06, 6.10 will be out in 4 months. ;)

As far as the freezing goes, I'm afraid I don't know. I've been running WoW on Dapper for months ith no problems. :(

---

### Post by sornen on 2006-06-03
6.06 :/

The problem seems to be that CPU usage is around 96 to 100 %, but that doesnt seem right for the type of CPU that I have: 
AMD Athlon64 3200+ (2GHz) Socket 939 CPU.

Any suggestions for finding out why this happening or other diagnostics that I can do gratefully appreciated.

Even without wow running my CPU is spiking to about 100 % every 15 s, which may be the cause of the problem.  Anyway of finding out what process is hogging the resources?

---

### Post by eqisow on 2006-06-03
Perhaps WoW is using a software renderer instead of hardware acceleration? I'm not sure, but that would almost seem to fit the problem. I take it you have [3D acceleration]("https://wiki.ubuntu.com/BinaryDriverHowto") working and followed the directions in the [WoW wiki]("http://wiki.ubuntu.com/WorldofWarcraft")?

---

### Post by sornen on 2006-06-03
Fixed the problem.  It was going too smoothly for it to be software rendering.
What I did was look at System/Sytem Monitor under the Processes tab to see what was hogging cpu cycles.  It turns out Beagle was evey 15 s or so using 80 % of the CPU capacity.

I went to System/Prefernces/Search & Indexing and turned off everything.  And now wow is not freezing every 15 s.  :)

---

### Post by eqisow on 2006-06-03
Awesome, glad you solved the problem.

If you want to keep the indexing running, you could always re-nice the process to give WoW priority.

---

### Post by sornen on 2006-06-03
How do you renice processes?

---

### Post by eqisow on 2006-06-03
Err, I can't recall exactly. I use KDE instead of Gnome. You should be able to do it from the system monitor though.

---

### Post by sornen on 2006-06-03
Oh yes I can by right clicking on the process, Thanks for your help.

---

### Post by frobroj on 2006-06-04
Just my personal feelings. I decided to pay $50 USD per year for the transgaming solution and I love it. Its worth the $50 per year for them to do all the work to test each WOW upgrade patch etc. Plus it infuses a little income into the Open Source world. I always try (with my limited budget)  to contribute to any good Open Source project. It helps validate the fact that Open Source can be profitable. ;) Just my two cents...

---

### Post by sheky on 2006-06-04
hope im not thread jacking this at all but i'm having a problem of my own trying to install WoW on Ubuntu and I thought this would be the place to try.

When I copy all the CDs to a folder and run the installer from there I get the error from WoW not the terminal(after I agree to the TOS):

Unrecognized key "options". (AttributeParser::Parse)

and then it brings me back to the WoW main menu.

The reason I am not running it from CDs is because it all works and installs the first disc perfectly no errors, but when I get to put in the second CD the terminal wont let me eject my cdrom because it's in use.

is there a workaround to either of these problems? I am using breezy Ubuntu.

Please help! Im so close!!!

---

### Post by eqisow on 2006-06-04
When installing from the CD, have you tried running the umount command? 

```
sudo umount /media/cdrom
```

That should allow it to eject.

Edit: Sorry it took you so long to get a reply shecky, I usually try to stay on top of this thread.

---

### Post by =Kevin= on 2006-06-04
First of all, hi everyone... I'm kind of new to this forum :)

I recently was fed up with XP and decided to install Dapper on my system (had it dual-booted before), and everything works perfectly....almost.

I had no problems running WoW with wine before, but when I was flying from a flypath to another city (not the 1st flypath tho) the game crashed, and I can't login into that character again, instead it gives me this nice lil error:

[[IMG]http://img260.imageshack.us/img260/1141/schermafdruk1fk.th.png[/IMG]](http://img260.imageshack.us/my.php?image=schermafdruk1fk.png)

I can still login to my other chars, but I would like to log in to this char.
My second problem is that the sound worked before, but also now it doesn't work anymore.

Any help would be greatly appreciated,
Kevin

Ps.Sorry for the rubbish english, it's late and i'm tired of getting this thing to work ;)

---

### Post by eqisow on 2006-06-04
If it's just one character, you could try clearing that characters configuration files. They will be at home/username/.wine/drive_c/Program Files/World of Warcraft/WTF/Account/wowaccountname/server/character.

For the audio, does the sound in the rest of your system work? If so, you could try opening up winecfg (just type winecfg in the terminal) and going to the audio tab. Once there, you can try changing your audio drivers. I find OSS works best for WoW. If that's a no-go, changing the hardware acceleration may help as well. Basically, just fiddle with those settings and see what you can get.

Good luck, and let us know how it goes. :)

Edit: I just read your error message. It says a file is corrupt. Does it tell you it's the same file every time, or is it random? At any rate, I would also try running Repair.exe in your WoW folder.

---

### Post by =Kevin= on 2006-06-05
Thanks alot eqisow, I' ll try your tips and edit this post to let you know how it goes!

EDIT:
Repair.exe didn't work...

EDIT 2:
Woot! I cleared the home/username/.wine/drive_c/Program Files/World of Warcraft/WTF/Account/wowaccountname/server/character folder and now I can play my char again :D Thanks so much eqisow :)

Now I' ll try to get my sound to work ;)
All other sounds work, even the sound in WoW worked before..

EDIT 3:
This happens when I try to access the sound tab in winecfg:
[[IMG]http://img108.imageshack.us/img108/8794/schermafdruk0wl.th.png[/IMG]](http://img108.imageshack.us/my.php?image=schermafdruk0wl.png)

Any suggestions?

---

### Post by eqisow on 2006-06-05
Go to a terminal and open kcontrol. Go to Sound and Multimedia, then Sound System. Uncheck "Enable the Soundsystem." Go back to winecfg and try to change your sound drivers to OSS again.

(Don't worry, you will still ahve sound on your computer when you disable the sound system)

Edit: I may not be able to post again for 6-7 hours, so good luck. :)

Edit again: If you're still having winecfg issues, what version of Wine are you running? There is a documented bug [here]("http://bugs.winehq.org/show_bug.cgi?id=4051"), but it seems to be for older version. It also seems to center around support for arts being bad. Disabling the sound system, like I said, should take care of arts. If not, try renaming winearts.drv.so witht he following command:

```
sudo cp /usr/lib/wine/winearts.drv.so /usr/lib/wine/winearts.drv.so_backup
```

If you are running an old version of Wine (winecfg should tell you, and the latest version is 0.9.14), see [here]("http://wiki.ubuntu.com/Wine"). You want the one that says "Latest Wine with WoW patch".

Yet another edit: The problem also seems to be solved in Dapper, so if all else fails, consider upgrading.

(OK, I'm really leaving now, good luck!)

---

### Post by slax0r on 2006-06-05
I think I am getting closer to having this work, on account of this thread.  I have one (maybe strange) question though.

After setting up all the repositories and finally getting the dependencies for wine, I need to start over and build a new one.  I know the commands for getting rid of a package, but even after I type them in and it tells me that nothing was removed because no packages of that name exist, but when I type 'wine' into the console, it's clearly still installed.

Any help would be much appreciated.

Edit: Just for further clarification

```
slax0r@Hyrule:/etc/apt$ sudo apt-get --purge remove wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
slax0r@Hyrule:/etc/apt$ wine
Wine 0.9.6
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

```

---

### Post by eqisow on 2006-06-05
Did you install Wine with something besides dpkg? (ie. with a regular binary or with make/makeinstall)

If you did, it wouldnt be in the package manager.

---

### Post by slax0r on 2006-06-05
Yeah, I just followed the guide and did the basic ./config and make install.  Turns out everything was in /usr/local/bin so I just cleared it out (it's a brand new install and wine is the only thing I've installed myself).

I got some tips about using checkinstall.

---

### Post by eqisow on 2006-06-05
There is a package that already has the WoW patch included. Just use the following commands to install it:

```
wget http://thepiratecove.org/files/wine-0.9.15_wow_i386.deb
sudo dpkg -i wine-0.9.14_wow_i386.deb
rm wine-0.9.14_wow_i386.deb
```

---

### Post by leris on 2006-06-06
Hello all,

After much muckin around, I have successfully made myself a neat little chroot, install wine and have everything working nicely.

Except wow.

Patched it, got extra needed files apt-get install, etc. I have this error now, and can not for the life of me find anything on the web to fix it.

```

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  361
  Current serial number in output stream:  362

```

I've tried installing more bits of X, graphics card drivers (for the 32bit chroot) etc. etc. Everything else wine seems to work but X doesn't want to give WoW any resources. Anyone help please.

EDIT: 64Bit Ubuntu 6.06, ATI X600 Graphics, 1Gb RAM.

---

### Post by Brighid on 2006-06-07
I'm excited about being able to play WoW with (K)ubuntu, but I can't download the files from "kaspersandberg.com".  It seems to be down.  Perhaps this is temporary (changing servers?) .. but either way, does anyone know where else I can find the two files I need (wine-cvs-glx.diff and wine-wow-fixes.patch)?  I'd really like to get this working. :(

Edit:  It seems the site is back up.  I hope that was just a temporary problem!

---

### Post by clarke.rainey on 2006-06-07
Well the only problem that I have now is that my sound does not work... I use an Audigy 2 ZS notebook, which is alsa... but for some reason it does not show up in the winecfg under alsa... but it does under OSS and so does the onboard sound which I hate... but for some reason I cannot choose which one I want it to use in winecfg... any help would be wonderful... and just tell me what info you need...

---

### Post by glaze on 2006-06-07
I did a clean install of Kubuntu 6.06 Dapper Drake. Then I installed Wine 0.9.14 with wow.new.patch.0.9.13-1. WoW installer fonts are so tiny that they're unreadable. I click on topmost button and installer hangs. If someone knows anything about this, please share information. WoW worked fine when I used Kubuntu Breezy Badger.

---

### Post by clarke.rainey on 2006-06-07
The installer is not really hanging... you need to give it like 5-10 minutes of sitting there... then it goes right ahead!..

---

### Post by glaze on 2006-06-08
[QUOTE=clarke.rainey]The installer is not really hanging... you need to give it like 5-10 minutes of sitting there... then it goes right ahead!..[/QUOTE]
Thanks, now it works fine, except that it only runs at 15-20 fps. Could be Nvidia driver related problem. I recall that with some older driver it ran at 30-40 fps.

---

### Post by clarke.rainey on 2006-06-08
Well mine will not go above 30FPS pretty much... but even when it is most busy it will not go below 20... I think that there may be some sort of problem with teh FPS counter... becuase it is really smooth...

---

### Post by Gendo.nerv on 2006-06-11
Hello, I'm very new to Ubuntu and I've been trying to get WoW to work. I read a lot of the guides on the forums here but they seem sort of complicated. I downloaded the wine patch for WoW, I think, and Im only having a few problems. Since I have my laptop set up to dual boot with Windows XP I tried just going to where WoW.exe is located and opening it with Wine, and it worked except for a lot of really messed up textures, on the ground mostly, while Im playing.

Is there any way to fix this and keep playing off my windows drive?

---

### Post by smaugslayer on 2006-06-14
I followed the latest instructions for installing the wow patched version of wine.  However, when I try to install wow, I get the following error:


Sorry the installer could not be initialized
Unrecognized key "options". (AttributeParser::Parse)

Any suggestions?

Thx for the help

---

### Post by Wallakoala on 2006-06-14
[QUOTE=Gendo.nerv]Hello, I'm very new to Ubuntu and I've been trying to get WoW to work. I read a lot of the guides on the forums here but they seem sort of complicated. I downloaded the wine patch for WoW, I think, and Im only having a few problems. Since I have my laptop set up to dual boot with Windows XP I tried just going to where WoW.exe is located and opening it with Wine, and it worked except for a lot of really messed up textures, on the ground mostly, while Im playing.

Is there any way to fix this and keep playing off my windows drive?[/QUOTE]

I found that just copying the whole "World of Warcraft" directory from my windows drive to my wine fake drive worked perfectly. Your problem sounds like you're not using opengl. Try doing this next time you play WoW:
```
wine /path/to/WoW.exe -opengl
```
And of course change /path/to/WoW.exe to the actual path to it.

---

### Post by nshank on 2006-06-17
Hi all

I have gotten wine installed, using apt-get install wine. I ran the rest of the WoW install process as per the howto, however, I am unable to get the keyboard to respond (it's still bound to the terminal window that I started WoW from). I can alt-tab, but WoW isn't listed as an option (neither is wine, or anything of the sort). The mouse responds correctly, however.
 Any one else have this problem? Thoughts?
 Nick

Running: 6.0.6 (Dapper Drake), on an nForce 4, using a 6800GT (and everything works fine, except, WoW.

---

### Post by eqisow on 2006-06-17
You actually need a special patches version of Wine to play WoW. Check the [WoW]("http://wiki.ubuntu.com/WorldofWarcraft") and [Wine]("http://wiki.ubuntu.com/Wine") wiki's for more info. :)

---

### Post by SquatcHman on 2006-06-19
I've followed the wikis and installed the pre-patched version(specifically for wow) of wine, and copied the World of Warcraft client from my windows machine.  After making some necessary changes to Config.wtf I've actually been able to log into the game with almost no problems.  However, the software isn't rendering any graphics while using opengl(black screen).  Running the game with the -d3d switch will allow me to see what I am doing, but performance is obviously unacceptable.  

Other programs work, and I used Automatix to install the nvidia drivers.


Hardware:
Intel Pentium M 2.0 Ghz
nvidia GeforceGo 7800 GTX

---

### Post by gi2k15 on 2006-06-20
I've got 4 ISO images of WoW CDs here, since I lost my original CDs. But I don't know how to install it. I mounted the 1st image at a dir and ran the install. Everything went fine until the installer asked the 2nd CD. I umount ISO 1 and mount ISO 2 at the same place, but it didn't work, the installer keeped asking for CD 2. Then, I tried to copy everything from the 4 CDs to a dir /home/bruno/wow but the installer didn't lauch. It says it couldn't start the installer. So, I don't know how to install it now. Any ideas?

---

### Post by GIBson3 on 2006-06-20
[QUOTE=gi2k15]I've got 4 ISO images of WoW CDs here, since I lost my original CDs. But I don't know how to install it. I mounted the 1st image at a dir and ran the install. Everything went fine until the installer asked the 2nd CD. I umount ISO 1 and mount ISO 2 at the same place, but it didn't work, the installer keeped asking for CD 2. Then, I tried to copy everything from the 4 CDs to a dir /home/bruno/wow but the installer didn't lauch. It says it couldn't start the installer. So, I don't know how to install it now. Any ideas?[/QUOTE]

you need to make an "install directory" and copy the entire first disk, and then the installer *.mpq files from the other three, then run the installer from that Directory, it'll install nicely from there.

---

### Post by gi2k15 on 2006-06-20
[QUOTE=GIBson3]you need to make an "install directory" and copy the entire first disk, and then the installer *.mpq files from the other three, then run the installer from that Directory, it'll install nicely from there.[/QUOTE]
I tried this, but it didn't work. It opens a window with the message "Sorry, the installer was unable to start up". Wine returns:

:~/wow$ Missing symbol {LanguageCode}! (SymbolTable::UnmappedSymbolSubstitution)
fixme:ole:OleCreateStaticFromData (not shown), stub!

But when I try to run the installer from the image mounted directly, everything works fine until it asks for CD 2. Can it be some kind of protection, like SecuROM?

---

### Post by GIBson3 on 2006-06-21
[QUOTE=gi2k15]I tried this, but it didn't work. It opens a window with the message "Sorry, the installer was unable to start up". Wine returns:

:~/wow$ Missing symbol {LanguageCode}! (SymbolTable::UnmappedSymbolSubstitution)
fixme:ole:OleCreateStaticFromData (not shown), stub!

But when I try to run the installer from the image mounted directly, everything works fine until it asks for CD 2. Can it be some kind of protection, like SecuROM?[/QUOTE]

I installed using the above mentioned method...  I also put the exact process into an ODT :D  Pasted here as <code>

```

[Step 1]
   copy all of Disk 1 to the hard drive
[Step 2]
   Copy the “Installer Tome 2.mpq” from Disk 2 to the hard drive
[Step 3]
   Copy the “Installer Tomb 3.mpq” from Disk 3 to the hard drive
[Step 4]
   Copy the “Installer Tomb 4.mpg” from Disk 4 to the harddrive
[Step 5]
    in a terminal issue the command “wine path/to/files/Installer.exe”
[Step 6]
    click on the “Install World of Warcraft” button
[Step 7]
    Select “Agree” and choose to continue WITHOUT installing DirectX

```

---

### Post by simplyw00x on 2006-06-21
Apologies if it's been answered, but since updating my WoW I get an authentication error on trying to log on. The username and pass is fine; it works on the website and on a friend's computer, just no this one. Ideas?

---

### Post by Mon on 2006-07-10
> **gi2k15 said:**
> I've got 4 ISO images of WoW CDs here, since I lost my original CDs. But I don't know how to install it. I mounted the 1st image at a dir and ran the install. Everything went fine until the installer asked the 2nd CD. I umount ISO 1 and mount ISO 2 at the same place, but it didn't work, the installer keeped asking for CD 2. Then, I tried to copy everything from the 4 CDs to a dir /home/bruno/wow but the installer didn't lauch. It says it couldn't start the installer. So, I don't know how to install it now. Any ideas?

I had this problem too when installing. The "copy everything to 1 directory" thingie didn't work for me either.
I think i fixed it by starting the installer like: wine /media/cdrom/Setup.exe while your current directory is your home directory and NOT the cd drive.

---

### Post by bankie on 2006-07-19
I've downloaded and patched the source but get an error when I use ./configure:

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

Anyone know what's going on?

---

### Post by ingenious28 on 2006-07-20
sorry, im a bit new to this, i searched and couldnt find an answer to this problem.

i have WoW up and running just fine, however, it doesnt seem to save any settings (video and such). when i start up, i have to agree to the end user licence agreement every time and choose a realm.  also, a wow downloader will pop up in the background. i was hoping someone new a fix for this.

thanks.

---

### Post by Sp00ne on 2006-07-20
I got WoW working fine after reinstalling it, but the only problem is certain graphics are broken.

---

### Post by SishGupta on 2006-07-27
> **smaugslayer said:**
> I followed the latest instructions for installing the wow patched version of wine.  However, when I try to install wow, I get the following error:


Sorry the installer could not be initialized
Unrecognized key "options". (AttributeParser::Parse)

Any suggestions?

Thx for the help

Same and its crazy frustrating.

---

### Post by Burkey on 2006-07-27
I got mine running by downloading wine-0.9.17_wow_i386.deb and installing (forgot where I found it I think from WOW wiki on Ubuntu)

However mine locks up at times and forces a hard power off (oddly sound seems to keep working so I wonder what other people see or if I am actually still online)

My system though has an ATI X1400 running with fglrx.  Does anyone have a working WoW on fglrx?

---

### Post by Bink on 2006-08-19
Hello, I'm a completely new Ubuntu user, and could use a little help. I don't think this problem has come up with others, but sorry if I'm mistaken.

I followed the steps, but the wine-wow-fixes.patch doesn't select a file to patch automatically...which file should I patch?
```
$ patch -p1 < wine-wow-fixes.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: libs/wine/mmap.c
|===================================================================
|--- libs/wine/mmap.c   (revision 3438)
|+++ libs/wine/mmap.c   (working copy)
--------------------------
File to patch:
```
I tried patching libs/wine/mmap.c and dlls/opengl32/wgl.c, but I just got an error.
```
File to patch: libs/wine/mmap.c
patching file libs/wine/mmap.c
Hunk #1 succeeded at 161 (offset -22 lines).
Hunk #2 FAILED at 210.
1 out of 2 hunks FAILED -- saving rejects to file libs/wine/mmap.c.rej
can't find file to patch at input line 45
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: loader/preloader.c
|===================================================================
|--- loader/preloader.c (revision 3438)
|+++ loader/preloader.c (working copy)
--------------------------

File to patch: dlls/opengl32/wgl.c
patching file dlls/opengl32/wgl.c
Hunk #1 succeeded at 163 with fuzz 2 (offset -20 lines).
Hunk #2 FAILED at 212.
1 out of 2 hunks FAILED -- saving rejects to file dlls/opengl32/wgl.c.rej
can't find file to patch at input line 45
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: loader/preloader.c
|===================================================================
|--- loader/preloader.c (revision 3438)
|+++ loader/preloader.c (working copy)
--------------------------
```

Am I patching the right file? Or why would the second hunk fail? ](*,) 
Any help would be greatly appreciated! And thanks in advance.

---

### Post by tokyovigilante on 2006-08-19
Those patches are too old I think to apply to the current Wine version (0.9.19) which no longer needs any patching to run WoW. However, if you are using an nVidia card, you'll need [http://www.thehandofagony.com/alex/wine/patches/wow-patch-0.9.18.diff.]("http://www.thehandofagony.com/alex/wine/patches/wow-patch-0.9.18.diff")

The rest of the guide should be valid. 

As an aside, who has opinions on Wine vs Cedega? On my amd64 Wine with opengl far outperforms Cedega with d3d rendering (1280x1024 everything on), and is approaching windows performance.

---

### Post by AngryKidJoe on 2006-08-19
Trying to get Wine to run in 64bit is like trying to find gas under $2.00/gal.

---

### Post by tokyovigilante on 2006-08-20
> **AngryKidJoe said:**
> Trying to get Wine to run in 64bit is like trying to find gas under $2.00/gal.

That's not very helpful. As I've already alluded to, I was able to force-arch the i386 nVidia-patched deb referenced at the Ubuntu wik on a fresh Dapper install, and run WoW -opengl without further ado. Compiling should also be possible with the appropriate 32-bit libraries installed. 

The issue that most people face is that Wine development seems to move much faster than 64-bit compile guides can be written. For most people the best option seems to be force-arching the precompiled i386 deb, and having libsdl2.0debian-oss and asound32-libs installed.

---

### Post by autrui on 2006-08-23
hi folks,, 

this thread has been really helpful..  i'm also new (installed ubuntu a couple days ago) and this thread's taught me a lot!  but i'm hung up around the 

"Now we need to install MozillaControl under wine:
$ wine MozillaControl1712.exe

Now we can use the graphical wine configuration utility and choose the following options:
$ winecfg"

area.. the dll files should be in the right place (they're no longer in the wine-0.9.6 folder).  that first line that i quoted didn't work, so i tried copying the Mozilla exe elsewhere, moving it to the system32 folder, and a couple other things, but it didn't seem to work..  so i eventually double-clicked it on the desktop and selected to open it with wine,,, a new tab opened in firefox, with nothing in it.  i took that as a good sign and moved on.  

winecfg gave me this: 

nico@blackbox:~$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
nico@blackbox:~$

any suggestions?

thanks so much... :D 

autrui

---

### Post by tokyovigilante on 2006-08-23
> **autrui said:**
> hi folks,, 

this thread has been really helpful..  i'm also new (installed ubuntu a couple days ago) and this thread's taught me a lot!  but i'm hung up around the 

"Now we need to install MozillaControl under wine:
$ wine MozillaControl1712.exe

Now we can use the graphical wine configuration utility and choose the following options:
$ winecfg"

area.. the dll files should be in the right place (they're no longer in the wine-0.9.6 folder).  that first line that i quoted didn't work, so i tried copying the Mozilla exe elsewhere, moving it to the system32 folder, and a couple other things, but it didn't seem to work..  so i eventually double-clicked it on the desktop and selected to open it with wine,,, a new tab opened in firefox, with nothing in it.  i took that as a good sign and moved on.  

Wine 0.9.19 can automatically install this when required - eg when patching WoW. 
> **autrui said:**
> 
winecfg gave me this: 

nico@blackbox:~$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
nico@blackbox:~$

any suggestions?

thanks so much... :D 

autrui
Hmm, looks like your graphics setup is not quite right. Try posting up your system specs, Ubuntu version, and the results of these commands:

lspci
cat /etc/X11/xorg.conf

---

### Post by autrui on 2006-08-23
> **tokyovigilante said:**
> 
Hmm, looks like your graphics setup is not quite right. Try posting up your system specs, Ubuntu version, and the results of these commands:

lspci
cat /etc/X11/xorg.conf

ok, here's lspci: 
```
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7142
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 7162
0000:02:09.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
0000:02:09.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
0000:02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
```

and here's cat /etc/x11/xorg.conf

```

cat: /etc/x11/xorg.conf: No such file or directory

```

that last one doesn't look right... ;)

autrui

---

### Post by notoriouslou1022 on 2006-08-23
I get this problem when I play wow, it freezes and i get a error report...

```
==============================================================================

World of WarCraft (build 5464)



Exe:      C:\Program_Files\World_of_Warcraft\WoW.exe

Time:     Aug 20, 2006  5:07:23.175 AM

User:     luigi

Computer: luigi-desktop

------------------------------------------------------------------------------



This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	C:\Program_Files\World_of_Warcraft\WoW.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:0048BA7D



The instruction at "0x0048BA7D" referenced memory at "0x00000000".

The memory could not be "read".





WoWBuild: 5464

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=00000000  EBX=0106BD08  ECX=00000018  EDX=00000018  ESI=00000000

EDI=0106BC08  EBP=0033FAC4  ESP=0033FA88  EIP=0048BA7D  FLG=00210246

CS =0073      DS =007B      ES =007B      SS =007B      FS =003B      GS =0033





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



0048BA7D 0033FAC4 0001:0008AA7D C:\Program_Files\World_of_Warcraft\WoW.exe

006ED3DA 0033FADC 0001:002EC3DA C:\Program_Files\World_of_Warcraft\WoW.exe

006F0461 0033FB24 0001:002EF461 C:\Program_Files\World_of_Warcraft\WoW.exe

006ED81F 0033FB34 0001:002EC81F C:\Program_Files\World_of_Warcraft\WoW.exe

006EB48B 0033FB9C 0001:002EA48B C:\Program_Files\World_of_Warcraft\WoW.exe

006EDBCB 0033FBC4 0001:002ECBCB C:\Program_Files\World_of_Warcraft\WoW.exe

006EB46C 0033FBE8 0001:002EA46C C:\Program_Files\World_of_Warcraft\WoW.exe

006FC3DE 0033FC74 0001:002FB3DE C:\Program_Files\World_of_Warcraft\WoW.exe

006F9977 0033FC90 0001:002F8977 C:\Program_Files\World_of_Warcraft\WoW.exe

006F9938 0033FCA8 0001:002F8938 C:\Program_Files\World_of_Warcraft\WoW.exe

00770246 0033FCDC 0001:0036F246 C:\Program_Files\World_of_Warcraft\WoW.exe

0077000F 0033FD00 0001:0036F00F C:\Program_Files\World_of_Warcraft\WoW.exe

0075D127 0033FD54 0001:0035C127 C:\Program_Files\World_of_Warcraft\WoW.exe

00424490 0033FD88 0001:00023490 C:\Program_Files\World_of_Warcraft\WoW.exe

00423EF5 0033FDBC 0001:00022EF5 C:\Program_Files\World_of_Warcraft\WoW.exe

004238BA 0033FDD4 0001:000228BA C:\Program_Files\World_of_Warcraft\WoW.exe

00423751 0033FE04 0001:00022751 C:\Program_Files\World_of_Warcraft\WoW.exe

00420B08 0033FE60 0001:0001FB08 C:\Program_Files\World_of_Warcraft\WoW.exe

004209D1 0033FE78 0001:0001F9D1 C:\Program_Files\World_of_Warcraft\WoW.exe

00403F1E 0033FF08 0001:00002F1E C:\Program_Files\World_of_Warcraft\WoW.exe

7EEA3A6F 0033FFE8 0001:00052A6F c:\windows\system32\kernel32.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



0048BA7D WoW.exe      <unknown symbol>+0 (0x0557A988,0x00000059,0x00000000,0x00000080)

006ED3DA WoW.exe      <unknown symbol>+0 (0x0D522068,0x0557A988,0x07A18808,0x00000000)

006F0461 WoW.exe      <unknown symbol>+0 (0x0557A988,0x006EB480,0x0033FB9C,0x006EB48B)

006ED81F WoW.exe      <unknown symbol>+0 (0x00000000,0x006ED027,0x00000000,0x0557A988)

006EB48B WoW.exe      <unknown symbol>+0 (0x0033FBE0,0x0D522008,0x00000050,0x07A18808)

006EDBCB WoW.exe      <unknown symbol>+0 (0x0033FBE0,0x00000060,0x00000050,0xFFFFFFFF)

006EB46C WoW.exe      <unknown symbol>+0 (0x00000000,0xFFFFFFFE,0x3A474244,0x6974704F)

006FC3DE WoW.exe      <unknown symbol>+0 (0x00000C2C,0x07A18808,0x07A0BCA8,0x0033FC1C)

006F9977 WoW.exe      <unknown symbol>+0 (0x07A18808,0x07A18CD4,0x00824200,0x0033FCBC)

006F9938 WoW.exe      <unknown symbol>+0 (0x07A18808,0x07A18CD4,0x00824200,0x0086D8E0)

00770246 WoW.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x0033FD98,0x071C8008)

0077000F WoW.exe      <unknown symbol>+0 (0x00000001,0x0033FD68,0x07AB41C8,0x07AB41C8)

0075D127 WoW.exe      <unknown symbol>+0 (0x0033FE5C,0x011C2408,0x00000001,0x07AB41C8)

00424490 WoW.exe      <unknown symbol>+0 (0x0033FD98,0x011C2408,0x00000000,0x00000001)

00423EF5 WoW.exe      <unknown symbol>+0 (0x0000030E,0x0000036A,0x00000000,0x000169B1)

004238BA WoW.exe      <unknown symbol>+0 (0x0033FDF0,0x0033FE5C,0x00000000,0x00000102)

00423751 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x7EEDC8A8,0x69676E45)

00420B08 WoW.exe      <unknown symbol>+0 (0x00000000,0x004021D9,0x00000001,0x00000001)

004209D1 WoW.exe      <unknown symbol>+0 (0x00409780,0x00400000,0x00000000,0x00116579)

00403F1E WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)

7EEA3A6F kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)

B7E85287              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)





----------------------------------------

    Loaded Modules

----------------------------------------



0x00340000 - 0x003D6000  C:\Program_Files\World_of_Warcraft\fmod.dll

0x00400000 - 0x00CFA000  C:\Program_Files\World_of_Warcraft\WoW.exe

0x10000000 - 0x10069000  C:\Program_Files\World_of_Warcraft\DivxDecoder.dll

0x6E670000 - 0x6E6A7000  c:\windows\system32\dbghelp.dll

0x71710000 - 0x7171B000  c:\windows\system32\psapi.dll

0x7BFD0000 - 0x7BFDE000  c:\windows\system32\mswsock.dll

0x7BFF0000 - 0x7C000000  c:\windows\system32\midimap.dll

0x7C390000 - 0x7C3C0000  c:\windows\system32\wineoss.drv

0x7CFA0000 - 0x7CFC6000  c:\windows\system32\uxtheme.dll

0x7E240000 - 0x7E2AF000  c:\windows\system32\winex11.drv

0x7E380000 - 0x7E398000  c:\windows\system32\mpr.dll

0x7E3A0000 - 0x7E3DF000  c:\windows\system32\wininet.dll

0x7E3F0000 - 0x7E441000  c:\windows\system32\msvcrt.dll

0x7E450000 - 0x7E467000  c:\windows\system32\msacm32.drv

0x7E470000 - 0x7E4EF000  c:\windows\system32\winmm.dll

0x7E500000 - 0x7E50B000  c:\windows\system32\imm32.dll

0x7E750000 - 0x7E7A9000  c:\windows\system32\opengl32.dll

0x7E7B0000 - 0x7E7D3000  c:\windows\system32\ws2_32.dll

0x7E7E0000 - 0x7E7ED000  c:\windows\system32\wsock32.dll

0x7E810000 - 0x7E81F000  c:\windows\system32\iphlpapi.dll

0x7E830000 - 0x7E86E000  c:\windows\system32\rpcrt4.dll

0x7E880000 - 0x7E8FE000  c:\windows\system32\ole32.dll

0x7E910000 - 0x7E954000  c:\windows\system32\shlwapi.dll

0x7E960000 - 0x7EA3A000  c:\windows\system32\shell32.dll

0x7EB30000 - 0x7EBCB000  c:\windows\system32\gdi32.dll

0x7EBF0000 - 0x7ECFE000  c:\windows\system32\user32.dll

0x7ED10000 - 0x7EDC0000  c:\windows\system32\comctl32.dll

0x7EDD0000 - 0x7EE04000  c:\windows\system32\advapi32.dll

0x7EE50000 - 0x7EF38000  c:\windows\system32\kernel32.dll

0x7EF90000 - 0x7F000000  c:\windows\system32\ntdll.dll





----------------------------------------

    Memory Dump

----------------------------------------



Code: 16 bytes starting at (EIP = 0048BA7D)



0048BA7D: 3B 0C 06 75  13 3B 54 06  04 75 0D 8B  4D F8 3B 4C  ;..u.;T..u..M.;L





Stack: 1024 bytes starting at (ESP = 0033FA88)



* = addr                            **                                *       

0033FA80: 08 BD 06 01  4B BA 48 00  D0 B9 48 00  88 A9 57 05  ....K.H...H...W.

0033FA90: 88 20 52 0D  88 A9 57 05  A8 8A 51 07  A8 8A 51 07  . R...W...Q...Q.

0033FAA0: B4 FA 33 00  86 1A 6F 00  88 20 52 0D  A8 8A 51 07  ..3...o.. R...Q.

0033FAB0: 88 A9 57 05  D4 FA 33 00  00 05 00 00  01 00 00 00  ..W...3.........

0033FAC0: 08 65 1B 01  DC FA 33 00  DA D3 6E 00  88 A9 57 05  .e....3...n...W.

0033FAD0: 59 00 00 00  00 00 00 00  80 00 00 00  24 FB 33 00  Y...........$.3.

0033FAE0: 61 04 6F 00  68 20 52 0D  88 A9 57 05  08 88 A1 07  a.o.h R...W.....

0033FAF0: 00 00 00 00  02 00 00 00  80 B4 6E 00  88 B0 C7 7E  ..........n....~

0033FB00: 60 43 CC 7E  00 00 00 00  28 FB 33 00  00 00 00 00  `C.~....(.3.....

0033FB10: 88 04 61 07  08 20 22 07  88 20 52 0D  60 AA 20 07  ..a.. ".. R.`. .

0033FB20: 88 A9 57 05  34 FB 33 00  1F D8 6E 00  88 A9 57 05  ..W.4.3...n...W.

0033FB30: 80 B4 6E 00  9C FB 33 00  8B B4 6E 00  00 00 00 00  ..n...3...n.....

0033FB40: 27 D0 6E 00  00 00 00 00  88 A9 57 05  00 00 00 00  '.n.......W.....

0033FB50: 9C FB 33 00  08 88 A1 07  00 00 00 00  88 A9 57 05  ..3...........W.

0033FB60: 38 FB 33 00  0C D0 6E 00  F8 FE 33 00  00 00 00 00  8.3...n...3.....

0033FB70: 30 32 43 56  00 00 00 00  00 00 00 00  00 00 00 00  02CV............

0033FB80: 7C FC 33 00  64 FC 33 00  CA 3D FD 7E  02 00 00 00  |.3.d.3..=.~....

0033FB90: 00 00 00 00  80 B4 6E 00  88 A9 57 05  C4 FB 33 00  ......n...W...3.

0033FBA0: CB DB 6E 00  E0 FB 33 00  08 20 52 0D  50 00 00 00  ..n...3.. R.P...

0033FBB0: 08 88 A1 07  00 00 00 00  00 00 00 00  88 A9 00 00  ................

0033FBC0: E0 FB 33 01  E8 FB 33 00  6C B4 6E 00  E0 FB 33 00  ..3...3.l.n...3.

0033FBD0: 60 00 00 00  50 00 00 00  FF FF FF FF  88 A9 57 05  `...P.........W.

0033FBE0: 68 20 52 0D  00 00 00 00  74 FC 33 00  DE C3 6F 00  h R.....t.3...o.

0033FBF0: 00 00 00 00  FE FF FF FF  44 42 47 3A  4F 70 74 69  ........DBG:Opti

0033FC00: 6F 6E 73 46  72 61 6D 65  4F 6B 61 79  00 C3 6F 00  onsFrameOkay..o.

0033FC10: 01 00 00 00  00 00 00 00  B1 69 01 00  FF FF FF FF  .........i......

0033FC20: 31 BB C6 7E  00 00 00 00  88 52 FF 7E  01 00 00 00  1..~.....R.~....

0033FC30: 8C FC 33 00  C4 FC 33 00  2A 73 FD 7E  4C FC 33 00  ..3...3.*s.~L.3.

0033FC40: AC FC 33 00  12 60 58 00  4C FC 33 00  00 00 00 00  ..3..`X.L.3.....

0033FC50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

0033FC60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

0033FC70: 01 00 00 00  90 FC 33 00  77 99 6F 00  2C 0C 00 00  ......3.w.o.,...

0033FC80: 08 88 A1 07  A8 BC A0 07  1C FC 33 00  08 88 A1 07  ..........3.....

0033FC90: A8 FC 33 00  38 99 6F 00  08 88 A1 07  D4 8C A1 07  ..3.8.o.........

0033FCA0: 00 42 82 00  BC FC 33 00  DC FC 33 00  46 02 77 00  .B....3...3.F.w.

0033FCB0: 08 88 A1 07  D4 8C A1 07  00 42 82 00  E0 D8 86 00  .........B......

0033FCC0: 18 FD 33 00  08 88 A1 07  B1 69 01 00  00 00 00 00  ..3......i......

0033FCD0: 7F 0E 7F 02  E4 FC 33 00  95 B5 42 00  00 FD 33 00  ......3...B...3.

0033FCE0: 0F 00 77 00  01 00 00 00  00 00 00 00  98 FD 33 00  ..w...........3.

0033FCF0: 08 80 1C 07  08 88 A1 07  79 41 F4 3E  95 68 BB 3D  ........yA.>.h.=

0033FD00: 54 FD 33 00  27 D1 75 00  01 00 00 00  68 FD 33 00  T.3.'.u.....h.3.

0033FD10: C8 41 AB 07  C8 41 AB 07  DC 83 7F 00  00 00 00 00  .A...A..........

0033FD20: C9 00 05 40  00 00 00 00  00 00 00 00  01 00 00 00  ...@............

0033FD30: 00 00 00 00  00 00 00 00  00 00 00 00  79 41 F4 3E  ............yA.>

0033FD40: 95 68 BB 3D  8A 69 01 00  B1 69 01 00  00 00 00 00  .h.=.i...i......

0033FD50: C0 1E 49 00  88 FD 33 00  90 44 42 00  5C FE 33 00  ..I...3..DB.\.3.

0033FD60: 08 24 1C 01  01 00 00 00  C8 41 AB 07  11 25 1C 01  .$.......A...%..

0033FD70: 00 04 00 00  6A 03 00 00  00 05 00 00  01 00 00 00  ....j...........

0033FD80: 0E 00 00 00  0C 25 1C 01  BC FD 33 00  F5 3E 42 00  .....%....3..>B.

0033FD90: 98 FD 33 00  08 24 1C 01  00 00 00 00  01 00 00 00  ..3..$..........

0033FDA0: 00 00 00 00  00 00 00 00  00 00 00 00  66 66 1C 3F  ............ff.?

0033FDB0: 00 00 16 3E  8A 69 01 00  B1 69 01 00  D4 FD 33 00  ...>.i...i....3.

0033FDC0: BA 38 42 00  0E 03 00 00  6A 03 00 00  00 00 00 00  .8B.....j.......

0033FDD0: B1 69 01 00  04 FE 33 00  51 37 42 00  F0 FD 33 00  .i....3.Q7B...3.

0033FDE0: 5C FE 33 00  00 00 00 00  02 01 00 00  08 24 1C 01  \.3..........$..

0033FDF0: 01 00 00 00  0E 03 00 00  6A 03 00 00  B1 69 01 00  ........j....i..

0033FE00: 0D 00 00 00  60 FE 33 00  08 0B 42 00  00 F0 FD 7F  ....`.3...B.....

0033FE10: 00 00 00 00  A8 C8 ED 7E  45 6E 67 69  6E 65 20 39  .......~Engine 9

0033FE20: 00 00 11 00  A0 BD 16 00  06 00 00 00  27 9C FA 7E  ............'..~

0033FE30: 65 6E 00 7E  A8 C8 ED 7E  00 F0 FD 7F  5C FE 33 00  en.~...~....\.3.

0033FE40: 14 79 EB 7E  98 20 00 00  00 00 00 00  64 FE 33 00  .y.~. ......d.3.

0033FE50: 57 44 42 43  A8 C8 ED 7E  B1 69 01 00  00 00 00 00  WDBC...~.i......

0033FE60: 78 FE 33 00  D1 09 42 00  00 00 00 00  D9 21 40 00  x.3...B......!@.

0033FE70: 01 00 00 00  01 00 00 00  08 FF 33 00  1E 3F 40 00  ..........3..?@.

0033FE80: 80 97 40 00  00 00 40 00  00 00 00 00  79 65 11 00  ..@...@.....ye..





------------------------------------------------------------------------------


```  I CAN"T GET ANY ANSWER ANYWHERE

---

### Post by tokyovigilante on 2006-08-23
> **autrui said:**
> ok, here's lspci: 
```
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7142
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 7162
0000:02:09.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
0000:02:09.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
0000:02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
``` 

OK, your video card is listed as an unrecognised ATI. I take it you haven't installed the fglrx accelerated drivers?
> **autrui said:**
> 
and here's cat /etc/x11/xorg.conf

```

cat: /etc/x11/xorg.conf: No such file or directory

``` 
that last one doesn't look right... ;)

No it doesn't... Linux has a case-sensitive file system, so you need to type /etc/X11/xorg.conf rather than /etc/x11/xorg.conf.

Basically the issue looks like you are using unaccelerated X drivers, and need to install the ATI ones. These are in the ubuntu repositories, so search for fglrx in Synaptic or type 

sudo apt-get install fglrx

at the command prompt.

you'll then need to set it up by editing xorg.conf:

sudo gedit /etc/X11/xorg.conf &

Change the "radeon" or "vesa" under the driver option in the [Device] section that matches your card.

then rerun winecfg.

---

### Post by tokyovigilante on 2006-08-23
> **notoriouslou1022 said:**
> I get this problem when I play wow, it freezes and i get a error report...


I CAN"T GET ANY ANSWER ANYWHERE

You need to provide more information about your hardware, system, configuration, and whether you are using wine or Cedega, and their versions and how you installed them before anyone can help you.

---

### Post by notoriouslou1022 on 2006-08-23
i'm running the newest version of wine. i have a ati x600 card and its configured correctly, i'm just gonna reistall everything ;)

---

### Post by autrui on 2006-08-23
> **tokyovigilante said:**
> No it doesn't... Linux has a case-sensitive file system, so you need to type /etc/X11/xorg.conf rather than /etc/x11/xorg.conf.

Basically the issue looks like you are using unaccelerated X drivers, and need to install the ATI ones. These are in the ubuntu repositories, so search for fglrx in Synaptic or type 

sudo apt-get install fglrx

at the command prompt.

you'll then need to set it up by editing xorg.conf:

sudo gedit /etc/X11/xorg.conf &

Change the "radeon" or "vesa" under the driver option in the [Device] section that matches your card.

then rerun winecfg.

ok, got the fglrx, but i'm unclear on what to edit in the xorg.conf.  my card is the ATI Radeon x1300 pro.  my xorg.conf presently looks like this:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fgrlx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

these lines, i think, are the ones you mean.
```
Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fgrlx"
```
driver was originally "vesa".  i also tried changing vesa/fgrlx to "radeon" and changing "default card" to "Radeon x1300 Pro" and (having learned from my previous mistake ;)) "Radeon X1300 Pro", and a number of other alterations.  

sorry if i sound like a total moron!  leave it to we newbies to find the one area of vagueness and blow a hole into it teh size of a truck!

thanks,

autrui

---

### Post by tokyovigilante on 2006-08-23
> **autrui said:**
> ok, got the fglrx, but i'm unclear on what to edit in the xorg.conf.  my card is the ATI Radeon x1300 pro.  my xorg.conf presently looks like this:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. ATI Default Card"
    Driver        "fgrlx"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "SyncMaster"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. ATI Default Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

``` 
these lines, i think, are the ones you mean.
```
Section "Device"
    Identifier    "ATI Technologies, Inc. ATI Default Card"
    Driver        "fgrlx"
``` driver was originally "vesa".  i also tried changing vesa/fgrlx to "radeon" and changing "default card" to "Radeon x1300 Pro" and (having learned from my previous mistake ;)) "Radeon X1300 Pro", and a number of other alterations.  

sorry if i sound like a total moron!  leave it to we newbies to find the one area of vagueness and blow a hole into it teh size of a truck!

thanks,

autrui
Yup, that's the right section. It needs to be fglrx rather than fgrlx. Then hit Control-Alt-Backspace to restart the X server.

Also, the device identifier doesn't matter, its a label for you, not the computer. However, it must match the indentifier in the [Screen] section, as the X server builds a [Server] from a combination of [Device] (ie 3d card) , [Display] and keyboard and mouse. The identifiers for these various sections must be the same in both, but they can be whatever you want.

Its entirely possible that in the course of changing xorg.conf you will make a mistake that will be unable to be interpreted by the X server and it won't start, leaving you at a command prompt. In this case log in, and use nano (the command prompt text editor) - 

sudo nano /etc/X11/xorg.conf

to correct it and then type startx to get the X server running. You could also make a backup of xorg.conf before starting - 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

and then to restore if things break - 

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Once you've got it working, type glxinfo | grep render to see if things are working. It should list somewhere "Direct Rendering - Yes".
If it says no you arent using the accelerated driver (fglrx).

Good luck! Don't worry about coming off as a noob, everyone starts somewhere.

---

### Post by autrui on 2006-08-23
> **tokyovigilante said:**
> Yup, that's the right section. It needs to be fglrx rather than fgrlx. Then hit Control-Alt-Backspace to restart the X server.

Also, the device identifier doesn't matter, its a label for you, not the computer. However, it must match the indentifier in the [Screen] section, as the X server builds a [Server] from a combination of [Device] (ie 3d card) , [Display] and keyboard and mouse. The identifiers for these various sections must be the same in both, but they can be whatever you want.

Its entirely possible that in the course of changing xorg.conf you will make a mistake that will be unable to be interpreted by the X server and it won't start, leaving you at a command prompt. In this case log in, and use nano (the command prompt text editor) - 

sudo nano /etc/X11/xorg.conf

to correct it and then type startx to get the X server running. You could also make a backup of xorg.conf before starting - 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

and then to restore if things break - 

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Once you've got it working, type glxinfo | grep render to see if things are working. It should list somewhere "Direct Rendering - Yes".
If it says no you arent using the accelerated driver (fglrx).

Good luck! Don't worry about coming off as a noob, everyone starts somewhere.

thanks for all that--i did, indeed, need to use nano.  then i did the backup thing, and every time i've screwed it up, its been cake!  

but, i keep screwing it up.  synaptic only lists xorg-driver-fglrx, and a couple of others that are similar; and they're all already installed.  when i do "sudo apt-get install fglrx" nothing comes up. "E: Couldn't find package fglrx" ... i have all the binary repositories checked, so i don't know what the deal is.

any thoughts?

autrui

---

### Post by tokyovigilante on 2006-08-24
> **autrui said:**
> thanks for all that--i did, indeed, need to use nano.  then i did the backup thing, and every time i've screwed it up, its been cake!  

but, i keep screwing it up.  synaptic only lists xorg-driver-fglrx, and a couple of others that are similar; and they're all already installed.  when i do "sudo apt-get install fglrx" nothing comes up. "E: Couldn't find package fglrx" ... i have all the binary repositories checked, so i don't know what the deal is.

any thoughts?

autrui
xorg-driver-fglrx is indeed the package you need installed. I suggest deleting your xorg.conf and using the configuration tool, which will walk you through the process. Its a bit tedious but should get you going. 

Its

sudo dpkg-reconfigure xserver-xorg

at the command prompt. Select fglrx when it asks you for a video driver, then accept the defaults for everything else.

---

### Post by autrui on 2006-08-24
> **tokyovigilante said:**
> xorg-driver-fglrx is indeed the package you need installed. I suggest deleting your xorg.conf and using the configuration tool, which will walk you through the process. Its a bit tedious but should get you going. 

Its

sudo dpkg-reconfigure xserver-xorg

at the command prompt. Select fglrx when it asks you for a video driver, then accept the defaults for everything else.

after giving up out of frustration for the night, i'm back on this morning. i believe i've got the xorg.conf right, but, having gone back to the original post to continue this process, i get the same error when i run winecfg:
```
$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

here's the lspci:
```
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7142
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 7162
0000:02:09.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
0000:02:09.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
0000:02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

```
and here's the cat /etc/X11/xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. ATI Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

i'm running a Dell GX270, 1gig ram (2x512), 3.2ghz, 200gig sata HD (with Ubuntu 6.06LTS on it) and a 250gig IDE (NTFS); ATI Radeon x1300pro; samsung syncmaster930b monitor, and a Braun KF590e.

any idea where to go from here?  

thanks,

autrui

---

### Post by Tanth on 2006-08-24
Whenever I try to launch WoW, before the game opens, I get error 132.

=============================================================================
World of WarCraft: Assertions Enabled Build (build 4115)

Exe:      C:\world\WoW.exe
Time:     Aug 24, 2006  5:01:59.034 PM
User:     tanth
Computer: Happy-Fun-Box
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084)
Program:	C:\world\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:B7CF2DA0

The instruction at "0xB7CF2DA0" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 4115
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0016D3F0  EBX=7D8F9F90  ECX=0016D3EF  EDX=00000000  ESI=0016D3F0
EDI=0016D3C8  EBP=0033EF3C  ESP=0033EF38  EIP=B7CF2DA0  FLG=00010206
CS =0073      DS =007B      ES =007B      SS =007B      FS =003B      GS =0033


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

B7CF2DA0 0033EF3C 0000:00000000 <unknown>
7D890CCA 0033F1AC 0001:0002FCCA c:\windows\system32\wined3d.dll
7D895AE6 0033F1EC 0001:00034AE6 c:\windows\system32\wined3d.dll
7D9134F4 0033F23C 0001:000124F4 c:\windows\system32\d3d9.dll
00583691 0033F860 0001:00182691 C:\world\WoW.exe
005801B0 0033F870 0001:0017F1B0 C:\world\WoW.exe
00637B54 0033FCAC 0001:00236B54 C:\world\WoW.exe
00630578 0033FD08 0001:0022F578 C:\world\WoW.exe
0040287B 0033FE5C 0001:0000187B C:\world\WoW.exe
00402424 0033FE68 0001:00001424 C:\world\WoW.exe
004041FB 0033FF08 0001:000031FB C:\world\WoW.exe
7EE9AA6F 0033FFE8 0001:00049A6F c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

B7CF2DA0              strcpy+32 (0x0016D3F0,0x00000000,0x0033EF6C,0x7EFB6825)
7D890CCA wined3d.dll  IWineD3DImpl_FillGLCaps+110 (0x0016D3C8,0x7C0618F0,0x7D8E68A0,0x7D8E8EE8)
7D895AE6 wined3d.dll  <unknown symbol>+0 (0x0016D3C8,0x00000000,0x00000000,0x0033F214)
7D9134F4 d3d9.dll     <unknown symbol>+0 (0x0016D028,0x00000000,0x00000000,0x0033F260)
00583691 WoW.exe      <unknown symbol>+0 (0x00A73120,0x00A73124,0x0033FCAC,0x00637B54)
005801B0 WoW.exe      <unknown symbol>+0 (0x00A73120,0x00A73124,0x00F3A9A8,0x00000005)
00637B54 WoW.exe      <unknown symbol>+0 (0x00F3A9A8,0x00000005,0x00000001,0x0033FCD8)
00630578 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x001164C9,0x00000000,0x6C726F57)
0040287B WoW.exe      <unknown symbol>+0 (0x00000001,0x0033FF08,0x004041FB,0x0040B034)
00402424 WoW.exe      <unknown symbol>+0 (0x0040B034,0x00400000,0x00000000,0x001164C9)
004041FB WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7EE9AA6F kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7DE0287              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00340000 - 0x003CF000  C:\world\fmod.dll
0x00400000 - 0x00B26000  C:\world\WoW.exe
0x10000000 - 0x10069000  C:\world\DivxDecoder.dll
0x7D800000 - 0x7D80A000  c:\windows\system32\psapi.dll
0x7D810000 - 0x7D84F000  c:\windows\system32\dbghelp.dll
0x7D860000 - 0x7D8FB000  c:\windows\system32\wined3d.dll
0x7D900000 - 0x7D924000  c:\windows\system32\d3d9.dll
0x7D930000 - 0x7D939000  c:\windows\system32\midimap.dll
0x7D960000 - 0x7D98D000  c:\windows\system32\wineoss.drv
0x7D9D0000 - 0x7D9F0000  c:\windows\system32\uxtheme.dll
0x7DA20000 - 0x7DA8B000  c:\windows\system32\winex11.drv
0x7DB60000 - 0x7DB74000  c:\windows\system32\mpr.dll
0x7DB80000 - 0x7DBBB000  c:\windows\system32\wininet.dll
0x7DBC0000 - 0x7DBE1000  c:\windows\system32\msacm32.drv
0x7DBF0000 - 0x7DC69000  c:\windows\system32\winmm.dll
0x7DC70000 - 0x7DC85000  c:\windows\system32\imm32.dll
0x7DC90000 - 0x7DC9B000  c:\windows\system32\glu32.dll
0x7E6E0000 - 0x7E73E000  c:\windows\system32\opengl32.dll
0x7E750000 - 0x7E768000  c:\windows\system32\ws2_32.dll
0x7E770000 - 0x7E782000  c:\windows\system32\wsock32.dll
0x7E7A0000 - 0x7E7B4000  c:\windows\system32\iphlpapi.dll
0x7E7C0000 - 0x7E803000  c:\windows\system32\rpcrt4.dll
0x7E810000 - 0x7E893000  c:\windows\system32\ole32.dll
0x7E8A0000 - 0x7E8E9000  c:\windows\system32\shlwapi.dll
0x7E900000 - 0x7E9CF000  c:\windows\system32\shell32.dll
0x7E9E0000 - 0x7EA13000  c:\windows\system32\advapi32.dll
0x7EB10000 - 0x7EBA4000  c:\windows\system32\gdi32.dll
0x7EBC0000 - 0x7ECD7000  c:\windows\system32\user32.dll
0x7ECE0000 - 0x7ED99000  c:\windows\system32\comctl32.dll
0x7EDB0000 - 0x7EDFB000  c:\windows\system32\msvcrt.dll
0x7EE50000 - 0x7EF2F000  c:\windows\system32\kernel32.dll
0x7EF90000 - 0x7F000000  c:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = B7CF2DA0)

B7CF2DA0: 0F B6 02 42  84 C0 88 04  0A 75 F5 89  F0 5E 5D C3  ...B.....u...^].


Stack: 1024 bytes starting at (ESP = 0033EF38)

* = addr                            **                                *       
0033EF30: 01 00 00 00  90 9F 8F 7D  00 00 00 00  AC F1 33 00  .......}......3.
0033EF40: CA 0C 89 7D  F0 D3 16 00  00 00 00 00  6C EF 33 00  ...}........l.3.
0033EF50: 25 68 FB 7E  E4 02 00 00  FF FF 00 00  AC EF 33 00  %h.~..........3.
0033EF60: 1E 6E FB 7E  00 39 B9 7E  58 01 00 00  00 00 11 00  .n.~.9.~X.......
0033EF70: 30 A0 16 00  00 00 00 00  48 01 00 00  38 00 11 00  0.......H...8...
0033EF80: A4 5C FB 7E  FC EF 33 00  00 00 11 00  00 00 11 00  .\.~..3.........
0033EF90: 27 9C FA 7E  68 91 16 00  00 00 06 00  88 A1 16 00  '..~h...........
0033EFA0: 19 96 FA 7E  20 A0 16 00  88 52 FF 7E  0C F0 33 00  ...~ ....R.~..3.
0033EFB0: 40 7B FB 7E  20 00 11 00  FF FF 00 00  FC EF 33 00  @{.~ .........3.
0033EFC0: A8 38 ED 7E  00 39 B9 7E  10 90 16 00  0C F0 33 00  .8.~.9.~......3.
0033EFD0: 19 96 FA 7E  00 39 B9 7E  A8 38 ED 7E  1C F0 33 00  ...~.9.~.8.~..3.
0033EFE0: 7C 14 EB 7E  00 39 B9 7E  28 A0 16 00  02 00 00 00  |..~.9.~(.......
0033EFF0: 27 9C FA 7E  E4 02 00 00  FF FF 00 00  00 00 11 00  '..~............
0033F000: A8 38 ED 7E  00 39 B9 7E  FF FF 00 00  4C F0 33 00  .8.~.9.~....L.3.
0033F010: C9 12 EB 7E  00 39 B9 7E  00 00 00 00  4C F0 33 00  ...~.9.~....L.3.
0033F020: 19 96 FA 7E  00 39 B9 7E  A8 38 ED 7E  6C F0 33 00  ...~.9.~.8.~l.3.
0033F030: B5 A2 A4 7D  00 39 B9 7E  4D CF 4C 01  CC C0 FD 7F  ...}.9.~M.L.....
0033F040: A8 38 ED 7E  00 39 B9 7E  FF FF 00 00  8C F0 33 00  .8.~.9.~......3.
0033F050: C9 12 EB 7E  00 39 B9 7E  4D 4F 00 00  8C F0 33 00  ...~.9.~MO....3.
0033F060: 19 96 FA 7E  F0 D3 16 00  DC D3 16 00  00 00 00 00  ...~............
0033F070: 7C 14 EB 7E  00 39 B9 7E  00 00 00 00  CC C0 FD 7F  |..~.9.~........
0033F080: 20 BD B8 7E  E4 02 00 00  FF FF 00 00  BC F0 33 00   ..~..........3.
0033F090: 34 76 B4 7E  00 39 B9 7E  20 BD B8 7E  CC F0 33 00  4v.~.9.~ ..~..3.
0033F0A0: 20 BD B8 7E  01 00 00 00  E4 02 00 00  DC F0 33 00   ..~..........3.
0033F0B0: 04 76 B4 7E  00 39 B9 7E  E4 02 00 00  DC F0 33 00  .v.~.9.~......3.
0033F0C0: BC 31 B2 7E  E4 02 00 00  FF FF 00 00  0C F1 33 00  .1.~..........3.
0033F0D0: 20 BD B8 7E  00 00 00 00  20 BD B8 7E  0C F1 33 00   ..~.... ..~..3.
0033F0E0: 46 89 B2 7E  E4 02 00 00  85 1A 00 00  04 00 00 00  F..~............
0033F0F0: F2 0D A3 7D  04 00 00 00  38 F1 33 00  E0 54 A8 7D  ...}....8.3..T.}
0033F100: 19 96 FA 7E  60 30 A8 7D  60 30 A8 7D  4C F1 33 00  ...~`0.}`0.}L.3.
0033F110: F6 11 A3 7D  A0 54 A8 7D  85 1A 00 00  04 00 00 00  ...}.T.}........
0033F120: 3C F1 33 00  04 00 00 00  38 F1 33 00  4C F1 33 00  <.3.....8.3.L.3.
0033F130: 20 BD B8 7E  00 00 00 00  E8 8F 16 00  06 00 00 00   ..~............
0033F140: 04 29 C8 7E  F0 18 06 7C  E4 02 00 00  6C F1 33 00  .).~...|....l.3.
0033F150: 8C B6 C3 7E  00 00 00 00  E4 02 00 00  00 00 00 00  ...~............
0033F160: 90 9F 8F 7D  00 00 00 00  90 9F 8F 7D  AC F1 33 00  ...}.......}..3.
0033F170: 7F FE 88 7D  00 00 00 00  E4 02 00 00  04 00 00 00  ...}............
0033F180: 98 F1 33 00  04 00 00 00  9C F1 33 00  10 00 00 00  ..3.......3.....
0033F190: FE F4 88 7D  20 AD 8F 7D  00 00 00 00  F0 18 06 7C  ...} ..}.......|
0033F1A0: 90 9F 8F 7D  00 00 00 00  C8 D3 16 00  EC F1 33 00  ...}..........3.
0033F1B0: E6 5A 89 7D  C8 D3 16 00  F0 18 06 7C  A0 68 8E 7D  .Z.}.......|.h.}
0033F1C0: E8 8E 8E 7D  C8 D3 16 00  00 00 00 00  00 00 00 00  ...}............
0033F1D0: 14 F2 33 00  C8 D3 16 00  A4 AC 8F 7D  00 00 00 00  ..3........}....
0033F1E0: 1C 31 A7 00  1E 31 A7 00  55 F7 33 00  3C F2 33 00  .1...1..U.3.<.3.
0033F1F0: F4 34 91 7D  C8 D3 16 00  00 00 00 00  00 00 00 00  .4.}............
0033F200: 14 F2 33 00  28 D0 16 00  20 00 00 00  3C F2 33 00  ..3.(... ...<.3.
0033F210: 42 F8 90 7D  60 F2 33 00  60 F4 33 00  60 F6 33 00  B..}`.3.`.3.`.3.
0033F220: 80 F6 33 00  88 F6 33 00  8C F6 33 00  90 F6 33 00  ..3...3...3...3.
0033F230: 94 F6 33 00  98 F6 33 00  A8 F6 33 00  60 F8 33 00  ..3...3...3.`.3.
0033F240: 91 36 58 00  28 D0 16 00  00 00 00 00  00 00 00 00  .6X.(...........
0033F250: 60 F2 33 00  1E 31 A7 00  00 00 00 00  1C 31 A7 00  `.3..1.......1..
0033F260: 08 18 D6 00  B0 F4 33 00  C7 1E 64 00  D8 8B A7 00  ......3...d.....
0033F270: 16 82 64 00  C0 A0 E0 00  77 C1 64 00  A8 7B 83 00  ..d.....w.d..{..
0033F280: 00 00 00 00  03 00 00 00  00 00 00 00  00 00 00 00  ................
0033F290: 80 02 00 00  E0 01 00 00  20 00 00 00  4B 00 00 00  ........ ...K...
0033F2A0: 80 02 00 00  E0 01 00 00  20 00 00 00  49 00 00 00  ........ ...I...
0033F2B0: 80 02 00 00  E0 01 00 00  20 00 00 00  3C 00 00 00  ........ ...<...
0033F2C0: 80 02 00 00  E0 01 00 00  10 00 00 00  4B 00 00 00  ............K...
0033F2D0: 80 02 00 00  E0 01 00 00  80 F3 33 00  00 00 00 00  ..........3.....
0033F2E0: A4 F3 33 00  09 0A DC B7  00 00 00 00  B0 F3 33 00  ..3...........3.
0033F2F0: 09 0A DC B7  00 02 00 00  20 00 00 00  4B 00 00 00  ........ ...K...
0033F300: 80 02 00 00  00 02 00 00  20 00 00 00  3C 00 00 00  ........ ...<...
0033F310: 80 02 00 00  64 F3 33 00  03 00 00 00  00 10 00 00  ....d.3.........
0033F320: F9 EE D4 B7  01 00 00 00  F9 EF FD 7E  53 74 17 7C  ...........~St.|
0033F330: 43 00 00 00  01 00 00 00  54 74 17 7C  43 00 00 00  C.......Tt.|C...


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     772

Percent memory used:    13
Total physical memory:  527802368
Free Memory:            309657600
Page file:              1274904576
Total virtual memory:   2147352575


If anyone has any idea how to help, please tell me.

---

### Post by AJLChase on 2006-08-24
I'm getting very frustrated. To start, WoW worked fine. Well, it had some slight lagg to it. But hey, it worked. Well, I had to exit out of X and then was told while trying to get back in that X was set up incorrectly. So I typed sudo dpkg-reconfigure xserver-xorg and it went through and took care of  X so I could log back in...but then bam all of a sudden WoW got this error saying it didn't have enough memory. Wich I beleive I know why, during X setup I didn't put in the memory on my gfx card. 

Well before I caught onto that, I decided to reinstall Wine to see if that helped now I get an error while trying to click the WoW installer.exe I get an error saying Couldn't display "/home/name/Desktop/WoW/Installer.exe". Now is there anyway I can get this all to go backwards, and start fresh. I used [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) to install Wine and WoW the first time and it worked......the guide from Kidcharles is over my head, when I try to make the patches go where they're suppose to go...it doesn't work. So please any help would be greatly appreciated.

---

### Post by tokyovigilante on 2006-08-24
> **autrui said:**
> after giving up out of frustration for the night, i'm back on this morning. i believe i've got the xorg.conf right, but, having gone back to the original post to continue this process, i get the same error when i run winecfg:
```
$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

``` 
here's the lspci:
and here's the cat /etc/X11/xorg.conf

i'm running a Dell GX270, 1gig ram (2x512), 3.2ghz, 200gig sata HD (with Ubuntu 6.06LTS on it) and a 250gig IDE (NTFS); ATI Radeon x1300pro; samsung syncmaster930b monitor, and a Braun KF590e.

any idea where to go from here?  

thanks,

autrui
I guess to check that the ATI drivers are running by running glxgears at the command prompt. Other than that I guess make sure that your X server is running - I assume you are trying to run winecfg from the Gnome/KDE terminal?

If that doesn't work I suggest flagging this guide and following the instructions for Ubuntu at the [www.winehq.org](www.winehq.org) Wiki.

---

### Post by tokyovigilante on 2006-08-24
Everyone seems to be having similar issues following this guide, So I'm just going to write a current one for Ubuntu 6.06 LTS/Kubuntu 6.06 LTS,  Wine 0.9.19, and WoW 1.12.0. 

I'll put it up in the main gaming forum and link it here.

THIS GUIDE IS OUT OF DATE!!!!

---

### Post by tokyovigilante on 2006-08-24
[As promised...]("http://ubuntuforums.org/showthread.php?p=1419085")

---

### Post by relux on 2006-08-25
> **smaugslayer said:**
> I followed the latest instructions for installing the wow patched version of wine.  However, when I try to install wow, I get the following error:


Sorry the installer could not be initialized
Unrecognized key "options". (AttributeParser::Parse)


I had this same issue. I found the way to fix it is to copy the Installer.exe from the first cd and run that. Hope this helps.

---

### Post by roguenoir on 2006-08-26
I installed WoW using wine 0.9.20 and I can enter the game fine.  However, my FPS is about 3 - 10.  (In windows, I'm usually getting 20 - 40 fps) Yes, I'm running with the -opengl flag.  And my video card is an NVidia, running the upgraded drivers installed using the Envy script.  I've also tried running using wine 0.9.19 and am still getting these horrible frame rates.  Can anyone point me to where something might be wrong?    Thanks.

---

### Post by eqisow on 2006-08-26
All I can recomend is playing around with your Wine and WoW settings.

However, if you were only getting 20-40 fps in Windows you may not be able to get anything playable in Wine.

---

### Post by roguenoir on 2006-08-26
Tried playing around with the settings in Config.wtf to no avail.

Are there any configuration files for Wine that are not updated from winecfg that may be of importance?

---

### Post by ctrlz on 2006-08-27
I cannot run WoW with the opengl flag. I can't figure out why! I feel like I've tried everything. Commenting and uncommenting dri from xorg.conf and restarting xorg. Running glxgears -info gives me 2000+ framerates. When I run  "wine WoW.exe -opengl", I get a bunch of errors in the command-line, and then WoW spits back an error saying it can't start 3D acceleration.

I'm running wine 0.9.20.

I guess the main problem is figuring out how to get direct rendering set to on.

```
glxinfo | grep direct
direct rendering: No

```

Is what I get. Any help would be appreciated! Thanks.

---

### Post by eqisow on 2006-08-27
ctrlz, post the contents of your /etc/X11/xorg.conf file please.

---

### Post by ctrlz on 2006-08-28
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel"   "true"
    	Option          "TripleBuffer" "true"
        Option          "NoLogo" 
	#VideoRam	128
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by tokyovigilante on 2006-08-28
> **ctrlz said:**
> ```
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
#    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "TripleBuffer" "true"
        Option          "NoLogo" 
    #VideoRam    128
EndSection

Section "Monitor"
    Identifier    "SyncMaster"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

```
That superficially looks ok, but the nvidia-glx package may have issues. Try reinstalling nvidia-glx, and your kernel and restricted-modules. If you want the latest drivers, try tseliot's excellent envy script - [http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by Allrab on 2006-08-30
I find it tricky. Im a noob i will agree to that but I would actually like to see the procedure to instal this.
For instance I dowloaded this to my desktop but could not run the commands in terminal so I had to set the properties of the files to be run and then open in terminal.
I then extracted the files to my desktop so my wine folder is on my desktop. Next thing to do  is to go to the \etc folder but what do i write to make a text file?
I am completely new to Ubuntu 6.06 or Ubuntu and have used windows all my life.

I belive this walkthrughis for advanced users and I dont understand half of it. What is wrong with getting wine from synaptic etc?

Please is there a walkthrugh for noobs because I would love that very much. a Step by step guide how to write etc in each step. I guess that is to much to ask but I would apreciate that.
If someone would have the time to lead me thrugh this by MSN(Gaim) or so I would apreciate this...

Looking for a teacher I guess...

/Allrab

---

### Post by tokyovigilante on 2006-08-30
> **Allrab said:**
> I find it tricky. Im a noob i will agree to that but I would actually like to see the procedure to instal this.
For instance I dowloaded this to my desktop but could not run the commands in terminal so I had to set the properties of the files to be run and then open in terminal.

I see from your other posts you have had trouble using the terminal. This is an absolute necessity for getting WoW running. You need to open a terminal session from the Applications menu, and then the guide should be an exercise in cutting and pasting. Just work through it logically. Your password to log into the system IS your administrator password.
> **Allrab said:**
> 
I then extracted the files to my desktop so my wine folder is on my desktop. Next thing to do  is to go to the \etc folder but what do i write to make a text file?

Again the commands in the Howto are quite clear, and need to be pasted into the kernel.
> **Allrab said:**
> 
I am completely new to Ubuntu 6.06 or Ubuntu and have used windows all my life.
 Fair enough, we all start somewhere. The most important thing to remember is have patience and think logically. People on the forum, including me, are more than happy to offer help to those who help themselves.
> **Allrab said:**
> 
I belive this walkthrughis for advanced users and I dont understand half of it. What is wrong with getting wine from synaptic etc?

I intended this guide to be for "noobs" as you say, although noob is a derogatory term. There's nothing wrong with being new to Linux. You've obviously managed to set up a desktop, well done! It takes time to get used to the differences between Linux and Windows.
The version of wine in synaptic (0.9.6) is too old to run WoW, hence this howto. Also, if you are an NVIDIA user, then you need a patched version anyway.
> **Allrab said:**
> 
Please is there a walkthrugh for noobs because I would love that very much. a Step by step guide how to write etc in each step. I guess that is to much to ask but I would apreciate that.
This is pretty much as uncomplicated as it gets. Just work through it as best you can, and remember not to go on to the next step unless the previous one has been successful, otherwise you're wasting your time. Post your problems as you have them instead.
> **Allrab said:**
> 
If someone would have the time to lead me thrugh this by MSN(Gaim) or so I would apreciate this...

Looking for a teacher I guess...

/Allrab
That is too big an ask for me anyway, someone else might be happy to. A far better way would be to work through the howto, and ask questions in a public forum so that more eyes can see the problems and respond to them, and so that others can see the problems you've had and help fix their own.
Try [my howto]("http://ubuntuforums.org/showthread.php?t=243336"), hopefully it's a little bit clearer.

---

### Post by Allrab on 2006-08-31
Thank you, I will take it easy but my patience is a bit limited. I do however want to learn so that is a good thing. I will try to do this again :D

I got stuck when I have to create thefile with a text editor in /etc called ld.so.conf contatining the  /usr/local/lib

I just stand in terminal /etc$

I do not know what command to use to create this file.

/allrab

---

### Post by Seine on 2006-08-31
G'day

I'm a fresh Ubuntu user and will attempt this tonight. I have some questions first though.

The guide was written back in January. Should I be concerned that the version of wine being patched is 0.9.6 and the current release is 0.9.20?

I've copied the wow files from the NTFS share to /opt/wow. Is this location OK? Is it "best practice"?

Thanks for listening!
Jem

---

### Post by tokyovigilante on 2006-08-31
> **Allrab said:**
> Thank you, I will take it easy but my patience is a bit limited. I do however want to learn so that is a good thing. I will try to do this again :D

I got stuck when I have to create thefile with a text editor in /etc called ld.so.conf contatining the  /usr/local/lib

I just stand in terminal /etc$

I do not know what command to use to create this file.

/allrab
I really think you should use [my guide]("http://www.ubuntuforums.org/showthread.php?t=243336"). This one is out of date.

---

### Post by tokyovigilante on 2006-08-31
> **Seine said:**
> G'day

I'm a fresh Ubuntu user and will attempt this tonight. I have some questions first though.

The guide was written back in January. Should I be concerned that the version of wine being patched is 0.9.6 and the current release is 0.9.20?

Yes. Use [mine]("http://www.ubuntuforums.org/showthread.php?t=243336"), which is current for 0.9.20.
> **Seine said:**
> 
I've copied the wow files from the NTFS share to /opt/wow. Is this location OK? Is it "best practice"?

Thanks for listening!
Jem
It's probably better in your home directory as the patcher needs write access to the location.

---

### Post by hikaricore on 2006-09-01
patched 0.9.20 [http://thepiratecove.org/files/wine-0.9.20_wow_i386.deb]("http://thepiratecove.org/files/wine-0.9.20_wow_i386.deb")bails out with this:

> 
 X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  449
  Current serial number in output stream:  449


removed 0.9.20 and reverted to 0.9.19 [http://thepiratecove.org/files/wine-0.9.19_wow_i386.deb]("http://thepiratecove.org/files/wine-0.9.19_wow_i386.deb")  and wow starts normally *sigh*  was hoping to see some helpful changes lol

---

### Post by SishGupta on 2006-09-03
i get this too and i hear it will be fixed in .21

---

### Post by simplyw00x on 2006-09-03
This application has encountered a critical error:
> ERROR #132 (0x85100084)
Program: C:\world\WoW.exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:B7CF2DA0

The instruction at "0xB7CF2DA0" referenced memory at "0x00000000".
The memory could not be "read".
I've had it running really well for weeks, but after the most recent patch I get this error the whole time as well on trying to start the game. This error only occurs with OpenGl, with D3D it's fine (but the game is unstable and slow). Any help?

---

### Post by Immorten on 2006-09-03
I have the exact same problem as Simplyw00x. I'm getting into WoW, but I can't change stuff in the video option. And somehow, everything there is maxed. That's crap, because it gives me a stunning 2-4 fps =/

---

### Post by hikaricore on 2006-09-03
> **Immorten said:**
> I have the exact same problem as Simplyw00x. I'm getting into WoW, but I can't change stuff in the video option. And somehow, everything there is maxed. That's crap, because it gives me a stunning 2-4 fps =/

load the game in direct3d mode "if possible" and edit the video settings there.  it may be nearly unplayable in this mode but if you're dead set on getting it working logging in for a few minutes _just_ to change the settings then logging out won't kill you :P

wine Wow.exe -d3d

---

### Post by DrunkenSheep on 2006-09-03
cartman@cartman:~/Desktop/wine-0.9.6/wine-0.9.6$ wine
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory

:( something is wrong...

---

### Post by tokyovigilante on 2006-09-04
> **DrunkenSheep said:**
> cartman@cartman:~/Desktop/wine-0.9.6/wine-0.9.6$ wine
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory

:( something is wrong...
Yeah, you're using 0.9.6, you need at least 0.9.18, latest version is 0.9.20. Look [here]("http://www.ubuntuforums.org/showthread.php?t=243336").

---

### Post by -Race- on 2006-09-04
After using the command
wine WoW.exe -opengl
The game doesnt load but the terminal shows this
wine:could not load L"c:\\windows\\system32\\WoW.exe":Module not found. 
What to do here?

---

### Post by Seine on 2006-09-04
This happened to me. Try running as root.

sudo wine WoW.exe -opengl

---

### Post by eqisow on 2006-09-05
Did you just suggest running an internet enabled Windows app in root mode? Come now, use a little common sense please.

The problem I see is that you're not actually typing the path to the executable. It should be:
```
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
```

---

### Post by girkid920 on 2006-09-05
hello .. im not new at linux .. ive used linux for 3 years lol just before it was mostly work related stuff .. now im trying to get games running in my linux system .. Im running ubuntu dapperdrake 6.06 ive installed cedega 5.1 and i installed WoW .. the installation of it went fine other then the error at the end which i discovered from previous forums is a big deal .. but when i go to run WoW in cedega nothing happens .. so i run it again in a terminal and what i get is not a great game to kill my life with but an error message that looks like this :

 For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
tid 5342 received signal 11. Raising signal 3
/home/dave/.cedega/.winex_ver/winex-5.1.1/bin/winex3: line 374:  5336 Quit               $SHELL -c "$RUNWINE $FULL_COMMAND_LINE"


i have know idea wut to do next .. so if anyone can help me that would be great !!

---

### Post by girkid920 on 2006-09-05
hello .. im not new at linux .. ive used linux for 3 years lol just before it was mostly work related stuff .. now im trying to get games running in my linux system .. Im running ubuntu dapperdrake 6.06 ive installed cedega 5.1 and i installed WoW .. the installation of it went fine other then the error at the end which i discovered from previous forums is a big deal .. but when i go to run WoW in cedega nothing happens .. so i run it again in a terminal and what i get is not a great game to kill my life with but an error message that looks like this :

For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
tid 5342 received signal 11. Raising signal 3
/home/dave/.cedega/.winex_ver/winex-5.1.1/bin/winex3: line 374: 5336 Quit $SHELL -c "$RUNWINE $FULL_COMMAND_LINE"


i have know idea wut to do next .. so if anyone can help me that would be great !!

---

### Post by girkid920 on 2006-09-05
im running cedega 5.0 and im trying to install and run WoW on my Ubuntu dapperdrake Linux box .. it installs fine but when i go to run it .. it doesnt pop up so i go to run it in a terminal ans i get this error:

For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
tid 6571 received signal 11. Raising signal 3
/home/dave/.cedega/.winex_ver/winex-5.1.1/bin/winex3: line 374:  6565 Quit               $SHELL -c "$RUNWINE $FULL_COMMAND_LINE"

can some one help ! lol :D

---

### Post by Jorenko on 2006-09-07
I've been enjoying WoW for months now by using the guide in the first post of this thread. However, as of today I am not able to play. After logging in, it pops up a "downloading..." dialog, then the screen starts to flash quickly between all black and the login display with the downloading box.

If I press enter here, I hear the 'Entering World' sound as if I've selected a character, and people in my guild see me log in. Eventually, it starts displaying badly distorted graphics and soon after the game crashes  with an access violation.

A few things have changed about my configuration in the past two days that could be the cause. I've tried to rectify them all and I thought I'd done a good job, but I must be missing something else:

1. In order to try out EVE-Online, I tried setting up cvscedega with WineCVS.sh. It installed with all defaults and no errors*, but EVE didn't work. No big deal there though.

* There was one minor error that I worked around: WineCVS assumes that you can su into root to run commands and doesn't provide for sudo. I worked around this by editing the section that uses su to just run the commands instead, and I ran WineCVS through sudo. This seemed to work fine.

2. I installed seven automatic updates. Unfortunately I don't know what they were, and I haven't been able to find any sort of udpate history on my system. I have universe and multiverse enabled on all the standard repos, and I have a few packages (mplayer, etc) installed from non-standard repos (all this stuff came from automatix), but I've purged all nonstandard repos from my sources list ever since the compiz repos broke gnome.

3. I booted into windows, deleted WoW from my windows partition, since I never play it there anymore, moved some files around, and booted back into ubuntu.

After installing cvscedega and before installing the updates, I was able to play WoW just fine. Upon booting back into ubuntu from windows was the first time I tried WoW since that, and also the first time I got this problem.


My steps so far to try to fix this:

1. Uninstall cvscedega (I accomplished this by running the same profile in WineCVS that I used to install it, then ctrl-c-ing it after the uninstall and clean up stages)
2. I still have the source folder for wine from when I built it originally, unchanged. I ran sudo make install to reinstall the files in the same version they had been when it worked.
3. I ran sudo make uninstall, then sudo make install again for my old wine again.

None of these worked, and I still have the same symptom.

Can anybody help me either back out the updates I installed, or have any other ideas about what could cause this?

Thanks

Edit: Here's the entire command-line output of running WoW.

```

fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c900000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c900000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbceeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

---

### Post by Euler on 2006-09-08
I have the same problem as you.  The only thing I remember having done is upgrading my system, and here are the package I did upgrade (I haven't closed the terminal yet :)) : 

  bind9-host dnsutils libbind9-0 libdns21 libisc11 libisccc0 libisccfg1
  liblwres9

I play regularly WoW, so I haven't made much more changes to my system.  I think the problem comes from one of those libraries.  I will try to find a way to reinstall the older ones, and I'll post here if I find a solution.

Euler

---

### Post by RotoGrip on 2006-09-08
Sorry if i missed while searching. But are you able to use add-on's, for instance i use Gaterer, Atlas, and Titan panel. Also how about sound? Ubuntu seems to be famous for sound not working properly. This has kept me from deleting windows.

Thanks

---

### Post by MemoryDump on 2006-09-08
I know it's why I havent' switched completly.. I run WinXP right now ince WOw runs no problems/all the time. Don't get me wrong I love Linux/Ubuntu.. it's just there's just too many little annoyances still bugging me :P

how has sound been playing WoW under Linux? (for those who actually have this running)
screen resolution? (can you max out your settings if you have one of the newer video cards)

---

### Post by sgtBiafra on 2006-09-08
I play WoW exclusively on my Dapper install. Last night when I attempted to login I received something similar to Jorenko's problem (a fluttering login screen with the Downloading message displayed... not sure if it ever logged me into the server).

I thought back a short while ago to the point when they pushed the hardware survey (that caused a crash during login) and attempted to adjust the permissions on the WTF folder to no avail. I then checked what version of WINE I had been running and it was a bit dated (I believe it was a patched version of 0.9.14).

Since I was down for the count already, I decided to reinstall and update WINE following the directions on the first page of this post ([http://www.ubuntuforums.org/showthread.php?t=243336)](http://www.ubuntuforums.org/showthread.php?t=243336)). I ended up with v0.9.20 (with the nVidia patch) up and running. Just to be thorough, I then archived my Config.wtf settings file and cleared it down to the bare essentials. 

All in all, this got me up and running again and even fixed up the problems I had with the mini-map crash. I don't know if this will fix everyone's issues but I thought I'd relate my experience.

**Edit:** MemoryDump, I haven't had any real issues (besides some crackles now and again) with sound under Ubuntu using integrated sound on my motherboard. As far as graphics go, it's smooth on my system on a 7800GS at 1920x1200 though granted I'm not pushing things (AA off, full screen glow/death effect off and no vertical sync).

---

### Post by imlost on 2006-09-09
> **Jorenko said:**
> I've been enjoying WoW for months now by using the guide in the first post of this thread. However, as of today I am not able to play. After logging in, it pops up a "downloading..." dialog, then the screen starts to flash quickly between all black and the login display with the downloading box.

If I press enter here, I hear the 'Entering World' sound as if I've selected a character, and people in my guild see me log in. Eventually, it starts displaying badly distorted graphics and soon after the game crashes  with an access violation.

A few things have changed about my configuration in the past two days that could be the cause. I've tried to rectify them all and I thought I'd done a good job, but I must be missing something else:

1. In order to try out EVE-Online, I tried setting up cvscedega with WineCVS.sh. It installed with all defaults and no errors*, but EVE didn't work. No big deal there though.

* There was one minor error that I worked around: WineCVS assumes that you can su into root to run commands and doesn't provide for sudo. I worked around this by editing the section that uses su to just run the commands instead, and I ran WineCVS through sudo. This seemed to work fine.

2. I installed seven automatic updates. Unfortunately I don't know what they were, and I haven't been able to find any sort of udpate history on my system. I have universe and multiverse enabled on all the standard repos, and I have a few packages (mplayer, etc) installed from non-standard repos (all this stuff came from automatix), but I've purged all nonstandard repos from my sources list ever since the compiz repos broke gnome.

3. I booted into windows, deleted WoW from my windows partition, since I never play it there anymore, moved some files around, and booted back into ubuntu.

After installing cvscedega and before installing the updates, I was able to play WoW just fine. Upon booting back into ubuntu from windows was the first time I tried WoW since that, and also the first time I got this problem.


My steps so far to try to fix this:

1. Uninstall cvscedega (I accomplished this by running the same profile in WineCVS that I used to install it, then ctrl-c-ing it after the uninstall and clean up stages)
2. I still have the source folder for wine from when I built it originally, unchanged. I ran sudo make install to reinstall the files in the same version they had been when it worked.
3. I ran sudo make uninstall, then sudo make install again for my old wine again.

None of these worked, and I still have the same symptom.

Can anybody help me either back out the updates I installed, or have any other ideas about what could cause this?

Thanks

Edit: Here's the entire command-line output of running WoW.

```

fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c900000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c900000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbceeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

Really easy fix to that... so easy you are going to hate me. Go to your WoW directory and open the properties window on your WDB folder and change the permissions so no one has permission to do anything but view the files... not executing and not write ability... then reload the game and you should be fine.

---

### Post by Jorenko on 2006-09-09
> **imlost said:**
> Really easy fix to that... so easy you are going to hate me. Go to your WoW directory and open the properties window on your WDB folder and change the permissions so no one has permission to do anything but view the files... not executing and not write ability... then reload the game and you should be fine.

On the contrary, I love you! That worked perfectly, thanks!

Any chance you can tell me WHY that works? I like to understand these types of things, and this is a pretty mysterious fix.

---

### Post by saxin on 2006-09-11
It's been a long time since I got WoW up and running with wine now. I downloaded a .deb file that was already patched for WoW. 

Is it possible to play WoW now, with the offical "clean" wine? If so, are the wine in the rep updated enough to fix WoW? Which version do I need to get it working?

---

### Post by zoro on 2006-09-13
*subscriber mark*

---

### Post by JermCool on 2006-09-29
Is there anyone out there who can make WoW 1.12.1 run on wine with an ATI Radeon 9200 in openGL?  Everything I've seen out there says it lasts for 5-7 minutes and then runs out of video RAM - the exact problem I've been having.

I've tried it on the patched wine 0.9.21 and the unpatched wine 0.9.22

If I have to go to a previous version of wine, I'll bloody do it.  I'm having WoW withdrawls.  I've had to pull out of four raids now and my DKP is dropping through the floor.

---

### Post by Hawkowl on 2006-11-03
I've tried installing WoW just as described on the first page, and all seemed well.
Istarted it and it ran fine, even showed the movie intro, but as soon as it gets to the terms of use page, it freezes!
Anyone else having this problem?
The video card is an onboard s3 Unichrome Pro, from VIA Tech. with 64 MB ram.
Any feedback would be appreciated.

---

### Post by Ferrat on 2006-11-03
> **Hawkowl said:**
> I've tried installing WoW just as described on the first page, and all seemed well.
Istarted it and it ran fine, even showed the movie intro, but as soon as it gets to the terms of use page, it freezes!
Anyone else having this problem?
The video card is an onboard s3 Unichrome Pro, from VIA Tech. with 64 MB ram.
Any feedback would be appreciated.

What version of Ubuntu are you running? 

What version if Wine?

---

### Post by Hawkowl on 2006-11-03
I'm using the latest ubuntu dapper drake and also using the latest wine 0.9.10.
I have just gone through and did the entire thing again.
The only thing that doesn't seem to go exactly as described is when i'm patching the files, in particular the second patch, it stops and asks me what files to patch.
I just select the file it had stopped at, this happened both times i did the walkthrough, i wonder if that means anything?
i have also fooled around with different resolutions, right down to 800x600 still freezes at the same spot, at the terms of use.
any ideas what it might be?

---

### Post by Ferrat on 2006-11-03
> **Hawkowl said:**
> I'm using the latest ubuntu dapper drake and also using the latest wine 0.9.10.
I have just gone through and did the entire thing again.
The only thing that doesn't seem to go exactly as described is when i'm patching the files, in particular the second patch, it stops and asks me what files to patch.
I just select the file it had stopped at, this happened both times i did the walkthrough, i wonder if that means anything?
i have also fooled around with different resolutions, right down to 800x600 still freezes at the same spot, at the terms of use.
any ideas what it might be?


lastest wine is 0.9.24 

but easiest to setup for wow is 0.9.23 

check out [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

---

### Post by Hawkowl on 2006-11-04
Ahh sorry, thanks, i'll check it out.
I'm wondering wether or not the onboard video card in this sempron is just not good enough for WoW.
What do you think?
Its an onboard VIA s3 Unichrome Pro with 64 mb Ram.

---

### Post by stryve on 2006-11-04
```
gcc -c -I. -I. -I../../include -I../../include  -DINCLUDEDIR="\"/usr/local/include/wine\""  -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o lex.yy.o lex.yy.c
lex.yy.c:2610: error: expected ‘;’, ‘,’ or ‘)’ before numeric constant
make[2]: *** [lex.yy.o] Error 1
make[2]: Leaving directory `/home/stryve/Desktop/wine-0.9.6/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/stryve/Desktop/wine-0.9.6/tools'
make: *** [tools] Error 2

```

im getting this error while trying to install wine, any suggestions? i've never really had any problems installing wine before but this is my first go at ubuntu

---

### Post by Ferrat on 2006-11-04
> **Hawkowl said:**
> Ahh sorry, thanks, i'll check it out.
I'm wondering wether or not the onboard video card in this sempron is just not good enough for WoW.
What do you think?
Its an onboard VIA s3 Unichrome Pro with 64 mb Ram.

Depends a bit on if it's integraded memory or dedicated to the grafic only and how much ram you have but 64 is in the low corner but it should work if you don't use shaders and run it on low graficsettings

---

### Post by epikos on 2006-11-06
So, I wonder if ANYONE has this working in OPENGL on older ATI radeon hardware? With all the errors everyone has posted, I've only see one with the same error I get.

It works fine in d3d except for the slow fps and busted textures. As soon as I launch -opengl, it tries to load and crashes with wow error 132. I've erased the config.wtf file, and I've tried making a new one with just the resolution, color depth, and refresh rates, and nothing helps. This is on a mobility radeon 9000 with working ati drivers and 3d acceleration. 

I installed the pre-patched wine .deb and copied from my XP box. I just can't get it to do anything in opengl.

So... can anyone help me? Pretty please?

---

### Post by doktor_p on 2006-11-07
hi folks!
i installed wine from the patched .deb in found in the howto (version 0.9.21_wow_i386.deb), then copied the content of all wow cds in a dir on my HD and installed it from there.
although i couldn't read properly the eula and other writings during the installation process it worked just fine, with no error messages.
anyway when launching wow with the command ```
wine WoW.exe
``` once inthe wow directory i get this reply:
```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d350000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d350000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

```

if should want to have  look this is my config.wtf:
```
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET realmList "eu.logon.worldofwarcraft.com"
SET SoundOutputSystem "2"
SET SoundBufferSize "150"
SET gxApi "OpenGL"

```
i also tried soundoutputsystem "1" and "-1" and soundbufersize "100"
what's wrong???
i'm on dapper, with a radeon igp 340m (64MB ram) with mesa/DRI drivers and direct rendering enabled.
please help obi wan kenobi, you're my last hope...

---

### Post by UchihanoKonoha on 2006-11-08
> Get the two patch files needed, and place them in the top directory of the source files:
[http://kaspersandberg.com/~redeeman/...e-cvs-glx.diff](http://kaspersandberg.com/~redeeman/...e-cvs-glx.diff)
[http://kaspersandberg.com/~redeeman/...ow-fixes.patch](http://kaspersandberg.com/~redeeman/...ow-fixes.patch)


these links you have given seem to be broken links all i see is a bunch of code once i see the page, no download prompt is given, how else can i get these patches?

---

### Post by Tantalus90 on 2006-11-08
> **UchihanoKonoha said:**
> these links you have given seem to be broken links all i see is a bunch of code once i see the page, no download prompt is given, how else can i get these patches?

google is your friend 

or try here [http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

---

### Post by Angel69 on 2006-11-09
hi
 im using kubuntu 6.10 and wine from Adept manager version 0.9.22

i installed wow without this instruction and without any dlls
its works good, but i have some lagging in game when i turning around fast

is it wine problem or not?

---

### Post by PisstMSTRCHIEF on 2006-11-18
I have the same issue.....](*,)

---

### Post by PisstMSTRCHIEF on 2006-11-18
> **Angel69 said:**
> hi
 im using kubuntu 6.10 and wine from Adept manager version 0.9.22

i installed wow without this instruction and without any dlls
its works good, but i have some lagging in game when i turning around fast

is it wine problem or not?

Oh, I was messing with the settings and if you turn down the distance you see in wow, the lag goes away. hope this helps

---

### Post by appdx on 2006-11-18
when I try to do

```

cd ~/.wine/drive_c/Program\ Files/World\ Of\ Warcraft/WTF/ 
cp Config.wtf Config.wtf.backup 
gedit Config.wtf
```

I get

```

cp: cannot stat `Config.wtf': No such file or directory
```

If I try to just play it after the cut-scene I get this
```

fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; 
STUB Exceeded max nr indirect texture lookups DRM_I830_CMDBUFFER: -22
```

---

### Post by mootzchee on 2006-11-20
[For World of Warcraft Cheats, Exploits, Dupes, and Hacks, click here.](http://www.exploitsrus.org/wow.html) It is a great site for World of Warcraft Cheats, Exploits, Dupes, and Hacks [http://www.exploitsrus.org/wow.html](http://www.exploitsrus.org/wow.html)

---

### Post by saintbe on 2006-11-23
I've installed Wine and installed WoW.

I checked the WTF directory but it is empty ... there is no config file in it ... should I just create it ?

When I start WoW I get to the login page but the patching fails every time.

I followed the instruction from [https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28world%29%7C%28of%29%7C%28warcraft%29](https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28world%29%7C%28of%29%7C%28warcraft%29)
However this howto only speaks of 1 .dll file.

I'm running this on an older system.  AMD Athlon 2800+ with GeForce2 and 512 DDR.
Running Ubuntu 6.10 (Edgy).

---

### Post by Kelnoky on 2006-11-23
My audio tab in the winecfg crashes the whole thing. But the suggested command for that problem:

```
sudo mv /usr/local/libs/wine/winearts.drv.so /usr/local/libs/wine/winearts.drv.so.backup
```

only tells me "mv: cannot stat `/usr/local/libs/wine/winearts.drv.so': No such file or directory"

-.-
So, something wrong with my wine installation? Maybe - I installed it from synaptic (but after adding the right repository to my sources.lst) and synaptic tells me that I got 0.9.25 installed - but in the winecfg tab "about" it says that I got 0.9.21. So what's the case now?

In addition to that my biggest problem is, that I can start World of Warcraft, login to my account but when I try to login to a realm with my character I get three to four seconds of normal game and then *everything* freezes. The whole Ubuntu crashes and I cant input anything. Any solutions?

(btw. I'm running Ubuntu edgy with an ATI X800 and fglrx from the repositories)

---

### Post by Afteraffekt on 2006-12-04
I used the

[http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft)

howto and I can get the launcher up, but it acts like it will work, then I get a wow error and thats it...

---

### Post by Sammi on 2006-12-04
That howto is ok, but I would like to ask you to try this howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

It's an old document that I've tried to update.

If you want detailed info then this Gentoo howto is also pretty good: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

Hope something works ;)

---

### Post by NerdyShinobi on 2006-12-11
Ok, this all seems well and good, but my question is (and I am sorry if my search-fu missed this): Is there a way to SHARE a single installation of WoW between a Windows and Ubuntu on the same machine?  I want to dual-boot when I reinstall Ubuntu again (until I see if this works, natch) and want to conserve space if at all possible.

---

### Post by Drezliok on 2006-12-12
> **NerdyShinobi said:**
> Ok, this all seems well and good, but my question is (and I am sorry if my search-fu missed this): Is there a way to SHARE a single installation of WoW between a Windows and Ubuntu on the same machine?  I want to dual-boot when I reinstall Ubuntu again (until I see if this works, natch) and want to conserve space if at all possible.

Yeah, you can share it. All you have to do is install WoW in windows and make all the Wine adjustments that are needed. then it would be best to make a launch script to the game for you Ubuntu.

I did this myself, I wanted to see which was going to work better, windows or Wine. Bonus was that my girlfreind who plays won't complain about linux. [I'm trying to ease her to it and it's working, but gaming is the big jump.]

Here's my command if I ran it from the terminal.
```
wine /media/sda5/games/World\ Of\ Warcraft/WoW.exe -opengl
```
sda5 is my shared window partitian and I needed Ubuntu to have write permission so I made the drive Fat32. Infact all myn windows drives are fat32 to make this easier.

PS
It runs slightly better for me in Linux on wine than it does on Windows. Partly because I use Xubuntu and have it run on a dedicated xserver. Frees up more memory for the game than it does for windows.
[the bottle neck for my preformance is my vidcard geforce 5200 just can't dish out enough anymore[

---

### Post by TDsai on 2006-12-28
when i try to change settings inside the game it crashes when i click ok or apply. is there a file maybe or is it in Config.wft where i can manually set these settings like disable some effects, shadows, details, and draw distance?

---

### Post by Sammi on 2006-12-28
WoW crashes if you try to change settings while running in opengl mode. What you have to do is run it in d3d mode, change the settins, and then run it again in opengl as usuall.

You can do this by editing this line in /path-to-wow/WTF/Config.WTF:
```
SET gxApi "OpenGL"
```From "OpenGL" to "d3d", run the game and change the settings, and then change the line back :)

If you can't find the line then just add it. The game may look strange while running in d3d mode, but the only thing that matters is that you are able to run it, log in, and change the setting.

---

### Post by Poka64 on 2007-01-02
Is it normal that WoW uses 97-100% of the cpu resources when Wine runs it?

---

### Post by Sammi on 2007-01-02
I don't really know myself. It runs at 100% at all times for me :-k

I have a Dell Inspiron 9300 laptop with a 1.7 centrino 1 gb ram and a Geforce 6800. I wonder if it behaves the same on systems with higher spesificcations, or even if systems with lower specifications run on less cpu use.

But hey, it's not bothering me :-D

---

### Post by Poka64 on 2007-01-02
> **Sammi said:**
> I don't really know myself. It runs at 100% at all times for me :-k

I have a Dell Inspiron 9300 laptop with a 1.7 centrino 1 gb ram and a Geforce 6800. I wonder if it behaves the same on systems with higher spesificcations, or even if systems with lower specifications run on less cpu use.

But hey, it's not bothering me :-D

I've got a AMD64 3200+,1GB ram and nvidia 6600gt :)

---

### Post by Poka64 on 2007-01-03
How do I apply AA and AF in WoW, I tried the first suggestion in this thread but it doesn't seem to work :(

> LOADING NVIDIA SETTINGS

If you have an nvidia card, you may notice that until you use nvidia-settings during your session, your antialiasing and anisotropic filtering will not be activated. My method to activate these automatically is to start WoW with a script. To create this script, just make a file (mine is named simply 'wow') with the following lines (you can use gedit or other editor):

nvidia-settings --load-config-only
cd '/path/to/World of Warcraft'
wine WoW.exe -opengl


---

### Post by Sammi on 2007-01-04
I'm not at my own computer right now, so I cant' check, but isn't it possible to change these settings in game?

The game might crash if you change video settings while in opelgl mode. Run the game with the -d3d flag instead of -opengl or if you set opengl in your config.wtf, just change in to d3d, run the game, change the video settings, and change your config.wtf back.

---

### Post by martianc on 2007-01-04
Kelnoky, I am also running ATI graphix and have problems with WoW like you do. I'm also having the "audio" tab crashing winecfg. Did you find any resolutions to your problems?

My biggest issue is that I can't left or right-click anything once I start the game. There is a terribly slow framerate as well, but the main issue is being able to click/target etc.

---

### Post by knoxX on 2007-01-05
my wow doesnt work with opengl
it only works in d3d but a little bit strange i have a ati x1600 pro. drivers are installed. 
i dont know whats wrong

---

### Post by martianc on 2007-01-05
knoxX, I am also running ATI (x1400) and can't get openGL to work.

---

### Post by Kve on 2007-01-07
i have a question while trying this whole tutorial i got stuck rather quickly , i cant manage to install 
Wine , i tried it using the Synaptic package manager and all goes smooth untill i press reload , then it comes up with this error :
ttp://wine.budgetdedicated.com/apt/dists/edgy/main/binary-amd64/Packages.gz: 404 Not Found

does this mean it doesnt support my Amd64 proccesor or? im new to Ubuntu as you can see and i was wondering if i did something wrong or if it just lacks some support for my pc?

Any help would be greatly appriciated

edit found what i needed 

[http://www.ubuntuforums.org/showthread.php?t=291620](http://www.ubuntuforums.org/showthread.php?t=291620)

---

### Post by Poka64 on 2007-01-13
How do we Wine users install Burning crusade?
Should we just copy the content on the cd:s and install it from the harddrive?

---

### Post by oxy on 2007-01-15
First of all, when I run "patch -p1 < wine-wow-fixes.patch" i get the following message
```
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: libs/wine/mmap.c
|===================================================================
|--- libs/wine/mmap.c   (revision 3438)
|+++ libs/wine/mmap.c   (working copy)
--------------------------
File to patch: 
Skip this patch? [y] y
Skipping patch.
2 out of 2 hunks ignored
can't find file to patch at input line 45
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: loader/preloader.c
|===================================================================
|--- loader/preloader.c (revision 3438)
|+++ loader/preloader.c (working copy)
--------------------------
File to patch: 
Skip this patch? [y] y
Skipping patch.
1 out of 1 hunk ignored

```

If I ignore this message and continue I get stopped when running "make depend && make" by this message

```
make[1]: Entering directory `/opt/wine/wine-0.9.6/libs'
make[2]: Entering directory `/opt/wine/wine-0.9.6/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/libs/port'
make[2]: Entering directory `/opt/wine/wine-0.9.6/libs/unicode'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/libs/unicode'
make[2]: Entering directory `/opt/wine/wine-0.9.6/libs/wine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/libs/wine'
make[2]: Entering directory `/opt/wine/wine-0.9.6/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/libs/wpp'
make[1]: Leaving directory `/opt/wine/wine-0.9.6/libs'
make[1]: Entering directory `/opt/wine/wine-0.9.6/tools'
make[2]: Entering directory `/opt/wine/wine-0.9.6/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/tools/widl'
make[2]: Entering directory `/opt/wine/wine-0.9.6/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/tools/winebuild'
make[2]: Entering directory `/opt/wine/wine-0.9.6/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/tools/winedump'
make[2]: Entering directory `/opt/wine/wine-0.9.6/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/tools/winegcc'
make[2]: Entering directory `/opt/wine/wine-0.9.6/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/wine/wine-0.9.6/tools/wmc'
make[2]: Entering directory `/opt/wine/wine-0.9.6/tools/wrc'
gcc -c -I. -I. -I../../include -I../../include  -DINCLUDEDIR="\"/usr/local/include/wine\""  -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o lex.yy.o lex.yy.c
lex.yy.c:2610: error: expected ‘;’, ‘,’ or ‘)’ before numeric constant
make[2]: *** [lex.yy.o] Error 1
make[2]: Leaving directory `/opt/wine/wine-0.9.6/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/opt/wine/wine-0.9.6/tools'
make: *** [tools] Error 2

```


Any ideas? I'm new with linux btw so I might have missed some "obvious" solutions.

---

### Post by Scooter7 on 2007-01-27
I'm having the same problem (oxy's problem) - could someone please help us?

---

### Post by hikaricore on 2007-01-29
Is there a specific reason some of you folks are still trying to patch wine?
I was pretty sure at this point the WoW patches for wine were done with.

---

### Post by Sammi on 2007-01-29
It's because people keep finding old, outdated, misleading, and completely useless howtos like this one, when they search the forum for a "world of warcraft howto" :(

---

### Post by Scooter7 on 2007-01-29
Too true... I used a different how-to recently and can get WoW working, although my only problem is, I don't have enough disk space on my computer for it... :P

---

### Post by martianc on 2007-01-29
oxy and scooter, the default wine libraries you download from the Ubuntu repositories should get you up and running with Warcraft without any need for patching. The only thing you'll want to do is make sure your sound is setup properly in winecfg, and that you've modified Config.wtf in the Warcraft directory to use opengl and the proper sound mode (maybe a couple other changes there). These changes are well-documented elsewhere so I won't bother repeating them further.

I also found that upgrading to 6.10 seemed to help a clean up some of the issues I was having.

---

### Post by bagarospo on 2007-02-11
Hi all!
There is no more need to patch and build Wine from source, if you get last binaries (ver 9.30).
I suggest you to download them following this procedure: 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I did it and Wow works fine!
Hope it helps.

Mic

---

### Post by smclough on 2007-02-11
so WoW will run, but not smoothly and it exits when about halfway through the load screen when i'm logging in (to play, not into the account)

any clue what the problem might be?

vid card is a Nvidia MX420

---

### Post by Sammi on 2007-02-11
Have you tried everything suggested in this updated howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ?

---

### Post by martianc on 2007-02-12
smclough, what is the output you receive on the command line when you try to run WoW? are there any error messages?

---

### Post by Moffett on 2007-02-12
I just downloaded ubuntu a few hours ago and am having a hard time with it. Honestly all i use my computer for is world of warcraft but cant seem to get it running good. I tried to follow the wine instal instructions as good as i could understand but I truly have no idea what im doing. I just coppy and past everything i can find in the terminal. I seem to have gotten wow to start up and run but every time it starts up my resolution goes from 1280x800 to 800x600 the game seems to be missing a bunch of pictures of my spells and stuff and if i try to adjust the video settings it locks up and i need to restart my computer. i see posts of people resetting settings in what looks like the actual world of warcraft file but i don't know where my file was downloaded to on my computer. hell i dont even know if it actualy is downloaded on my computer. I found this post and want to follow it but not sure if it still works now that it's old. The first thing it tells me to do is uninstall wine and i dont know how to uninstall it. 

Maybe if someone could help explain what to do in overly simple terms I just might be able to not only fix it but understand what the hell im doing.

---

### Post by Sammi on 2007-02-12
[SIZE=4][COLOR=Red][B]DO NOT FOLLOW THE INSTRUCTIONS IN THIS TREAD!
[/B][COLOR=Black][SIZE=2]
Instead you should follow the directions in our community WoW/Wine wiki, which I'll post again here: [/SIZE][/COLOR][/COLOR][/SIZE][https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

And you should ask for help/directions on making this work in this tread: [http://www.ubuntuforums.org/showthread.php?t=312482](http://www.ubuntuforums.org/showthread.php?t=312482)

---

### Post by Perfect Storm on 2007-02-12
I'm locking it down.

---

