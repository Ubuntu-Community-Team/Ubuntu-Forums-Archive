---
title: "Ubuntu 10.04 32bit running UT99GOTY linux client"
date: 2010-08-17
forum: Gaming &amp; Leisure
---

### Post by sxxxe83 on 2010-08-17
In this case I had the original UT99-GOTY CD1 & CD2 as .iso files on my computer.

**1. Prerequisites: libgtk1.2**

```
sudo sed s/lucid/jaunty/g /etc/apt/sources.list -i
sudo aptitude update
sudo aptitude install -y libgtk1.2
sudo sed s/jaunty/lucid/g /etc/apt/sources.list -i
sudo aptitude update
```

**Loki installer:**
Then get the Loki installer or both if one is not working.
[http://www.liflg.org/?catid=6&gameid=51]("http://www.liflg.org/?catid=6&gameid=51")

I used the default install path: /usr/local/games/ut
and the S3TC textures.

```
sudo mkdir /media/cdrom
sudo mount -o loop ~/ut99-goty-cd1.iso /media/cdrom
sudo bash ~/unreal.tournament_436-multilanguage.run
sudo umount /media/cdrom
sudo mount -o loop ~/ut99-goty-cd2.iso /media/cdrom

```

After the installer is finished, do this.

```
sudo mkdir -p ~/.loki/ut/Cache
sudo chmod 775 -R ~/.loki/ut
```

If u want to, you can test the game now. If u have a dualcore CPU it will most likely be running at a too high speed.

Custom UT99 Launcher SPEED PROBLEMS:
[http://www.mediafire.com/?fjia8qs5ulggcbc]("http://www.mediafire.com/?fjia8qs5ulggcbc")

```
sudo mv /path/to/utcustom.sh /usr/local/games/ut/
sudo chmod +x /usr/local/games/ut/utcustom.sh
```

**Custom UT99 Cache Cleaner:**
[http://www.mediafire.com/?v5hsmglkg5k9pt5]("http://www.mediafire.com/?v5hsmglkg5k9pt5")

```
sudo mv /path/to/ut99cache.sh ~/.loki/ut/
sudo chmod +x ~/.loki/ut/ut99cache.sh
```

Insert this:
```
bash /path/to/file/ut99cache.sh
```

3 lines from the top in this file:
```
/usr/local/games/ut/utcustom.sh
```

So everytime I start UT99, the cache is also cleaned.

Then on your desktop create an launcher with this:
```
/usr/local/games/ut/utcustom.sh
```

After testing that everything worked, I did this too:
```
sudo chown -R username:username ~/.loki/ut
sudo chown -R username:username /usr/local/games/ut
```

Some files just got deleted from my cache, not moved. On my "Compal IFL90", UT99 runs flawless on Linux compared to Windows, and I tried all dual core fix, affinity settings and non worked.

**The Enhanced OpenGL Renderer With S3TC settings**

Linux port of "The enhanced OpenGL renderer" v3.1:
[http://www.mediafire.com/file/cvuh88che0tiy7s/OpenGLDrv.so](http://www.mediafire.com/file/cvuh88che0tiy7s/OpenGLDrv.so)

I have this in my UnrealTournament.ini:
```

[Engine.Engine]
GameRenderDevice=OpenGLDrv.OpenGLRenderDevice
WindowedRenderDevice=OpenGLDrv.OpenGLRenderDevice
RenderDevice=OpenGLDrv.OpenGLRenderDevice

[OpenGLDrv.OpenGLRenderDevice]
ZRangeHack=True
AAFilterHint=2
NoAATiles=False
NumAASamples=8
UseAA=True
RequestHighResolutionZ=True
MaskedTextureHack=False
SmoothMaskedTextures=False
FrameRateLimit=125
SwapInterval=0
UseFragmentProgram=True
UseVertexProgram=True
UseCVA=True
UseMultiDrawArrays=True
TexDXT1ToDXT3=False
DynamicTexIdRecycleLevel=100
CacheStaticMaps=False
UseTexPool=True
UseTexIdPool=True
UseSSE2=True
UseSSE=True
BufferTileQuads=True
BufferClippedActorTris=False
SinglePassDetail=True
SinglePassFog=True
ColorizeDetailTextures=False
DetailClipping=False
UseDetailAlpha=True
DetailMax=8
RefreshRate=0
MaxTMUnits=0
NoFiltering=False
NoMaskedS3TC=False
MaxAnisotropy=8
UseTNT=False
Use16BitTextures=False
UseS3TC=True
UseAlphaPalette=True
AutoGenerateMipmaps=True
UseTrilinear=True
UsePrecache=True
AlwaysMipmap=True
ShareLists=False
UsePalette=True
UseMultiTexture=True
UseBGRATextures=True
UseZTrick=False
MaxLogTextureSize=8
MinLogTextureSize=0
MaxLogVOverU=8
MaxLogUOverV=8
OneXBlending=False
GammaCorrectScreenshots=False
GammaOffsetBlue=0.000000
GammaOffsetGreen=0.000000
GammaOffsetRed=0.000000
GammaOffset=0.000000
LODBias=0.000000
DetailTextures=True
DescFlags=0
Description=Nvidia 8600M GT
HighDetailActors=True
Coronas=True
ShinySurfaces=True
VolumetricLighting=True

```

For a complete list and what the settings do, check this site:
[http://www.cwdohnal.com/utglr/settings.html](http://www.cwdohnal.com/utglr/settings.html)

High End S3TC Textures Retextured:
[http://www.unrealtexture.com/UT/Website/Downloads/Textures/HighEnd/MasterFiles/MasterFilesHighEnd.htm](http://www.unrealtexture.com/UT/Website/Downloads/Textures/HighEnd/MasterFiles/MasterFilesHighEnd.htm)

[B]
Optional:[/B]
On my Windows install of UT99 I had lots of extra stuff, high res textures, maps etc.

I put my windows UT99 install folder on an external disk, and connected it to my linux machine

```
sudo cp -v /path/to/windows/ut99/Sounds/* /usr/local/games/ut/Sounds/
sudo cp -v /path/to/windows/ut99/Music/* /usr/local/games/ut/Music/
sudo cp -v /path/to/windows/ut99/Maps/* /usr/local/games/ut/Maps/
sudo cp -v /path/to/windows/ut99/Textures/* /usr/local/games/ut/Textures/
```

Run chmod on all folders you copied files to.
```
sudo chmod 755 /usr/local/games/ut/Sounds/*
sudo chmod 755 /usr/local/games/ut/Music/*
sudo chmod 755 /usr/local/games/ut/Maps/*
sudo chmod 755 /usr/local/games/ut/Textures/*
```

Source/Useful links:
UT99 on ubuntu
[http://www.xantaz.net/ut-99/installing-unreal-tournament-goty-edition-linux#Renderer](http://www.xantaz.net/ut-99/installing-unreal-tournament-goty-edition-linux#Renderer)
[http://piotr.gabryjeluk.pl/dev:playing-unreal-tournament-on-ubuntu-lucid](http://piotr.gabryjeluk.pl/dev:playing-unreal-tournament-on-ubuntu-lucid)
[http://www.fingel.com/ut/howtos/utonlinux.html](http://www.fingel.com/ut/howtos/utonlinux.html)

The Enhanced OpenGL Renderer
[http://www.cwdohnal.com/utglr/](http://www.cwdohnal.com/utglr/)

Linux Port OpenGL Renderer
[http://forums.beyondunreal.com/showthread.php?t=161177](http://forums.beyondunreal.com/showthread.php?t=161177)
[http://forums.gentoo.org/viewtopic-t-452678.html](http://forums.gentoo.org/viewtopic-t-452678.html)

Linux port of "The enhanced OpenGL renderer" v3.6: **THIS ONE HAS BROKEN FRAMERATELIMIT**
[http://github.com/stephank/surreal/downloads](http://github.com/stephank/surreal/downloads)
[http://forums.beyondunreal.com/showthread.php?t=191623](http://forums.beyondunreal.com/showthread.php?t=191623)

Unreal Tournament 99 with High Res Textures (Retextured)
[http://www.unrealtexture.com/General/Website/Forums/Forums01/viewtopic.php?f=23&t=44](http://www.unrealtexture.com/General/Website/Forums/Forums01/viewtopic.php?f=23&t=44)
[http://www.unrealtexture.com/General/Website/Forums/Forums01/viewtopic.php?f=23&t=19](http://www.unrealtexture.com/General/Website/Forums/Forums01/viewtopic.php?f=23&t=19)

sXe

---

### Post by sxxxe83 on 2010-08-28
Added link to a Linux port of the "Enhanced OpenGL renderer", finally UT99 on linux is as good as it gets.

sXe

---

### Post by beast2k on 2010-08-28
Awesome how does it run? it must be really fast even with all the graphics turned up as high as they will go. Have you tried UT2004 CD edition? This is the one that gives me grief I can only get as far as the first CD. Strange thing is I seem to remember when Ubuntu first came out all I had to do is double click the linux-installer.sh file it then asked me if I wanted to read it or open it, I choose open and I could install all 5 CD's as normal. I noticed how you did it with this version is way more involved. I am going to try it though it should be fun. Cheers.

---

### Post by sxxxe83 on 2010-08-30
UT99 on Ubuntu 10.04 with the settings described above it actually runs better on Linux than Windows (on my laptop),no "dual core" problems with the fix above, no problems with "overlay" mouse pointer when getting in and out of fullscreen.

Running at 1680x1050x32 on my Compal IFL90, dual core something, 2GB RAM, Nvidia 8600M GT 512MB, Im impressed how good it still looks.

sXe

---

