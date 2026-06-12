---
title: "Eve online, Ubuntu, NVIDIA, Bumblebee... NOT WORKING!!!"
date: 2013-01-02
forum: Gaming &amp; Leisure
---

### Post by jackechanprime on 2013-01-02
I'm trying to get Eve online working on ubuntu 12.04. My machine has an NVIDIA GeForce GT 520M, and some sort of integrated intel chipset aswell. Apparently the drivers and hardware conflicted previously, and Bumblebee is the program I was told would help with that, which it seems to have.

And yet, Eve still does not work. I have it installed (via WINE), and the launcher-splash-screen-thing comes up fine, but hitting "play" makes it blink, then crash (actually it "self-terminates" whatever that means.)

If i'm missing any information (or being too vague) just ask, I'll clarify (and apologize profusely).

Please help?
~Q

---

### Post by jackechanprime on 2013-01-03
Someone I was talking to said the problem may lie with how WINE allocates system resources for applications to use. for example, EVE wants to use 500 units of GPU power, but WINE only allocates it 250 units of GPU power = insta-crash.

Is there anyway to adress this, or rule it out? This kind of stuff is waaaaaaaaay above my head. I dont have a clue where to look.

---

### Post by mastablasta on 2013-01-03
have you checked here for any possible tips, tricks and solutions: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25823](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25823)
 
also it has silver rating so some things may not work.
 
3D desktop effects can also interfere with wine.

---

### Post by bitwaba on 2013-01-03
Hi,

I just got EVE working on my system today after screwing around with it while I was drunk over the last few days (probably created more problems than it solved...)

From start to finish, I think there were 2 big errors that other people run into.

I installed the game by copying off my windows partition.  Installing from the installer file I would assume runs into the same issues.


I think the error you're having is the same one that I ran into.  When you game crashes, it should be a wine dialogue box. click the view details button.  If it is Unhandled exception: unimplemented function d3d11.dll.D3D11CreateDevice, then you need to disable d3d11.

run winecfg > libraries tab.
click the dropdown box with the "Add" button beside it.
Find d3d11, and click add.
d3d11 should now appear under "Existing Overrides:"
Click on it, then hit the "Edit button"
Select the "Disable" option, then OK.

Also, after getting my game to load up, I was only able to get to the character selection screen.  The game would crash again as soon as I started to load into the game world.  This was fixed by dropping all graphics settings to a minimum.

Hopefully that fixes your problem.



I took notes when I installed everything. Here's the steps I went through to get everything working:

> 

Before launching:
load up a terminal and check the output of  "wine --version".  I'm running 1.5.20, which i'm assuming you might be as well.
Also, make sure you've got a pretty recent version of winetricks (winetricks --version).  20120912 is the version that I think installs with PlayOnLinux.

Make sure you've got corefonts d3dx9_36 vcrun2005 vcrun2008 and vcrun2010 all installed via winetricks.

Now, run winecfg, then exit.  Just to make sure it set up the ~/.wine/ folder if you haven't run wine yet.

Add the below lines to ~/.wine/user.reg
```

[Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"VertexShaderMode"="hardware"

```

K. now to test.
cd /home/username/.wine/CCP/EVE
wine eve.exe

Launcher loads up. awesome
Now hit play.  Crash. damnit.
Wine error details:
Unhandled exception: unimplemented function d3d11.dll.D3D11CreateDevice

After about about an hour of drunkenstumbling around the internet, looks like people used to have it working on wine-1.5.19, but 1.5.20 broke it.  The fix:
run winecfg > libraries tab.
click the dropdown box with the "Add" button beside it.
Find d3d11, and click add.
d3d11 should now appear under "Existing Overrides:"
Click on it, then hit the "Edit button"
Select the "Disable" option, then OK.

Now, Launcher loads up, and clicking Play launches the game.  I get all the way to the Character selection screen. But when clicking on a character, the game immediately crashes. Seems to be crashing as soon as the actual game environment starts to load.

Did a bit of searching around, forgot to do something from the install guide on eveonline.com: disable HDR and shadows.

Easy enough to fix.  wine eve.exe, click Play. before logging in, hit esc and drop all graphics settings to minimum.  Log in. select character.  Undock from station. Dance.



---

### Post by jackechanprime on 2013-01-04
Re: Eve online, Ubuntu, NVIDIA, Bumblebee... NOT WORKING!!!
Hi,

I just got EVE working on my system today after screwing around with it while I was drunk over the last few days (probably created more problems than it solved...)

