---
title: "World of Warcraft unplayable after every troubleshooting attempt"
date: 2007-06-14
forum: Gaming &amp; Leisure
---

### Post by sigmund1898 on 2007-06-14
Well I'm at a total loss.  I've spent the last few days pouring over these forums and help websites and I feel like I've done everything I can do.  My fps runs very low (as low as 2fps in booty bay..) and I can't seem to figure out what's causing it.  Unfortunately this game runs so perfect under windows (grrr..).  

My specs are: NVIDIA GeForce 6200OC and 2GB RAM.  The only thing that I'm still not sure about is my nvidia driver.  I currently have the driver 1.0-9631 although I have tried 9755 and all compatible NVIDIA drivers that the program 'Envy' can provide.  No effect at all on performance (but I had a fun time getting xserver to restart).   I've done all the tweaks and solutions provided by [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) - and had little to no effect on performance.

Here is what my xorg.conf looks like: 

```
Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
    Option         "UseFastTLS" "2"
EndSection
```

And here is my config.wtf -

```
SET gxApi "OpenGL"
SET SoundOutputSystem "1"
SET gxColorBits "24"
SET hwDetect "0"
SET gxDepthBits "24"
SET gxResolution "1680x1050"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET farclip "177"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET locale "enUS"
SET expansionMovie "0"
SET accountName ""
SET realmName ""
SET gameTip "31"
SET mouseSpeed "1.5"
SET MusicVolume "0.5"
SET SoundVolume "0.60000002384186"
SET MasterVolume "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET AmbienceVolume "0.69999998807907"
SET spellEffectLevel "0"
SET Gamma "1.000000"
SET weatherDensity "0"
SET uiScale "1"
SET M2UsePixelShaders "1"
SET ffxDeath "0"
SET ffxGlow "0"
SET UnitNameNPC "1"
SET EnableErrorSpeech "0"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET SoundZoneMusicNoDelay "1"
SET statusBarText "1"
SET ChatBubblesParty "1"
SET guildMemberNotify "1"
SET patchlist "us.version.worldofwarcraft.com"
SET checkAddonVersion "0"
SET gxMaximize "1"
SET DesktopGamma "1"
SET shadowLOD "0"
SET profanityFilter "0"
SET showGameTips "0"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET lod "1"
SET useWeatherShaders "0"
SET gxCursor "0"
SET SoundNumChannels "128"
SET gxFixLag "0"
SET doodadAnim "0"
SET gxTripleBuffer "1"
SET baseMip "1"
SET ffx "0"
```

It looks fine to me but if there is an error please point it out.

