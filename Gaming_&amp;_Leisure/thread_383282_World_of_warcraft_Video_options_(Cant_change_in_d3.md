---
title: "World of warcraft Video options (Cant change in d3d) help"
date: 2007-03-13
forum: Gaming &amp; Leisure
---

### Post by Rocket-Dog on 2007-03-13
Ok I searched for an answer but couldnt find one. OpenGL is working fine, the only thing I want to do is change the Video options to lower settings since I have some dated hardware. Since doing that in OpenGL makes WoW crash I tried to do it the d3d way by changing it in the Config.wtf file. It will start up fine in d3d but as soon as I accept the changed video options it will crash. Please help guys just wanted to get some gaming in. My Comp specs are ( P4 2.0, 512 ddr, radeon 9600XT "with the correct drivers" )

---

### Post by Ferrat on 2007-03-13
how does your config.wtf look?

---

### Post by Sammi on 2007-03-13
There is a mod that disables three functions that make the game crash while changing video settings. You will not be able to change these few settings(including resolution), but everything else should work. 

The addon is found here [http://fuxsake.net/t51-Apply-Forehead.html](http://fuxsake.net/t51-Apply-Forehead.html), and you should extract the zipped folder in to /Interface/AddOns/ in your WoW directory. Then enable it under AddOns in the choose character screen. You probably need to tick the option, which says Load out of date AddOns, for it to work. 

You can still change your resolution manually by editing this line in config.wtf by hand:
```
SET gxResolution "1024x768"
```

---

### Post by willskills on 2007-03-13
It is possible to set loads of options in your config.wtf!

Please see here for a full list; [http://www.wowwiki.com/Config.wtf_defaults](http://www.wowwiki.com/Config.wtf_defaults)

---

### Post by Ybra on 2007-03-18
> **Sammi said:**
> 
The addon is found here [http://fuxsake.net/t51-Apply-Forehead.html](http://fuxsake.net/t51-Apply-Forehead.html), and you should extract the zipped folder in to /Interface/AddOns/ in your WoW directory. Then enable it under AddOns in the choose character screen. You probably need to tick the option, which says Load out of date AddOns, for it to work. 


how do i zipp something into the wine folders, im kinda new at this and i haven't fond anyway to browse my "c:"

EDIT: nwm i found this :P [http://ubuntuforums.org/showthread.php?t=371276](http://ubuntuforums.org/showthread.php?t=371276)

---

### Post by fktt on 2007-03-18
> **Sammi said:**
> The addon is found here [http://fuxsake.net/t51-Apply-Forehead.html](http://fuxsake.net/t51-Apply-Forehead.html), and you should extract the zipped folder in to /Interface/AddOns/ in your WoW directory. Then enable it under AddOns in the choose character screen. You probably need to tick the option, which says Load out of date AddOns, for it to work. 

You can still change your resolution manually by editing this line in config.wtf by hand:
```
SET gxResolution "1024x768"
```
thanks Sammi just what i needed! :)

---

### Post by dstanzler on 2007-03-27
@obscured
@sammi

I just used obscured's "applytoforehead" strategy to correct my WOW resolution issue. I changed my resolution to 1024x768 instead of 1280x1024. However, when I restart WOW and get past Launcher.exe, the game seems to reset my resolution to 1280x1024. It seems that everytime I start wow with wine and I get the Launcher.exe message: an internal error has occured, my resolution gets changed back to its default 1280x1024.

How can I set my resolution in WOW so that  so that I have to reset completely static ?

So far changing "SET gxResolution "1024x768" has not worked.
So far adding a modeline to section Monitor" in etc/X11/xorg.conf has not worked.

Aside from getting the "Launcher.exe" error message everything seems to be working fine.

I'm on Ubuntu dapper Desktop 6.06 and I have installed my nVidia drivers. Wow runs fine but the resolution issue annoys me.

---

### Post by dstanzler on 2007-03-27
Okay, this is how I resolved my Wow issue.

_The Problem_

Launcher crashes on its own but it doesn't mess up the resolution.

I found out that wow.exe alters the resolution of the game on startup by running WOW.exe and then checking my Config.wtf.

I followed up on my research checking my Errors folder located in my World of Warcraft wine directory. As it turns out Wow.exe was having this error:

"**The memory could not be "read"**"

A quick google revealed that its a Microsoft Windows 2000 error. Hence, the issue is with Wine.


_The Solution_

Open terminal and run winecfg.

In the applications tab under default click "Add application..."

Select WOW.exe.

Then from the "Windows Version" drop down menu, select "Windows 2000."

Click the graphics tab.

**Uncheck** "Allow Directx apps to stop the mouse leaving their window."
Check "Allow the window manager to control the windows."
Check "Emulate a virtual desktop.

Enter the resolution that you want to run Wow.exe at.

**Uncheck** "Allow Pixel Shader."

Click OK and run WOW at the resolution that you want!

Note, this will run in a wine virtual desktop window. I have been able to adjust the resolutions in Wow and in the virtual desktop window in order meet my full screen-highest resolution Wow needs.

_Further Notes_
I run Ubuntu Dapper 6.06 desktop client.
This is my first install of Ubuntu, EVER, so thank you to this awesome community.

I use 
2.1 GHZ intel pentium
nVIDIA 6800 ULTRA GT
2000mb DDR ram
55g HD

I also have Ubuntu running on an ibook powerpc G4.

---

### Post by sdman on 2007-03-29
Like you all I installed the applytoforhead addon. On the icon command  I added -d3d instead of -opengl. Excerpt of config.wtf :

```
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET accountName "--removed--"
SET movie "0"
SET expansionMovie "0"
SET checkAddonVersion "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET realmName "Thrall"
SET gxApi "d3d"
SET ffxDeath "0"
SET ffxGlow "="
SET gameTip "2"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
```

The problem Im having is it gets to the character screen I enable out-of-date addons and click enter to enter the game but it freezes and crashes to desktop without errors any suggestions?

edit: nvm now im getting error #132 after I looked under error logs. I thought I fixed it from that error but guess not.. too bad I forgot what the fix was..google is my friend..

---

### Post by sdman on 2007-03-29
Well I got it to work I resinked my ram and no error 132 but when I log in everything is upside down the tiles on the land are pink and green ](*,) any suggestions?

 Scratch all this.. come to find out the fps registry tweak does not work with d3d, Im running 120fps so that is good enough for me without all the other features. I found the information out here [resolved article]("http://appdb.winehq.org/appview.php?iVersionId=5606"):

> Do you need 100% boost to your FPS ?

Then apply the same DisabledExtensions registry key as described above. This works for ATI & Nvidia plus
others but only in opengl mode, not D3D.

---