From start to finish, I think there were 2 big errors that other people run into.

I installed the game by copying off my windows partition. Installing from the installer file I would assume runs into the same issues.


I think the error you're having is the same one that I ran into. When you game crashes, it should be a wine dialogue box. click the view details button. If it is Unhandled exception: unimplemented function d3d11.dll.D3D11CreateDevice, then you need to disable d3d11.

run winecfg > libraries tab.
click the dropdown box with the "Add" button beside it.
Find d3d11, and click add.
d3d11 should now appear under "Existing Overrides:"
Click on it, then hit the "Edit button"
Select the "Disable" option, then OK.

Also, after getting my game to load up, I was only able to get to the character selection screen. The game would crash again as soon as I started to load into the game world. This was fixed by dropping all graphics settings to a minimum.

Hopefully that fixes your problem.



I took notes when I installed everything. Here's the steps I went through to get everything working:

Quote:

Before launching:
load up a terminal and check the output of "wine --version". I'm running 1.5.20, which i'm assuming you might be as well.
Also, make sure you've got a pretty recent version of winetricks (winetricks --version). 20120912 is the version that I think installs with PlayOnLinux.

Make sure you've got corefonts d3dx9_36 vcrun2005 vcrun2008 and vcrun2010 all installed via winetricks.

Now, run winecfg, then exit. Just to make sure it set up the ~/.wine/ folder if you haven't run wine yet.

Add the below lines to ~/.wine/user.reg
Code:

[Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"VertexShaderMode"="hardware"

K. now to test.
cd /home/username/.wine/CCP/EVE
wine eve.exe

Launcher loads up. awesome
Now hit play. Crash. damnit.
Wine error details:
Unhandled exception: unimplemented function d3d11.dll.D3D11CreateDevice

After about about an hour of drunkenstumbling around the internet, looks like people used to have it working on wine-1.5.19, but 1.5.20 broke it. The fix:
run winecfg > libraries tab.
click the dropdown box with the "Add" button beside it.
Find d3d11, and click add.
d3d11 should now appear under "Existing Overrides:"
Click on it, then hit the "Edit button"
Select the "Disable" option, then OK.

Now, Launcher loads up, and clicking Play launches the game. I get all the way to the Character selection screen. But when clicking on a character, the game immediately crashes. Seems to be crashing as soon as the actual game environment starts to load.

Did a bit of searching around, forgot to do something from the install guide on eveonline.com: disable HDR and shadows.

Easy enough to fix. wine eve.exe, click Play. before logging in, hit esc and drop all graphics settings to minimum. Log in. select character. Undock from station. Dance.

***************************************

Ok going through these suggestions, I first went into wine to track down that library. Turns out I dont have it to begin with, but I do have d3d10... perhaps just an updated version? Regardless, not going to play russian roulette with that until someown who understands that .dll stands for dot-hell gives me a green light.

I'm running wine 1.4 apparently, so that may be the diffrence.
Winetricks version = 20120308

"Make sure you've got corefonts d3dx9_36 vcrun2005 vcrun2008 and vcrun2010 all installed via winetricks."
^ not sure how to do this from scratch, but I do seem to vaguely remember one of the other guides I ran across having me do this... at least the vcrun names seem familiar. Please tell me how to confirm/install these.

Gotta go for now, life calls. Gotta cut this post short. will be back.

---

### Post by bitwaba on 2013-01-05
Did you try following the guide directly from the guys at CCP?
[http://wiki.eveonline.com/en/wiki/Install_EVE_on_Linux_with_Wine](http://wiki.eveonline.com/en/wiki/Install_EVE_on_Linux_with_Wine)

its not very detailed, so you kinda need to know your way around linux and be able to follow their poorly formatted sections.

First thing I do when trying to get most games to work under wine are make sure that wine is pretty recent, and make sure i have a recent version of winetricks installed.  Those 2 things alone might make all the difference.

how to install wine-1.5:
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

how to install the latest winetricks:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
One thing I'd add to the winetricks install is after downloading and chmoding it, I would copy it to /usr/bin/ and /usr/bin/X11

EDIT: the d3d11.dll is most likely not on your list of possible exceptions because of your wine version.  Adding it to this portion of winecfg, then disabling it is simply telling wine to not load directX 11. If it breaks something new, delete it from winecfg.  If you want to start over from a fresh wine environment, just go cd ~, mv .wine .wine.backup, then run winecfg, and you'll be right back where you started with a clean winecfg

---

