---
title: "WINE screen flicker on ATi"
date: 2009-05-02
forum: General Help
---

### Post by Legace on 2009-05-02
Hi guys,

I am running WINE 1.1.16 and each time I open any Windows program (Office 2007, Wine Configuration, regedit, etc.) the screen flickers for about a second.

Is there a way to solve this as it is pretty annoying..?

---

### Post by Legace on 2009-05-02
By the way, I'm using the open source drivers.

---

### Post by bturig on 2009-07-01
I have the same problem on my laptop's external monitor, when opening any wine application.

Have you had any clues on getting this resolved?

---

### Post by Karolis on 2009-07-15
I have the same problem using newest wine (intel video drivers).

---

### Post by landy rover on 2009-07-15
i have actually the same problem with the latest Wine ,,,but does mot flicker.... my Ati Drivers are activated and my visual effects is working fine but when i run games like counter strike or need for speed underground it works perfectly till it reaches the main menu of the game or program it force quits the program then my screen resolution is very small 

:guitar::popcorn::KS

---

### Post by AllRadioisDead on 2009-07-18
Same problem. Any fix?

---

### Post by advocate 21 on 2009-10-09
turn off visual effects. that works for me

---

### Post by dagasaga on 2010-02-12
Same thing here, but disabling desktop effects didn't work.

---

### Post by fragov on 2010-05-21
Same problem. Each time when any WINE application is loading second monitor start flicking. It makes me feel terrible.

---

### Post by leonexis on 2010-06-17
Sorry to respond to such an old post, but this was #1 when I googled "wine video flicker starting a new application".

If you get a black screen for a moment when you run 'xrandr' from a console, then this might actually not be a Wine bug, but a problem with the video card driver. I have seen it on both Intel and ATI drivers. See [Wine Bug #15214]("http://bugs.winehq.org/show_bug.cgi?id=15214").

There is a workaround to this issue: 

[LIST=1]
[*]Start Wine's Registry Editor
[*]Navigate to "HKEY_CURRENT_USER\Software\Wine\X11 Driver". You may need to create X11 Driver.
[*]Create a new key called "UseXRandR" and set it to "N".
[/LIST]
That should prevent Wine from using XRandR and hopefully fix the annoying black flicker. More useful registry entries for Wine can be found on the Wine Wiki page [UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys").

Hope that helps.

-Leo

---

### Post by M@s on 2010-08-22
Hey, bumping this thread because I have the same problem: The screen flickers on boot, when starting Wine applications and when running the xrandr command. I tried to disable XRandR according to the solution above, but it didn't fix the problem.

Any other solutions? :)

Running Ubuntu 10.04 x64, ATI Radeon HD 4850.


/EDIT:
Uhm... seems like the problem isn't bound to only Wine programs, it starts flickering when launching ATI Catalyst Control Center as well...

---

### Post by GhettoFish on 2011-01-20
BUMP again...

Google gives this at the first one.
Okay, I got the same problem as above.

Tried to add hey regedit key as well, no luck.

Below is the post I posted over at the Wine games boards. Perhaps you guys have any idea on what it might be?

[quote=martin]

Black screen flashes
by martin on Thursday January 20th 2011, 16:17
I don't think that this is a iRO specific error, but this is the first time I've had this problem. 

if I run :~$ wine RagnarokFree.exe it patches just fine and I click on "Start" it starts the game. 

I see the Logo splash and then it flashes black a couple of times. It enters the EULA that you have to agree on which is where everything stays black. If I hover the mouse over the buttons "Agree" or "Exit" the image and agreement flashes for real quick, so if I know where my mouse is I can get past this screen. The same happen in the login window and character creation. 

So, I can only see the game screen when i hover buttons, the rest of the time it is black. 

When I first hit enter to run the application my entire screen flashes, not only the windowed game. 

If i do :~$ wine Setup.exe it flashes a couple of times but when the setup window has loaded I can change all the settings I want. I have tried all combinations I could think of in this window. 

Here I thought that my problem might be with my gfx card or how wine or my computer handles OpenGL. So testet two applications. 

First was: lab.bachem-it.com/opengl/qtgears/ which runs fine, no flashes and I see the gears without a hitch. When i first run the program how ever my screen flashes a couple of times before it loads. 

Second was: freewebs.com/mannymax/cpp/GLtest.html which did just as fine as qtgears for windows. So, problem here shouldn't be OpenGL but something else. 

Some gfx info that might be of interest. 

:~$ lspci -vvv | grep "VGA compatible" 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller]) 

