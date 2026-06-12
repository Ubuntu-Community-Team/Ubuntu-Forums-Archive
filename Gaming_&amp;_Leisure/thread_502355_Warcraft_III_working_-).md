---
title: "Warcraft III working :-)"
date: 2007-07-16
forum: Gaming &amp; Leisure
---

### Post by Diabolis on 2007-07-16
I had a lot of trouble before I could play warcraft III on ubuntu and now that is working, I though It would be good to share my experience. It might help out someone less experienced.

At first I thought that having the latest versions of software running on fesity would be the best to have but after getting lots of errors in the terminal and reading through many forums, I ended up running **wine-0.9.35** on ubuntu edgy. For some reason warcraft would crash everytime with wine-0.9.40 on feisty.

I still have to try wine-0.9.35 on feisty, but It will probably work. So as many probably know, newer isn't always better.

if you already have wine-0.9.40 you can remove it and get the older version from the official site, It comes already compiled so its very easy to install. You just have to double click the file and it will install automatically. When the installation is done type:

```
winecfg
```

It will prompt a window where you can set many options I setted mine to windows xp and in the audio tab I changed the driver to ALSA driver, the OSS driver gives a lot of noise  and bad quality (at least in my laptop).

Installing warcraft should run smoothley, When you are done, go to your home directory and press

```
ctrl + h
```

Doing that will show the hiden folders and files. Look up for .wine folder and open it. It will have the same folders that a windows installation has. Now you have to go to where warcraft is installed and delete/rename the movies folder because if you don't warcraft will crash. You can still watch the movies with a movie player outside the game.

then to check that everything is fine in the pc, type in terminal the following:

```
glxinfo | grep rendering
```

The output should be: direct rendering: yes. If that isn't your case, you don't have the correct configuration for your video card or you don't have the correct driver. If you wan't to know what driver you are using, type this in terminal:

```
sudo gedit /etc/X11/xorg.conf
```

A file will open, look for the section called "device", it should look like this:

```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML 		Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```

As you can see the driver I'm using is "i810". Before I had this driver I didn't have direct rendering because I guess (not sure) the default driver that ubuntu uses when you install it is VESA. I've heard that this driver is good and it works for a lot of people but that wasn't my case, probably because I have an intel chipset as you can see.

After changing the driver I restarted my computer and voila I had direct rendering. I've been playing a few games in battlenet and everything works well. to run warcraft do it like this:

```
wine .wine/drive_c/Program\ Files/Warcraft\ III/Warcraft\ III.exe -opengl
```

I don't like typing all that everytime I want to play, so I added the route to my "windows" path variable. Its very easy, just type this in the terminal:

```
wine regedit
```

a regedit window should appear, go to this key:

```
HKEY_LOCAL_MACHINE/System/CurrentControlSet/Control/SessionManager/Environment/Path
```

Double click on it and add this to its value:

```
;c:\Program Files\Warcraft III
```

don't forget the **;** at the begining.

after that you can run warcraft like this:

```
wine Warcraft\ III.exe -opengl
```

When I run warcraft I still get this error:

```
libGL warning: 3D driver claims to not support visual 0x5b
```

I don't know how to fix it yet, but It doesn't seem to be an important error. I think that If I were able to fix it, It would improve a little the performance of the game, but as I said I don't even know what it really means.

All this was done on a Acer TravelMate 2420 with 256 of ram and a centrino 1.7ghz

*** Edit *** *05/september/07*

After running warcraft for a while as I described, I decided to upgrade my ubuntu version to feisty and then my wine installation to the latest. I have no problems while playing, but for some reason colors are a bit messed up. Its hard to distiguish between orange and yellow or light blue and teal when you pick a color and everything seems to be a bit brighter. I tried to fix it by playing around with the video options that come with the game, but no luck. Is not too bad, but still a bug. The good new is that this error is not showing up anymore.
> libGL warning: 3D driver claims to not support visual 0x5b

---