Note that I have tried to run the game at a lower resolution and at the highest resolution, and no change in frame rate.  Also I have all antialiasing and antisotropic filtering turned off or at the lowest setting (I've heard this increases the frame rate).  I have the latest version of Wine and run several programs under it with no problems.  Any suggestions/comments would be greatly appreciated.

---

### Post by cessna_89702 on 2007-06-14
try this command:

```
glxgears
```

and see what the frame rate looks like

---

### Post by sonicborg on 2007-06-14
atleast you get to have low frame rates, mine is crashing as soon as i login and it tries to draw my char on screen. the music keeps playing though

---

### Post by sigmund1898 on 2007-06-14
> **cessna_89702 said:**
> try this command:

```
glxgears
```

and see what the frame rate looks like


Wow that's a nice little utility.

301 frames in 5.0 seconds = 60.185 FPS
290 frames in 5.0 seconds = 57.971 FPS
299 frames in 5.0 seconds = 59.772 FPS
299 frames in 5.0 seconds = 59.770 FPS
299 frames in 5.0 seconds = 59.770 FPS
299 frames in 5.0 seconds = 59.771 FPS

If only it would look like that in the game..

---

### Post by cessna_89702 on 2007-06-14
You should make sure you have all the drivers or the most up to date one for that card. Im not sure how to fix it because I had a problem like that so I just use a dual boot and use windows for games.

---

### Post by hikaricore on 2007-06-14
> **sigmund1898 said:**
> Wow that's a nice little utility.

301 frames in 5.0 seconds = 60.185 FPS
290 frames in 5.0 seconds = 57.971 FPS
299 frames in 5.0 seconds = 59.772 FPS
299 frames in 5.0 seconds = 59.770 FPS
299 frames in 5.0 seconds = 59.770 FPS
299 frames in 5.0 seconds = 59.771 FPS

If only it would look like that in the game..

Unlike in-game FPS counters, 57-60fps in glxgears is **BAD**.

I have nearly the same card as you.  Something is seriously wrong.

> [hikaricore@devistate:~ (4.2 Mb)]$ glxgears
7228 frames in 5.0 seconds = 1445.518 FPS
10174 frames in 5.0 seconds = 2034.751 FPS
10149 frames in 5.0 seconds = 2029.775 FPS
9770 frames in 5.0 seconds = 1953.875 FPS
9919 frames in 5.0 seconds = 1983.758 FPS
8413 frames in 5.0 seconds = 1682.462 FPS
9791 frames in 5.0 seconds = 1958.133 FPS


And this is on a _PCI_ version of the 6200 which sucks badly.

Check the output of:

```

glxinfo | grep rendering
```
for any strange errors.  It should simply reply with:

> direct rendering: Yes

One other thing strikes me as very odd.

This line:
> Option         "UseFastTLS" "2"

To the best of my knowledge this line is for ATI cards.
Unless you have a very specific reason for it being there it may not belong in your xorg.conf.

If you have installed your nvidia drivers with Envy (which works great but can sometimes cause issues) I would suggest you try installing the brand new 100 series release of drivers from Nvidia after running the remove option in Envy to clean up it's bit of mess.

Here's the latest from Nvidia btw: [http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

This link is for the 32 bit version, I'm assuming you're on a 32 bit system.

Good luck,

--Aaron

p.s.  If you want to post your full /etc/X11/xorg.conf file here, or _atleast the screen/display sections_ I can tell you if anything looks out of place.  ^_^  It may be awhile before I can respond though depending on work tomorrow.

---

### Post by sigmund1898 on 2007-06-14
> p.s.  If you want to post your full /etc/X11/xorg.conf file here, or _atleast the screen/display sections_ I can tell you if anything looks out of place.  ^_^  It may be awhile before I can respond though depending on work tomorrow.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Sat May 26 01:03:50 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "6 7 5"
    Option         "ButtonMapping" "1 2 3 4 5 6 7"
    Option         "Emulate3Buttons" "YES"
    Option         "Buttons" "7"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I decided to look into this and noticed some differences in the "Screen" section between mine and most other xorg.conf files others have posted.  The major difference was I lacked these three lines so I added them.

```

    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
```

And now I'm getting these refresh rates in glxgears:

6173 frames in 5.0 seconds = 1234.460 FPS
6579 frames in 5.0 seconds = 1315.669 FPS
6583 frames in 5.0 seconds = 1316.472 FPS
6580 frames in 5.0 seconds = 1315.821 FPS

BUT - No difference in WoW ](*,)

By the way, dlxinfo did return 'direct rendering: Yes'.

I just want to be rid of windows for good.. it almost seems too much to ask...

---

### Post by hikaricore on 2007-06-14
You don't by any chance have beryl or "desktop effects" enabled while trying to run WoW do you?

Because while that card can handle it, it doesn't do so very well.  ^_^

You may also want to launch in d3d mode to lower a few video settings.  Example:  SET gxTripleBuffer "1"

Turn everything you can to low or off, save, logout, then relaunch in opengl mode to see if it helped.

Now I'm really going to bed for the night hehe.

--Aaron

---

### Post by sigmund1898 on 2007-06-14
> **hikaricore said:**
> You don't by any chance have beryl or "desktop effects" enabled while trying to run WoW do you?

Because while that card can handle it, it doesn't do so very well.  ^_^

You may also want to launch in d3d mode to lower a few video settings.  Example:  SET gxTripleBuffer "1"

Turn everything you can to low or off, save, logout, then relaunch in opengl mode to see if it helped.

Now I'm really going to bed for the night hehe.

--Aaron