:~$ glxinfo | grep "OpenGL renderer" 
OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL DRI2 

:~$ glxinfo | grep "OpenGL version" 
OpenGL version string: 1.5 Mesa 7.9-devel 


Anyone have any idea on where my problem might lie?
[/quote]

---

### Post by GhettoFish on 2011-01-20
BUMP again...

Google gives this at the first one.
Okay, I got the same problem as above.

Tried to add hey regedit key as well, no luck.

Below is the post I posted over at the Wine games boards. Perhaps you guys have any idea on what it might be?

[quote=martin]

Black screen flashes
by martin on Thursday January 20th 2011, 16:17
I don't think that this is a iRO specific error, but this is the first time I've had this problem. 

if I run :~$ wine RagnarokFree.exe it patches just fine and I click on "Start" it starts the game. 

I see the Logo splash and then it flashes black a couple of times. It enters the EULA that you have to agree on which is where everything stays black. If I hover the mouse over the buttons "Agree" or "Exit" the image and agreement flashes for real quick, so if I know where my mouse is I can get past this screen. The same happen in the login window and character creation. 

So, I can only see the game screen when i hover buttons, the rest of the time it is black. 

When I first hit enter to run the application my entire screen flashes, not only the windowed game. 

If i do :~$ wine Setup.exe it flashes a couple of times but when the setup window has loaded I can change all the settings I want. I have tried all combinations I could think of in this window. 

Here I thought that my problem might be with my gfx card or how wine or my computer handles OpenGL. So testet two applications. 

First was: lab.bachem-it.com/opengl/qtgears/ which runs fine, no flashes and I see the gears without a hitch. When i first run the program how ever my screen flashes a couple of times before it loads. 

Second was: freewebs.com/mannymax/cpp/GLtest.html which did just as fine as qtgears for windows. So, problem here shouldn't be OpenGL but something else. 

Some gfx info that might be of interest. 

:~$ lspci -vvv | grep "VGA compatible" 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller]) 

:~$ glxinfo | grep "OpenGL renderer" 
OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL DRI2 

:~$ glxinfo | grep "OpenGL version" 
OpenGL version string: 1.5 Mesa 7.9-devel 


Anyone have any idea on where my problem might lie?
[/quote]

---

### Post by GhettoFish on 2011-01-20
Double post...

---

### Post by GhettoFish on 2011-01-20
BUMP again...

Google gives this at the first one.
Okay, I got the same problem as above.

Tried to add hey regedit key as well, no luck.

Below is the post I posted over at the Wine games boards. Perhaps you guys have any idea on what it might be?

[quote=martin]

Black screen flashes
by martin on Thursday January 20th 2011, 16:17
I don't think that this is a iRO specific error, but this is the first time I've had this problem. 

if I run :~$ wine RagnarokFree.exe it patches just fine and I click on "Start" it starts the game. 

I see the Logo splash and then it flashes black a couple of times. It enters the EULA that you have to agree on which is where everything stays black. If I hover the mouse over the buttons "Agree" or "Exit" the image and agreement flashes for real quick, so if I know where my mouse is I can get past this screen. The same happen in the login window and character creation. 

So, I can only see the game screen when i hover buttons, the rest of the time it is black. 

When I first hit enter to run the application my entire screen flashes, not only the windowed game. 

If i do :~$ wine Setup.exe it flashes a couple of times but when the setup window has loaded I can change all the settings I want. I have tried all combinations I could think of in this window. 

Here I thought that my problem might be with my gfx card or how wine or my computer handles OpenGL. So testet two applications. 

First was: lab.bachem-it.com/opengl/qtgears/ which runs fine, no flashes and I see the gears without a hitch. When i first run the program how ever my screen flashes a couple of times before it loads. 

Second was: freewebs.com/mannymax/cpp/GLtest.html which did just as fine as qtgears for windows. So, problem here shouldn't be OpenGL but something else. 

Some gfx info that might be of interest. 

:~$ lspci -vvv | grep "VGA compatible" 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller]) 

:~$ glxinfo | grep "OpenGL renderer" 
OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL DRI2 

:~$ glxinfo | grep "OpenGL version" 
OpenGL version string: 1.5 Mesa 7.9-devel 


Anyone have any idea on where my problem might lie?
[/quote]

---