### Post by cogadh on 2007-07-16
Rather than creating a registry edit that adds the Warcraft directory to the environment path, it is easier and better to create a simple script like this:
```
#!/bin/sh

# Goto game dir
cd "$HOME/.wine/drive_c/Program Files/Warcraft III"

# Launches game (modify as needed)
WINEDEBUG=-all wine "C:/Program Files/Warcraft III/Warcraft III.exe -opengl"
```
Then you just need to make the script executable and run it to launch the game appropriately. You could even create a desktop or menu shortcut to the script to make launching even easier.

EDIT - You may need to leave the "-opengl" outside of the quotes, I'm not really sure on that part (I don't play Warcraft).

---

### Post by Diabolis on 2007-07-16
Good idea, I tried that and my script looks like this:

```
#!/bin/sh

# Launches game (modify as needed)
WINEDEBUG=-all wine .wine/drive_c/Program\ Files/Warcraft\ III/Warcraft\ III.exe -opengl
```

I took out the other line because I didn't know which was it purpose and the script still works.

---

### Post by cogadh on 2007-07-16
Most game executables like to be run within the install directory, so it is best to CD to the install directory before launching the game. Otherwise, there is a chance that the executable won't be able to find the game files it needs to run properly. That might not be the case with Warcraft, but it is true for most Windows games.

---

### Post by xxrealmsxx on 2007-07-18
Thanks for sharing your experiences. Sadly however I can't even get warcraft installed.

Here is as far as i've gotten:

realms@realms-desktop:/media/cdemu0$ dir
autoplay.exe  directx      movies     setup.mpq  trailers  War3.mpq
autorun.inf   install.exe  Razor1911  support    War3.ico  Warcraft\ III\ Manual.pdf
realms@realms-desktop:/media/cdemu0$ wine install.exe
err:module:import_dll Library &#65533;&#65533;&#65533; (which is needed by L"Z:\\install.exe") not found
err:module:import_dll Library &#65533;&#65533;&#65533; (which is needed by L"Z:\\install.exe") not found
err:module:import_dll Library &#65533;&#65533;&#65533; (which is needed by L"Z:\\install.exe") not found
err:module:import_dll Library &#65533;&#65533;&#65533; (which is needed by L"Z:\\install.exe") not found
err:module:import_dll Library &#65533;&#65533;&#65533; (which is needed by L"Z:\\install.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\install.exe" failed, status c0000135

any suggestions?

---

### Post by xxrealmsxx on 2007-07-18
Ok I tried using my original Warcraft 3 CD instead of a mounted .bin file and it worked perfectly.

---

### Post by chaos2286 on 2007-07-23
Hi,

I've installed Warcraft 3 and the Frozen Throne pretty smoothly with wine.  Everything works pretty normally, when I'm playing single player.  The only thing that happens is I notice some strange effects (units being close to invisible in certain conditions, unit portraits not showing up).  Ok, now onto the problem I cannot play multiplayer on the internet.  Either the program will freeze during the loading screen after a game is found or shortly after I enter the game.  If anyone has had this problem or knows how to fix it I'd be greatly appreciative.  Let me know any info you need from the terminal (I'm new to linux).  Thankkkkssss

---

### Post by ignos on 2007-07-23
Also, if anyone is having trouble launching the game and they have the CD (they should) then they:

1. Terminal> Type "winecfg"
2. Click on "Drives"
3. Click "Add"
4. A new drive should pop up like "D:"
5. Click on "Advanced"
6. Enter in the location of your CD drive and the Type selection you need to pull down is "CD ROM"
7. Make sure the Advanced option is "Autodetect". Click "Apply" and exit/"OK".

The game will now load without a NO-CD crack from your CD-ROM drive. (If the game doesn't start up automatically when the CD-ROM drive is mounted then you just launch "autoplay.exe" or "install.exe" from the opened drive.)

Hope that helps!:)

---

### Post by chaos2286 on 2007-07-24
going back to my previous problem, if anyone could help heres the log

