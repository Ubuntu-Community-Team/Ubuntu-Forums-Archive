---
title: "WoW + Opengl + Nvidia 7600GT doesn't work :("
date: 2007-04-28
forum: Gaming &amp; Leisure
---

### Post by MauditOstie on 2007-04-28
Hi guys,
pretty new to Ubuntu but i read a load of tweaks and things to get WoW working on my machine...
Everything worked fin and WoW even start... but not in Opengl and this causes me to get 3fps with an AMD64 X2 3800+, 2gigs of Ram and an Nvidia 7600GT on Fiesty.

Everytime i try to start WoW (aoss wine WoW.exe -opengl) i get the following:
```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7e1e0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e1e0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  28 ()
  Serial number of failed request:  508
  Current serial number in output stream:  509

```

also glxinfo | grep rendering 
and got:
direct rendering: Yes
and
cat /etc/X11/xorg.conf | grep Driver
got:
    Driver         "kbd"
    Driver         "mouse"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "nvidia"

Any ideas anyone? 

TY 

Rob

---

### Post by Garyu on 2007-04-28
Maybe not much help, but I've got almost exactly the same hardware as you, and for me everything runs very smooth...

Things you could try:
- uninstall / reinstall nvidia driver
- use "nv" instead of "nvidia" might give other results
- instead of running WoW.exe with -opengl option it is possible to edit WTF/Config.wtf in your wow-folder and add this line: SET gxApi "OpenGL"
- do you really need aoss? For me sound works great without that. There are sound settings in WTF that you can play around with too, if you have sound issues.
- install a different version of Wine. I don't know which version you have, but some seem to work better than others with WoW.

BTW, are you running 32-bit or 64-bit version of Ubuntu?

---

### Post by MauditOstie on 2007-04-28
Hi!
I got Ubuntu's 64-bit version so i know wine might be a little buggy sometimes with it and that i cannot use the ADD/Remove package :(
.
As for the SET gxAPi, i did try it and when i got this line in my config.wtf, this causes the same thing.

I had a lot of problems with the Nvidia driver installation as i had to use Envy since my Kernel and the driver weren't the same. So i'll try to re-install both Wine and
aoss i use it because i'm using TeamSpeak.

---

### Post by MauditOstie on 2007-04-28
Re-installed Nvidia and Wine...
Still the exact same error:

```
 
 wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7e190000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e190000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  28 ()
  Serial number of failed request:  564
  Current serial number in output stream:  565

```

---

### Post by RobinOfSweden on 2007-05-03
Sounds a bit weird, but i have the same hardware as you and i cant use much juice of my own Geforce 7900 GT either (see my fotnote guess we are in the same puddle of goo).

Anyway it works but... i wouldnt say 3-5FPS is working.
I think that there might be some issues between the OpenGL driver for 64bit and the 32bit Wine.
*edit* forgot to mention  that NWN works perfectly fine in OpenGL thus i think there is some issues between wine (maybe due to using all those fixes to get it working... dont know).
Not realy sure but it feels like its from something in that area.

Anyway if i come up with/find a solution i will reply here asap :D
hope you do as well 
regards Robin

---

### Post by Garyu on 2007-05-03
Hey Robin,

7900GT is not exactly the same as 7600GT, is it? But you are also using Edgy. I never tried the 64-bit version of Edgy, but WoW and lots of other 3D games worked fine in 32-bit for me. Now in Feisty I only got 64-bit installed so far, and it's working great. Everything. Not a hassle anywhere. Well, I can't use Beryl and start some games, but it's easy to switch to Metacity before starting any 3D-stuff.

My hardware:
AMD Athlon 64 X2 4200+
MSI K9N Neo
1 GB RAM
nVidia GeForce 7600GT 256Mb 
320 GB S-ATA 

I use wine version 0.9.35 maybe there is a difference there? I will upgrade and see... wait... there... yes, now I have wine 0.9.36 and that works great as well. I have tested WoW, Heroes of Might and Magic 5 and Americas Army 2.8 without problems. Oh, for sound to work, I have to use ALSA, not OSS.

What I am saying is, you should be able to get it to work. Try a clean install. Or try reinstalling wine or whatever. Check you've got the latest versions. And Robin - get Feisty, it's worth it, my system is actually even faster. :D

---

### Post by marcozs on 2007-05-03
> **RobinOfSweden said:**
> Anyway it works but... i wouldnt say 3-5FPS is working.