I do have Beryl installed but I'm always sure it's not running while I game.  And one of the first things I did was turn down the video settings.  I just tried putting the card into a different PCI slot.  Didn't help, naturally.  Since this game runs near perfect in windows I know it's not the card itself.  There has to be something I've missed.  I am running ubuntu x86_64 and not i386 because I have an AMD64, would there be an advantage to running the i386 distribution?  Or maybe simulating the i386 version of Wine?  I found out I have Wine 0.9.37 and when I tried to update to 0.9.38 it says I already have the latest drivers installed.  The link for the latest 64-bit version of Wine is broken and is said hasn't been built yet.  However I've seen places on the internet that says it's out already.  Can anyone clear that up?  Assuming it has anything to do with my problem.

---

### Post by Cappy on 2007-06-14
> **sigmund1898 said:**
> I do have Beryl installed but I'm always sure it's not running while I game.  And one of the first things I did was turn down the video settings.  I just tried putting the card into a different PCI slot.  Didn't help, naturally.  Since this game runs near perfect in windows I know it's not the card itself.  There has to be something I've missed.  I am running ubuntu x86_64 and not i386 because I have an AMD64, would there be an advantage to running the i386 distribution?  Or maybe simulating the i386 version of Wine?  I found out I have Wine 0.9.37 and when I tried to update to 0.9.38 it says I already have the latest drivers installed.  The link for the latest 64-bit version of Wine is broken and is said hasn't been built yet.  However I've seen places on the internet that says it's out already.  Can anyone clear that up?  Assuming it has anything to do with my problem.

There are 64-bit build problems with the newest Wine, don't worry about it though. It isn't important. There wouldn't be any benefit to moving to i386.

I would re-install your video card drivers. Use Envy to remove your drivers (if you are using the drivers from Envy).
Then re-install with the pre-packaged Ubuntu drivers:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```
(reboot)

For best results save it to a file such as ```
nvidiainstall.sh
```. Switch to a virtual terminal (Alt + Control + F1) use command
```

sudo /etc/init.d/gdm stop
chmod +x nvidiainstall.sh
sudo sh nvidiainstall.sh

```

---

### Post by hikaricore on 2007-06-14
The 64bit version of WINE is known to be problematic at best >.<  since WINE is mostly 32bit at the moment, the 64bit version is moot.

Also I wasn't aware that your card was PCI.  PCI cards are limited by your FSP (front side bus) as well as having to compete with any other PCI cards in use at the moment  PCI is a major bottleneck and limits the throughput to a trickle if it's competing with other hardware.  Perhaps this is an issue with a hardware conflict which exists in Linux and which doesn't exist in your Windows setup.  Personally I only get 15-25 fps at best while running my system with a stripped down X server and no other applications but essential system applications.  I really don't play anymore but being in towns and other busy areas was hell at best.  It's also possble that your card doesn't have decent opengl support, but that's probably not the case, just an idea.

Anyway try out the 32bit version, there are howtos on setting this up in a 64bit environment and see what happens.

Aside from that I'm mostly out of ideas.

---

### Post by MikeEvans on 2007-06-15
If you haven't tried envy to setup your graphics driver I would recommend it.  That and following the guide at the wow wiki got the game running nice for me. [ http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine")

---

### Post by sigmund1898 on 2007-06-17
> **hikaricore said:**
> The 64bit version of WINE is known to be problematic at best >.<  since WINE is mostly 32bit at the moment, the 64bit version is moot.

Also I wasn't aware that your card was PCI.  PCI cards are limited by your FSP (front side bus) as well as having to compete with any other PCI cards in use at the moment  PCI is a major bottleneck and limits the throughput to a trickle if it's competing with other hardware.  Perhaps this is an issue with a hardware conflict which exists in Linux and which doesn't exist in your Windows setup.  Personally I only get 15-25 fps at best while running my system with a stripped down X server and no other applications but essential system applications.  I really don't play anymore but being in towns and other busy areas was hell at best.  It's also possble that your card doesn't have decent opengl support, but that's probably not the case, just an idea.

Anyway try out the 32bit version, there are howtos on setting this up in a 64bit environment and see what happens.

Aside from that I'm mostly out of ideas.

Thanks for all your help and support.  I resolved this issue by using the 32-bit version of wine.  Since I normally got 30-60 fps using windows, I knew it wasn't a hardware problem.  And now it runs better than my roommate's computer.  You are right saying the 64-bit version of Wine is problematic considering now Neverwinter Nights runs just as good as it did on windows.  And now, I can finally format my windows partition! Again, thank you.
-Josh

---