:~/.wine/drive_c/Games/Warcraft III$ wine "Frozen Throne.exe" -opengl
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
**err:ole:CoCreateInstance apartment not initialised**
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed80,0x00000000), stub!
[email]eric@ACIDPSYCHO:~/.wine[/email]/drive_c/Games/Warcraft III$ fixme:ntdll:NtCreateIoCompletion (0x34eeb0, 1f0003, (nil), 0)
fixme:imm:ImmAssociateContextEx (0x10028, (nil), 16): stub
[B]wine: Unhandled page fault on read access to 0x003c00c4 at address 0x403e03 (thread 0010), starting debugger...
[/B]


thank youu for any help

---

### Post by Diabolis on 2007-07-29
Recently I upgraded from edgy to feisty, so my wine version got upgraded too, now it is **wine-0.9.41**. I though everything would be messed up as last time, but for my surprise everything went well. The only problem I had was that I didn't have direct rendering, that was weird because I had direct rendering in edgy, even then I was able to play warcraft. I figured that if I enabled direct rendering I would get a better performance, so I made this changes in my xorg.conf file.

```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML 		Express Graphics 				Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	**option		"DRI"		"true"**
EndSection

Section "ServerLayout"
	**Option 		"AIGLX"		"true"**
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

[B]Section "Extensions"
        Option "Composite" "Enable"
EndSection[/B]
```