I have the same problem: if I run WoW in d3d mode it's playable, about 30fps on 1280x1024. If I try to run it in opengl mode at the same resolution then the fps just drop below 2 and I have a really hard time to get the mouse over the button to exit the game!

It worked in opengl only the first time I run it until I heartstoned to the Outlands... since then the only way to play is in d3d and it really annoys me cause under windows WoW is perfectly fluid in full detail...

It's really weird, anyone else experienced the same problem?

I have Feisty running on an AMD 3800+ 1Gb RAM and a Geforce6800U

---

### Post by RobinOfSweden on 2007-05-04
> 7900GT is not exactly the same as 7600GT, is it?
Indeed Garyu it is! Haha
such a fool i am! I saw 9 instead of 6 :P

Anyway i followed your recommendation and i am now using Feisty (havent had the chance yet to update my signature so bear with me :D I also used the "Update manager" in "System -> Administration" for my dist upgrade, worked perfectly fine though i doubted it first :P)

Anyway i am off to set drivers etc straight had some issues earlier wich ended with me "accidently" removing the Nvidia drivers and i am now using nv >_>
However since my glxheader and glxgears worked perfectly fine earlier i realy do think that there was some issues between libs/graphic driver and wine. NWN and PSX worked perfectly, yes i do dare say that :D while wine WoW did not. And i was using the tricks to get it working in 32bit, maybe some libs was not linked so that wine found the OpenGL thus resulting in the bad, real bad, gaming experience in World of warcraft :D

---

### Post by marcozs on 2007-05-04
Have you tried in d3d mode?

---

### Post by RobinOfSweden on 2007-05-04
Actualy after alot of scratching in my head i cant understand how this happened:
WTF/Config.wtf contains this:
SET gxApi "OpenGL"

Yet!

when i run it its very slow... so i thought "wait a sec! Maybe its still running Direct3D!"
so i tried running it again though i did:
```
wine ~.wine/drive_c/.../WoW.exe -d3d
```
and what do you know its the same result!
But i have had a improvement of 3-5 FPS when i went to 800x600 and outside Orgr i ended up with 9 FPS.

But i assume there is some sort of trouble somewhere... considering i have this result from glxgears:
```

46581 frames in 5.0 seconds = 9316.127 FPS
49454 frames in 5.0 seconds = 9890.331 FPS
50202 frames in 5.0 seconds = 10040.380 FPS
49576 frames in 5.0 seconds = 9915.105 FPS
49584 frames in 5.0 seconds = 9916.704 FPS
49542 frames in 5.0 seconds = 9908.306 FPS
50521 frames in 5.0 seconds = 10104.136 FPS
46617 frames in 5.0 seconds = 9323.390 FPS
49255 frames in 5.0 seconds = 9850.437 FPS

```
Not the same result but its atleast working, cant realy figure out why it doesnt work properly,
i also tried using the console with opengl as command and ended up with this:
```

err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  28 ()
  Serial number of failed request:  654
  Current serial number in output stream:  658

```
Though someone might know i am clueless yet, googling around to see if i can find a possible solution to it!

---

### Post by Garyu on 2007-05-04
hmm. have you tried removing that line from config.wtf and running with
-d3d
-opengl
to see if it makes any difference between the two? It is a strange problem, I'll agree to that. Especially since I am sitting here with basically the same setup and everything works GREAT...

What version of Wine are you using btw? Did you try different versions?
[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)

---

### Post by marcozs on 2007-05-04
> **RobinOfSweden said:**
> Though someone might know i am clueless yet, googling around to see if i can find a possible solution to it!

Yeah, I googled the whole world yesterday night.. I really wanna get windows out of my computer, but if WoW doesn't work propely I can't

---

### Post by Garyu on 2007-05-04
> **marcozs said:**
> Yeah, I googled the whole world yesterday night.. I really wanna get windows out of my computer, but if WoW doesn't work propely I can't

You know, if you want to ditch windows, just use 32-bit Ubuntu. Everything will work smoothly without issues there. Actually, most things work smoothly in 64-bit as well, but since you are having wine-related problems and that is one of the things that you need to run in 32-bit mode that might be the reason. So just make a 32-bit installation and try it out. 32-bit has always been a lot more hassle-free than 64-bit. And the difference in speed is negligible.

Personally, I'm only using 64-bit right now because I think more users should go there so developers are pushed to migrate their stuff from 32-bit. After all, 64-bit is the future, and linux is starting to fall behind in that area.

