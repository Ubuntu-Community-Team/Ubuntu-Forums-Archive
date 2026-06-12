---
title: "another steam thread (yes, its different --i think)"
date: 2005-08-01
forum: Gaming &amp; Leisure
---

### Post by proxess on 2005-08-01
When i try to run steam with wine i get [this](http://members.netmadeira.com/andreoliveira/lalala/winesteam.png) and when i try to run it with cvscedega (i followed the 2 guides of linux-gamers-net) i got [this](http://members.netmadeira.com/andreoliveira/lalala/cvscedegasteam.png) 

any help?


-Proxess

---

### Post by frodon on 2005-08-01
With cedega go to the directory where steam is and do : ```
sudo cedega Steam.exe
```

---

### Post by strikeforce on 2005-08-01
Wine does not contain everything either.  You will need to install fonts and a webbrowser and some other files in order to get it to work.  However the post above will help you with how to get it to run.

---

### Post by claydoh on 2005-08-02
[Check out Transgaming's Games DB section on Half Life2 ]("http://digital-conquest.ath.cx/wiki/index.php/Half_Life_2")
you neeed their Mozilla ActiveX component, and also their font installer will improve things a little. Both are available as .deb files in their download section, read the README's there as well on how to use them.

---

### Post by simonjardine on 2005-08-02
Download latest Wine
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

or use WineCVS to compile Wine from CVS [http://winecvs.linux-gamers.net/](http://winecvs.linux-gamers.net/)

Needed apps, packages, libraries:
wget, fontconfig, freetype2, freetype2-devel, bison, flex, libjpeg, libjpeg-devel, libpng, libpng-devel, zlib, zlib-devel, xorg-x11-devel (resp. XFree86-devel)

Mesa (resp. xorg-x11-Mesa, XFree86-Mesa), Mesa-devel (resp. xorg-x11-Mesa-devel, XFree86-Mesa-devel), freeglut, freeglut-devel

Debian users can just use:
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

Change to the location where the WineCVS.sh is lying and start it with:

sh WineCVS.sh

The script downloads with wget a archiv defaults.tar.gz with the need install scripts. After that you should see its installation menu.

Select a profile ... follow the steps...

... done!

Compilation and installation successful.



3. Configuration


Now its time to come to the real stuff...

Run wine which will create the configuration for you.

Create a files e.g. called hl2.reg and add the following content.

REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\hl2.exe]

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\hl2.exe\DllOverrides]
"shdocvw"="native,builtin"
"shlwapi"="native,builtin"

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\hl2.exe\dsound]
"HardwareAcceleration"="Emulation"

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\Steam.exe]

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\Steam.exe\DllOverrides]
"shdocvw"="native,builtin"
"shlwapi"="native,builtin"

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\Steam.exe\X11 Driver]
"Desktop"="1024x768"



Now update your registry with

regedit hl2.reg

if you use cvswine, cvswine regedit hl2.reg.



4. Needed DLLs


The latest Steam version requires msvcr70.dll, shdocvw.dll and shlwapi.dll. Get it at [http://www.dll-files.com/](http://www.dll-files.com/) and place it in your ~/.wine/drive_c/windows/System resp. ~/.cvswine/drive_c/windows/System directory.



5. Installation and Login

5.1 Steam


Simply change to the directory where you downloaded SteamInstall_CS.exe and type

wine SteamInstall_CS.exe

resp.

dx9wine SteamInstall_CS.exe

The install should go fine, and after it's completed and wasted your time "updating" steam (it generated strangely small amounts of network traffic) Steam will launch. Create an account or log in, then add Counter Strike to your list of games.

5.2 Half-Life 2
Half-Life2 Linux

In order to get the installer running you need to install DCOM98 first. Get it here.

WINEDLLOVERRIDES="ole32=n" wine dcom98.exe

The Half-Life 2 installer is an msi installer and needs a utility called Windows Installer. You can download Windows Installer from here.

You can install Windows Installer by typing

wine instmsia.exe

Now add the following lines to the [DllOverrides] section of ~/.wine/config:
"msi" = "native, builtin"
"msiexec.exe" = "native, builtin"


Now type

wine msiexec /i /path/to/HL2/steam.msi

and Half-Life 2 will be installed.

5.3 Login


If you won't be able to type your password/email. So you have to start Wine in desktop mode. It will fake a windows desktop and all Windows apps will be displayed in one big window.

Find in your ~/.wine/config a line which begins with
;\"Desktop\"= ...


Uncomment it (remove the semicolon in front of the line) and change the resolution if you wish.



6. Command Line Options


Similar to the way you can add command variables to the Steam Launch Options, you can also add them to a Half Life 2 startup script.

#!/bin/bash
cd /path/to/Steam
wine Steam.exe -fullscreen -width 1024 -height 768 -applaunch 220 -heapsize 512000 +map_background none &


The above command line will launch Half Life 2 (-applaunch 220) with a memory allocation of around 500MB (-heapsize 512000), and Half Life 2 will start without a 3D background on the main menu (+map_background none). You can add as many variables as you want :)


Command Line Commands

-heapsize [Kilobytes]: This command tells Half Life 2 to allocate more RAM to the game system heap, where it can be accessed by the game to improve performance by storing more game information in RAM and hence reducing loading pauses. The default heapsize is 64MB, however you can safely allocate around 128MB (i.e. -heapsize 128000) for most systems. You can use higher values if you have more RAM, but I don't recommend exceeding half your physical RAM (e.g. for 1GB RAM, set heapsize of 512000).

-console: Speeds up the loading of Half Life 2 at startup by not loading up the background 3D graphics on the main menu and instead loading up a blurry background picture and the Half Life 2 console open. Note you can close this console using the '~' key.

-width [pixels] -height [pixels]: Using these two commands you can set a custom resolution in Pixel Width x Pixel Height (e.g. -width 640 –height 480 starts HL2 with 640x480 resolution). Make sure you choose a resolution supported by your monitor and with the correct ratio of width to height (usually 4:3).

-dxlevel [version]: Using this command allows you to force Half Life into only using the specified DirectX version for shaders. For example, use -dxlevel 70 to force Hardware DirectX7.0 level support for shaders. This means a reduction in image quality but an increase in performance. Other values include -dxlevel 80 -dxlevel 81 and -dxlevel90. Note that this only works if you choose a DirectX version which is lower than the current one supported by your graphics card. See the Hardware DirectX Version option under the In-Game settings for more details.

-refresh [Hz]: Specifies the refresh rate the game will use upon loading. This is normally not required as your system should already use the optimal refresh rate at your chosen resolution. However if this is not the case you can force it to a specific refresh rate (e.g. -rate 85). Make absolutely certain that the rate you are trying to apply does not exceed your monitor's capabilities otherwise you may damage your monitor - especially if you change resolutions and forget to change this option.



7. Tweaking Guide


A tweaking guide for Half-life 2 can be found here:
[http://www.linux-gamers.net/modules/wfsection/index.php?articleid=60](http://www.linux-gamers.net/modules/wfsection/index.php?articleid=60)



Hope this helps everyone play CS within Linux, 

"LIKE LINUX" \\:D/

---