The bold text are the changes I made to my file. I made those changes according to what I read here:
[https://wiki.ubuntu.com/i810?highlight=%28CategoryDocumentation%29]("https://wiki.ubuntu.com/i810?highlight=%28CategoryDocumentation%29")
[http://gentoo-wiki.com/HOWTO_Direct_rendering_on_Intel_Extreme_Graphics_(855GM)_chipsets]("http://gentoo-wiki.com/HOWTO_Direct_rendering_on_Intel_Extreme_Graphics_(855GM)_chipsets")

After that I restarted my X server by pressing:
```
ctrl + alt + backspace
```
And I had direct rendering again.

this error doesn't appear anymore, I guess it got fixed in the upgrade.
```
libGL warning: 3D driver claims to not support visual 0x5b
```

Back in edgy graphic were as good as running the game in windows, but now they don look that good. Everything looks too bright and in some games some units change their color unexpectedly, like from dark blue to a bit darker blue. It isn't a big issue but still a issue.

---

### Post by massong on 2007-08-23
Hi folks,

I am having a problem with Warcraft III keyboard support under Wine.

I have installed wine & Warcraft III (Reign of Chaos) without any problems and the game loads up fine using my original Warcraft III CD. 

However, I have no keyboard input support at all.   I do have keyboard input for other games I have installed under wine (Like Diablo 2).

I noticed this problem after I click Single Player from the Warcraft III main menu and it wants me to give a name for a new profile.  I am unable to enter anything at this prompt :(

Could anyone give me a few suggestions on how to troubleshoot this problem further?

Thank you,
Gary

---

### Post by xxrealmsxx on 2007-08-23
Do you have compiz or any desktop effects enabled?

---

### Post by angryfirelord on 2007-08-23
> **massong said:**
> Hi folks,

I am having a problem with Warcraft III keyboard support under Wine.

I have installed wine & Warcraft III (Reign of Chaos) without any problems and the game loads up fine using my original Warcraft III CD. 

However, I have no keyboard input support at all.   I do have keyboard input for other games I have installed under wine (Like Diablo 2).

I noticed this problem after I click Single Player from the Warcraft III main menu and it wants me to give a name for a new profile.  I am unable to enter anything at this prompt :(

Could anyone give me a few suggestions on how to troubleshoot this problem further?

Thank you,
Gary
Did you try updating to the latest patch for Warcraft? Also, make sure to get your wine from budgetdedicated instead of the Ubuntu repos, they're more up-to-date.

---

### Post by melzanis on 2007-08-26
Hey Everyone, 
       First I would like to start off by saying I have Wine and Warcraft installed. Also that everything up to that put was working, but when every I try to start Warcraft it just freezes up. I can't do anything but use Alt + tab to move over to a different window. I have know idea how to fix this glitch, can some one please lend me a hand in solving this issuse.

Thanks

---

### Post by Diabolis on 2007-08-26
Might be slow because you don't have direct rendering enabled. Check for it with this command:
```
glxinfo | grep rendering
```

---

### Post by joeyea on 2007-08-26
i maneged to get warcraft installed but the only way i could play it was by using a no-cd crack because it did not recognise the disk was in the drive. when i eventually got it working it was extreemly slow even with -openl

---

### Post by melzanis on 2007-08-27
Ya I tried that command before I installed Warcraft. I followed every step. The only one I was unsure about was the part with deleting/renaming the movie folder. I'm not sure if that's what's wrong.

---

### Post by Diabolis on 2007-08-27
you'll never have a problem related to the delete/rename movies folder trick. Since I didn't want to change the order of my files under my warcraft folder, I changed the name of the folder to this: **mMovies**

---

### Post by DawgPoP on 2007-09-05
> **Diabolis said:**
> 

Back in edgy graphic were as good as running the game in windows, but now they don look that good. Everything looks too bright and in some games some units change their color unexpectedly, like from dark blue to a bit darker blue. It isn't a big issue but still a issue.

Diabolis, did you ever fix this issue, I am getting the exact same thing with ubuntu feisty and wine-0.9.44  

Some things look REALLY bright and others REALLY dark.

[IMG]http://im1.shutterfly.com/procserv/47b7d724b3127ccebb24e7385bcc00000026108AYtG7Rm2cty[/IMG]
[IMG]http://im1.shutterfly.com/procserv/47b7d724b3127ccebb24e7265bd200000026108AYtG7Rm2cty[/IMG]

---

### Post by Shin_Gouki2501 on 2007-09-05
Is the Battle net features generally not working within Wc3 FT?

---

### Post by DawgPoP on 2007-09-05
> **Shin_Gouki2501 said:**
> Is the Battle net features generally not working within Wc3 FT?

my battlenet is working at the moment in frozen throne, i played a few games earlier.

---

### Post by Shin_Gouki2501 on 2007-09-05
Thx for reply!Thats nice to hear :D
I guess i give it a try today!!

Although i have a Original CD for install of RoC and TFT i used to play with an image in windows i mount it with daemon tools hope that works here too!

---

### Post by KarmaticStylee on 2007-09-05
```
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed04,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ef50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ef88,0x00000000),m  stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16

```

No CD-ROM error.  It works fine on my desktop pc but not my brand new laptop :( 

I'm running the newest version of Ubuntu and Wine

---

### Post by Diabolis on 2007-09-05
If you read the first post in this thread, You know that newer is not always better. Maybe trying an older version of wine at first will fix your problem.

I have to mention that after running warcraft for a while as I described in my first post. I decided to upgrade my ubuntu version to feisty and then my wine installation to the latest. I have now no problems while playing, but for some reason colors are a bit messed up. Its hard to distiguish between orange and yellow or light blue and teal when you pick a color and everything seems to be a bit brighter. Is not too bad, but still a bug.

---

### Post by KarmaticStylee on 2007-09-05
> **Diabolis said:**
> If you read the first post in this thread, You know that newer is not always better. Maybe trying an older version of wine at first will fix your problem.

Well here's the weird thing.  I went ahead and got Cedega.  I install Warcraft III via Cedega - same thing, can't find the CD! 

I tried to boot it with a no-cd crack in both WINE and Cedega - both times it caused my computer to freeze.  Even if it did work I'd rather use my CDs...

This is really the only game I care about so this is really irritating.

Also - does deleting the "Program Files" area in  ".Wine" remove all of the program? I just want to make sure I am trying fresh installs of Warcraft iii

---

### Post by Diabolis on 2007-09-06
Wine has a uninstalling tool or uninstall through warcraft uninstaller. I wouldn't delete the folder if I wanted to make a freshand clean install. Have you tried making a mounting point which only pourpose is to mount warcraft. I have not done that, but if you type **winecfg** in the terminal a window will appear. In that window you can setup exactly which drives you want to be availabelin wine. As I said I haven't been in the need of using that tool, so I can't tell you exactly how to do it, but I hope it points you to the right direction.

---

### Post by drkknight on 2007-09-06
I have Warcraft 3 running just fine except that the movies crash the game. I removed them and it runs fine, but I would like to watch the videos too. Is there something that I'm missing?

---