EDIT: oops, sorry, I thought I was in the 64-bit forum... Guess not. Sorry. So are all of you guys using 32-bit? Then maybe 64-bit is the one that works well in this case? :confused:

---

### Post by marcozs on 2007-05-04
> **Garyu said:**
> You know, if you want to ditch windows, just use 32-bit Ubuntu.

Sorry, maybe I didn't specify but... I AM using the 32-bit Feisty!
Latest Wine dowloaded from the winehq repos.

As I said it works quite ok with "-d3d", playable but the frame rate is not even close to what I get on windows in full detail.
If I try in opengl, I get 2 fps :-(

I will try to remove "SET gxApi "OpenGL" from the config.rtf once I get home...

---

### Post by RobinOfSweden on 2007-05-04
Hehe woopsie didnt take notice of that either Garyu!
But yes i am a 64 bit user, using the 64bit apt repositery from wineHQ.
The thing is i would love if you checked your libraries in winecfg.
i find the d3d libs (quiet the lot of them) but i cant find anything on the OpenGL (maybe there aint supposed to be any!)

And on the next end (think my config file was rewritten during my tries on wow since my SET gxApi was gone!) but i did try it again with gxApi "opengl" and now it wont start. So now i _know_ that my wine doesnt have opengl support thus ending with me only able to use d3d (might have been rewritten since it didnt find opengl support, dont know).

Anyway i am off to surf the ocean on my goggle board and see if i can find anything on 64bit feisty wine on OpenGL.

Robin goes out surfing. (maybe should make a specific thread for the AMD64 users? but i think that marcozs has the same problem with opengl not installed/supported in the wine installation)

---

### Post by marcozs on 2007-05-04
> **RobinOfSweden said:**
> but i think that marcozs has the same problem with opengl not installed/supported in the wine installation)

I posted in a specific thread... 
My wine is anyway the one from the official winehq repos, so I don't get why it should not be supporting the opengl? How do I check that?

I will try to reinstall wine, and to clean wow's cache file as suggested by one guy in the other post I wrote...

---

### Post by RobinOfSweden on 2007-05-04
i am not sure its the correct way but you can edit all the libs (i assume) in wine by typing:
winecfg
in a terminal (no sudo or anything) and you will get a window with a few tabs. One of the tabs has the name Libraries and in there you can choose specific libraries to edit. among those i found the d3d but none regarding opengl.

Not 100% sure thus i hope that Garyu will be able to compare it to his own winecfg. (if there is a opengl to choose among his libraries then without a doubt i lack them for some reason.)

---

### Post by marcozs on 2007-05-04
> **RobinOfSweden said:**
> in a terminal (no sudo or anything) and you will get a window with a few tabs. One of the tabs has the name Libraries and in there you can choose specific libraries to edit. among those i found the d3d but none regarding opengl.

Isn't it because opengl is supported natively by linux?

---

### Post by RobinOfSweden on 2007-05-04
Yea i found the opengl32.dll
weird now i am totaly out of ideas >_>
what could it be... what could it be...

---

### Post by marcozs on 2007-05-04
> **RobinOfSweden said:**
> Yea i found the opengl32.dll
weird now i am totaly out of ideas >_>
what could it be... what could it be...

but do you get it working in d3d or not even that way?

By the way I really believe that Blizzard would get many happy customers making a launcher for linux...They've already got a Mac version, shouldn't be so hard to port that to linux as well!

---

### Post by RobinOfSweden on 2007-05-04
Marcozs indeed i would agree on that.
However i doubt they will. Since they are probably pretty content with the way it is :P

Regarding if i get it working with D3D yea i think i mentioned that as well.
However OpenGL give me the error message i also mentioned above.
Anyway i give up for the day, got database project for a "new" forum at my college to prepare :)
exams are getting close all and all perhaps its better that i feel the pain of the 1-3FPS
(i thought i should go try to wack some monsters but no... it didnt go so well xD)

Anyway i will be looming over this thread and if some interesting possible solutions comes up i will be there to try it asap :D

---

### Post by Garyu on 2007-05-04
humm... I have six "d3d...dll" in winecfg, like "d3d8.dll" and "d3d9.dll".

I can not find any opengl dll in there... Maybe that is your problem? You might be using the Microsoft drivers while you should be connected to linux native drivers?

---

### Post by RobinOfSweden on 2007-05-04
Garyu i have the same as you.
Nothing on opengl but 6 d3d...
oh well will see if i am missing some other DLL in the lib/wine folder

---

### Post by bfree on 2007-05-04
A little bit off-topic, but CPAN's recently updated Perl OpenGL 0.55 module has been tested with a number of nVidia cards on Ubuntu (haven't tried with WoW): [http://graphcomp.com/opengl](http://graphcomp.com/opengl)

Benchmarks show that OpenGL performance on Ubuntu is much faster than Windows, and in some cases faster than Fedora (using same machine, GPU and drivers - go figure).

---

### Post by RobinOfSweden on 2007-05-05
Bfree: 
Sounds interesting but since i am running Feisty64 the installation couldnt find my openGL libs >_> but i read through each sections and i found it interesting :D

Back to the topic! i surfed the net loong into the night yesterday on my "google board" and i found my errors both in a WhineHQ thread on WoW as well as on some other games. Their problems lied in Framerate but each of them knew how to fix it but never posted how... (crying inside!) since it was a very long time since i last went with a linux system (the latest was slackware about 4-5 years ago) and i got Ubuntu about 2 weeks ago :D.
Anyway i have no idea what they meant with the framerate, is it settings on WoW ini files or is it xorg.conf settings that messes things up?

Would love an reply on this :D:D

*Edit*
Garyu could i have a look at your Device section in your Xorg.conf? might find a missing part there (instead of having me post my entire config i think its better to have a look at someone who has it working!)

*Edit2*
Ok now i did another reinstall of Ubuntu 6.10 and directly updated to Feisty 7.04 and installed the drivers through Envy and used the 64bit package from apt-get to install wine and i still have the same issue. GLXgears returns:
```

glxgears 
87458 frames in 5.0 seconds = 17491.559 FPS
86813 frames in 5.0 seconds = 17362.510 FPS
86828 frames in 5.0 seconds = 17365.568 FPS
86796 frames in 5.0 seconds = 17359.137 FPS
86758 frames in 5.0 seconds = 17351.438 FPS
86828 frames in 5.0 seconds = 17365.500 FPS
86799 frames in 5.0 seconds = 17359.639 FPS
86842 frames in 5.0 seconds = 17368.348 FPS
86813 frames in 5.0 seconds = 17362.426 FPS

```
I am at a total loss now. Considering i havent done any changes at all to the system libraries or trying with different installations of Nvidia drivers etc (since last installation i used the 6.10 for a long time resulting in quiet alot of reinstalls and the like).

*screams out in frustration*
*drinks 10 cups of coffee*
*stretches*
Ok time to find another possible solution!

There thinking about the threads i had found earlier naming framerate as a possible evil thing that causes wine to fail using OpenGL.
Anyone who knows/suspects what they ment (they where very unclear about it, just "fixing it" solved it).
Since i am using Geforce 7900GT and the NVIDIA Driver Version: 1.0-9755 on my uname: 2.6.20-15-generic
It might be some xorg.conf settings that couldnt be set with the nvidia installer from Envy (like that framerate issue)

---

### Post by Garyu on 2007-05-05
This is my /etc/X11/xorg.conf part that deals with graphics:
```
Section "Monitor"
    Identifier     "Compaq S720"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Compaq S720"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Another thing you could compare with, owner and so on for wine opengl:
```
ls -l /usr/lib/wine/opengl32.dll.so 
-rw-r--r-- 1 root root 520780 2007-04-27 22:08 /usr/lib/wine/opengl32.dll.so

```

You could try disabling full screen glow in config.wtf, they say that speeds things up a lot:
SET ffxGlow "0"

Hey, while I am at it, why don't you take a look at my entire config.wtf (even though I have not done that many settings other than adding the opengl tag):
```
SET SoundOutputSystem "1"
SET gxApi "OpenGL"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "85"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "eu.logon.worldofwarcraft.com"
SET gxCursor "0"
SET Gamma "1.000000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmName "Silvermoon"
SET SoundZoneMusicNoDelay "1"
SET AmbienceVolume "0.60000002384186"
SET minimapZoom "0"
SET uiScale "1"
SET gameTip "21"
SET minimapInsideZoom "0"
SET gxMultisample "1"
SET lod "0"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET movieSubtitle "1"
SET weatherDensity "3"
SET mouseSpeed "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraTerrainTilt "1"
SET cameraDistanceMaxFactor "2"
SET locale "enGB"
SET soundMaxHardwareChannels "12"
SET doodadAnim "0"
SET shadowLevel "0"
SET cameraView "2"

```

If you come up with something else you want to look at, just let me know.


EDIT: Oh, hey, did you see that there is now a 64-bit repository for installing wine? So now it is possible to install wine with aptitude or apt-get or synaptic or whatever even in 64-bit version? I tried it and it works great, BUT for some reason ALSA sound disappeared. OSS sound still works though, so I don't think this matters (especially not since the "aoss"-command is available)...

---

### Post by RobinOfSweden on 2007-05-06
Omg dont say that!
I am using that version already :D
Was hoping that the next thing to ask how you did to install wine/graphic driver could lead to a solution :>

Aw crap! Atleast i know i havent failed anything in the installer >_>
Ok so what could it be then... hmm... i still think it could be a refresh thing...

Could it be my WoW installation?
Could something have gone wrong (i copied my install into my homedir which is in its own partition so i can save my data/settings and the like incase i need to reinstall etc) and then moved it back to the new .wine folder...
Though i cant see a reason how the WoW install could interfere in using OpenGL or the like...
any opinions on this?

*Edit*
Oh right i tested the way you had set your xorg.conf to the degree i didnt mess with any specific things for my TFT or GForce 7900GT
i also copy pasted your config.wtf and nothing changed :P
Damn if it only was that... and yea i rebooted before trying wow :) (so you dont waste your breath on asking :D)
BTW! 51-160 VertRefresh rate thats damn impressive! mine has:
```

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    ModelName      "STN SAMTRON"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

```

---

### Post by Garyu on 2007-05-06
Hmm, it's been so long since I installed WoW that I forgot how I did it. There are two options:
1) I installed it in Edgy (most probable)
2) I installed it in WinXP 

Now I only have a VMPlayer installation of XP (to do my taxes once a year). So if my WoW was installed on native XP it was done on a totally different machine. Though that might actually be the case. I can't say anything for sure on my installation method. Sorry. But I know that I have installed it in XP at least once. And I have installed it in Edgy at least once. So any of them might be true. I do know that my current installation is not installed, it is copied.

Have you been in touch with the blizzard help desk?

---

### Post by RobinOfSweden on 2007-05-06
No i havent been in contact with Blizzard help desk, you think they might know of a solution?
Well anything is worth trying by now, been going through as many threads as possible on the Ubuntu that involved framerate/OpenGL/WoW/Wine and i have found similliar errors but no solutions. Well not realy anything i can do about but keep on surfing with my google/ubuntu board :D

Even did Deadmines with my alt rogue with D3D, ended up with running ontop looking down on my rogue the entire time :D was playing in 3-7 FPS :D we succeded but it wasnt much of an enjoyment :P

---

### Post by RobinOfSweden on 2007-05-06
Behold the result of obstinance and pure will power!
I got the trial version of CrossOver and tried to run World of Warcraft (from my wine installation)
And guess what i get!

Err:
```

Your 3D accelerator card is not supported by World of Warcraft. Please install a 3D accelerator card with dual- TMU support.

```
Weeeee~!
Finaly we are getting somewhere!
Now i just need to figure out how to get it working!

---

### Post by RobinOfSweden on 2007-05-06
Ok i gave up >_>
Ok not realy i just gave up on my 64bit system >_<
32bit Feisty = WoW OpenGL with 88-110 FPS (just a quick check didnt play for long) in Stormwind :D so it works and it seems to be very stable so far :)

No need for more hacks for Flash and Java and hopefully i will also get a experience from MySQL-Query-Browser as well (didnt work so well for me in 64 edgy/feisty)

Anyway i think we can safely reduce my error with problems between my 64bit Nvidia drivers/OpenGL and Wine which ended with me not able to use OpenGL in wine!

Who knows there might be a fix to make a soft link on libraries that i couldnt find or that someone knows about (please for future 64bit users add them to forums :D )

Robin goes 32bit with his AMD Athlon 64FX Dual Core ...

---

### Post by marcozs on 2007-05-06
> **RobinOfSweden said:**
> Ok i gave up >_>
32bit Feisty = WoW OpenGL with 88-110 FPS (just a quick check didnt play for long) in Stormwind

I get that result with WoW and d3d... still haven't managed to make it work in opengl... by the way I get those framerates only in Stormwind... when I get to hellfire, drops even to 20 :(

---

### Post by RobinOfSweden on 2007-05-08
well i wonder if it realy is correct. I have never experienced any lagg even if it drops to 20 (as it did in Shattrah when i was at the Bank with alot of people around me) still i didnt notice any difference from when i had 100 to 20 ... think it could be some "wrong" response on the FPS meter. Did Shadow Labs in around 50-80 (if i looked down the floor i fought in 140FPS :D
Still i cant tell a difference. WoW aint that based on the fPS as any other First person shooter game so i am happy as it is.

What graphic card you using and which drivers? the Nvidia 9755? i used Envy to install my drivers which worked perfectly fine for me. I assume your Direct Rendering is on (glxinfo | grep direct) hmmm, did you activate your 3D acceleration? (in feisty and i assume edgy its in the system -> Administration -> Restricted Drivers Manager, if you have it activated it should be visible in there)
If not i know there was a guide for it but i cant remember the address, will take a look around after getting back from college.

---

### Post by marcozs on 2007-05-08
> **RobinOfSweden said:**
> What graphic card you using and which drivers? the Nvidia 9755? i used Envy to install my drivers which worked perfectly fine for me. I assume your Direct Rendering is on (glxinfo | grep direct) hmmm, did you activate your 3D acceleration?

Direct rendering is definetly on, what do you mean by activate 3d acceleration? I think it's on too though...
I am using the restricted drivers coming with Feisty, I think they are the 96XX? 
is there a big change with 9755? is there a repo with unofficial linux-restricted which include the 9755? I did read something about installing nvidia-glx-new instead of nvidia-glx... should I do that or use Envy?

---

### Post by peacebloom on 2007-06-05
Bump

I've had the same problems as RobinOfSweden with bad framerates, etc. I have 7.04 64bit feisty with a 7800gt. If I change from 64bit to 32bit feisty, will WoW look good again as in Windows?

---

### Post by Sammi on 2007-06-05
> **peacebloom said:**
> I've had the same problems as RobinOfSweden with bad framerates, etc. I have 7.04 64bit feisty with a 7800gt.64 bit versions of Wine have recently become available for Ubuntu Feisty. Are you sure you are using 64 bit Wine? 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

> **peacebloom said:**
>  If I change from 64bit to 32bit feisty, will WoW look good again as in Windows?Should be no difference. Why would there be?

---

### Post by peacebloom on 2007-06-05
> **Sammi said:**
> 64 bit versions of Wine have recently become available for Ubuntu Feisty. Are you sure you are using 64 bit Wine? 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Should be no difference. Why would there be?

oops, I meant to say I have the 64bit version of wine, and if I uninstall wine, and reinstall 32bit wine, would the fps change?

---

### Post by Sammi on 2007-06-05
> **peacebloom said:**
> oops, I meant to say I have the 64bit version of wine, and if I uninstall wine, and reinstall 32bit wine, would the fps change?Still don't see how that should be. Please try it out. There should be no harm done. You get different deb files here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by peacebloom on 2007-06-05
> **RobinOfSweden said:**
> Ok i gave up >_>
Ok not realy i just gave up on my 64bit system >_<
32bit Feisty = WoW OpenGL with 88-110 FPS (just a quick check didnt play for long) in Stormwind :D so it works and it seems to be very stable so far :)

No need for more hacks for Flash and Java and hopefully i will also get a experience from MySQL-Query-Browser as well (didnt work so well for me in 64 edgy/feisty)

Anyway i think we can safely reduce my error with problems between my 64bit Nvidia drivers/OpenGL and Wine which ended with me not able to use OpenGL in wine!

Who knows there might be a fix to make a soft link on libraries that i couldnt find or that someone knows about (please for future 64bit users add them to forums :D )

Robin goes 32bit with his AMD Athlon 64FX Dual Core ...


Well I've been referring to this, but it's possible I misunderstood.

---

### Post by Nkari on 2007-07-15
I actually have two 7600s in my computer and am currently trying to get WOW running. I have the 64bit version of feisty installed.

I can't seem to get it to do anything in GL mode, just tells me my card is no supported and I need a better graphics card with dual TMU support, someone mentioned this earlier in this thread.

In D3D I can log in to a server, and select a character to play, however the progress bar never moves on the splash screen, it just freezes up. Also if I go to create a new character I can do almost anything in there except change race or class.

So I am trying to get GL working to see if I can get further that way, like as in actually playing the game.

---

