---
title: "World of Warcraft 1.11?"
date: 2006-06-20
forum: Gaming &amp; Leisure
---

### Post by Grog140 on 2006-06-20
Anyone else not being able to get past character selection after patch?

EDIT: PArtially fixed!

Thanks to JairunCaloth for posting:

> I read on the App DB over at wine HQ that the crash is being caused by the minimap. There is a mod [http://www.curse-gaming.com/en/wow/a...-autohide.html](http://www.curse-gaming.com/en/wow/a...-autohide.html) that will hide the mini-map when you go indors(which is what is apparently causing the bug, so if you logged out inside, you will crash on entrance). I'm going to install the mod and see if it helps me.

That worked for the problem it seems most peopleare having.

---

### Post by hawk684 on 2006-06-20
I'm able to get into the character selection with certain characters but only sometimes.   
> 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  469
  Current serial number in output stream:  469

Is the error message, the numbers are usually different though.  Running Wine 0.9.15

---

### Post by Grog140 on 2006-06-20
I have the exact same output.....

You know what I want? I want a native Linux Client for WoW....:rolleyes: 

](*,)  But it's not going to happen! ](*,)

---

### Post by hawk684 on 2006-06-20
They've at least got a client for Mac so it's a step in the right direction.  Blizzard's probably one of the best bet's to actually get major publisher games on Linux, them or Valve anyway.

---

### Post by JairunCaloth on 2006-06-20
I was able to log in just fine, but then the game crashed as I was walking into the blacksmith shop in Elwyin forrest. Wine gave me this error.

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  487
  Current serial number in output stream:  487

---

### Post by gi2k15 on 2006-06-20
[QUOTE=hawk684]They've at least got a client for Mac so it's a step in the right direction.  Blizzard's probably one of the best bet's to actually get major publisher games on Linux, them or Valve anyway.[/QUOTE]
Is there any game from Blizzard native on Linux?

---

### Post by jdmpike on 2006-06-20
I can't get past the "Connected" screen.

It just sits there for a few minutes then it disconnects me from the server... Not what I want!

I am currently running a patched version of wine 0.9.12 because I get the same GLX errors when I run the 0.9.15 and I get a VERY flaky screen redraw with 0.9.14...

Hope to see you all in game, I have grinding to do!

jdmpike

---

### Post by Grog140 on 2006-06-20
[QUOTE=JairunCaloth]I was able to log in just fine, but then the game crashed as I was walking into the blacksmith shop in Elwyin forrest. Wine gave me this error.

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  487
  Current serial number in output stream:  487[/QUOTE]

Yeah, I get:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  509
  Current serial number in output stream:  509

```

Not exactly the same but the same none the less.

---

### Post by jdmpike on 2006-06-20
[http://forums.worldofwarcraft.com/thread.aspx?fn=wow-customer-service&t=54375&p=1&tmp=1#post54375](http://forums.worldofwarcraft.com/thread.aspx?fn=wow-customer-service&t=54375&p=1&tmp=1#post54375)

That shows that Blizzard knows about the stuck at "connected" problem with Login on some servers...

As for the GLX errors. I was getting those until I switched back to a patched version of 0.9.12 - you can still get the source and build it from winehq - you might give that a shot.

jdmpike

---

### Post by lleonard on 2006-06-20
I'm having problems too, but I don't even get to the character selection screen.  

After the client authenticates it goes to a "Downloading" dialog box and the screen flickers with black areas sort of roll from top to bottom.  The mouse stops responding and I have to kill X with Ctrl+Alt+Backspace to get control back.  

Is anyone else experiencing this and does anyone have suggestions?

---

### Post by JairunCaloth on 2006-06-20
I read on the App DB over at wine HQ that the crash is being caused by the minimap. There is a mod [http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html](http://www.curse-gaming.com/en/wow/addons-4147-1-minimap-autohide.html) that will hide the mini-map when you go indors(which is what is apparently causing the bug, so if you logged out inside, you will crash on entrance). I'm going to install the mod and see if it helps me.

(edited with the correct URL)

*update*
By turning off the minimap I found that I can walk into buildings.
The minimap can be hidden manualy, so if your character isn't stuck inside an area then you just have to remember to close the minimap before you walk inside. However if you are stuck inside, this mod will disable the minimap from the start, and should allow you to log in.

To install the mod you just unzip and place the folder inside your "World of Warcraft/Interface/AddOns" folder. When you get to the character selection screen click the add-ons button in the bottom left corner. From there make sure you check the "Load out of date add-ons" box. Then volia load in like normal, and you should have no more crash. For more information about add-ons look here [http://www.curse-gaming.com/en/wow/article-2-1-addons.html](http://www.curse-gaming.com/en/wow/article-2-1-addons.html)

---

### Post by JairunCaloth on 2006-06-20
[QUOTE=lleonard]I'm having problems too, but I don't even get to the character selection screen.  

After the client authenticates it goes to a "Downloading" dialog box and the screen flickers with black areas sort of roll from top to bottom.  The mouse stops responding and I have to kill X with Ctrl+Alt+Backspace to get control back.  

Is anyone else experiencing this and does anyone have suggestions?[/QUOTE]

Have you tried to download and install the patch manualy? I usually just get my patches from [http://www.filefront.com](http://www.filefront.com). Typicly I get better download speeds then with the blizzard patcher. If you are current with your patches other than the newest one, just download the [World of Warcraft v1.10 to v1.11 patch]("http://files.filefront.com/World+of+Warcraft+v110+to+v111+Patch/;5169823;;/fileinfo.html") or you can download the [full patch]("http://files.filefront.com/World+of+Warcraft+v111+Full+Patch/;5169828;;/fileinfo.html") which will patch you from any version to the current one. 

To install a manual patch, unzip the patch into the world of warcraft folder and just type *wine nameofthepatch.exe* into the terminal in the WoW home directory.

---

### Post by Kageboushi on 2006-06-20
After installing the patch (which went flawlessly), I logged into the game, got the character select screen, chose my character, watched the loading bar fill up completely...

THEN BOOM, the whole game shuts down before the game starts showing.

Why does Blizzard hate Linux?

---

### Post by dancingtofu on 2006-06-20
I am not having any of the problems that you guys are discussing. 
I just followed the tutorial described here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
I used the prepatched binary build of wine 0.9.15 that is discussed in the tutorial.
I installed WoW by copying an already patched installation from another Windows PC into the wine directory.
I got all the necessary dlls and changes to Config.wtf done and it runs ok.
I have some problems, but its mainly the camera making the system choke a little, I think its because of my ATI card. I have heard ATI is not very good, even if you have a good card.
By the way, if this helps anyone, I am running a 2 GHz P4 with 512 MB RAM and my gfx is an ATI Radeon 9800 Pro with 128MB of memory.
All in all, my WoW installation is very playable with very few graphical problems, and nothing that makes it unplayable.
Oh, my performance improved noticably when I turned off all sound and music. I don't mind, since I rarely play where I can hear it anyway.

---

### Post by hawk684 on 2006-06-20
[QUOTE=JairunCaloth]To install the mod you just unzip and place the folder inside your "World of Warcraft/Interface/AddOns" folder. When you get to the character selection screen click the add-ons button in the bottom left corner. From there make sure you check the "Load out of date add-ons" box. Then volia load in like normal, and you should have no more crash. For more information about add-ons look here [http://www.curse-gaming.com/en/wow/article-2-1-addons.html](http://www.curse-gaming.com/en/wow/article-2-1-addons.html)[/QUOTE]

Wow (heh), what a weird bug, minimap in 1.11 makes Wine crash...that's just bizarre.  Working fine without the minimap though so I guess it's good...just strange though, wonder what bliz changed in the minimap.

---

### Post by DotBot on 2006-06-20
The game patched just dandily for me and now I can't so much as open the game. :(

---

### Post by simon50508861 on 2006-06-21
Well i can load the game fine, but i get a horrible flicker making the game unusable. Anyone know of a fix to this? or does this add-on fix that?

---

### Post by Roostey on 2006-06-21
I've got the same problems with the minimap - when it's open and i'm in a building/cave the game bombs out.  The suggested fix (the addon to automatically close the minimap) works to some extent, except when my character died - the game bombed out immediately then and I couldn't get back into the choose character screen because I suspect that rendering for death mode uses the same feature that crashes the minimap.

The only way I could get back in was to run in DirectX mode (upside down - yay!) then resurrected myself with the angel.

To stop this happening again, I turned off Death effect and Full screen glow effect in the video options menu and committed suicide.  The game didn't bomb out this time, so hopefully it'll be a little more stable now.

---

### Post by JairunCaloth on 2006-06-21
[QUOTE=Kageboushi]After installing the patch (which went flawlessly), I logged into the game, got the character select screen, chose my character, watched the loading bar fill up completely...

THEN BOOM, the whole game shuts down before the game starts showing.

Why does Blizzard hate Linux?[/QUOTE]

Did you logout inside a building? If so it sounds like the minimap bug.

---

### Post by GIBson3 on 2006-06-21
[QUOTE=hawk684]They've at least got a client for Mac so it's a step in the right direction.  Blizzard's probably one of the best bet's to actually get major publisher games on Linux, them or Valve anyway.[/QUOTE]

if I remember correctly there was a Linux client in the early days of Closed beta. It was horribly buggy and disappeared about the same time as the first "major" CB Patch, I wouldn't hold my breath for an elf binary any time soon. :mad:

---

### Post by saxin on 2006-06-21
[QUOTE=simon50508861]Well i can load the game fine, but i get a horrible flicker making the game unusable. Anyone know of a fix to this? or does this add-on fix that?[/QUOTE]
Yep, same thing happens to me also mate. Any suggestions?

---

### Post by Grog140 on 2006-06-21
The addon works for me.

---

### Post by Demoncrat on 2006-06-21
Well, i'll just post what makes it work for me.

I had the same problem with wine 0.9.14 (being the screen flickering).

I have downloaded the wine source for wine 0.9.15, which can be found [here]("http://prdownloads.sourceforge.net/wine/wine-0.9.15.tar.bz2").

Also download the [patch](http://rapidshare.de/files/20885790/wow.new.patch.0.9.13-1.html).

The instructions to get this compiled and installed can be found on [this](http://appdb.winehq.org/appview.php?versionId=4031) page.

Once you have a running wine, start winecfg in a terminal and make sure that "Enable desktop double buffering" under the Graphics tab is tagged.

Now you still have to resolve the minimap bug. Go to the [Curse Gaming website](http://www.curse-gaming.com/en/wow/download-13194.html curse-gaming), save and unpack the Minimap_Autohide.zip file in your interface/addons folder. Don't forget to activate the addon when starting WoW, because it will be marked as "out-of-date".

Now, if your character was logged out in one of the major cities, you'll have to find someone with a running WoW, log in with your account and move all your characters outside of the major city and log out again. If you character was inside the inn of let's say Menethil, don't worry, that won't be a problem.

I hope this post will help you out a bit, so you can enjoy WoW again.

PS: I have a nvidia card with latest drivers, but i didn't make any changes there.
PS2: don't open you minimap in a major city, or you'll be instant logged ;)

---

### Post by thecwin on 2006-06-21
For those suffering with the X_GLXMakeCurrent error(s), this seems to be nVidia specific...

It seems to be a bug in WINE but one that's brought out by the way the nVidia drivers are coded. I think it's a YMMV thing :/. The WoW patched WINE seems to fix some of it for me but not all of it, however it works fine with an ATI card.

---

### Post by simon50508861 on 2006-06-21
[QUOTE=saxin]Yep, same thing happens to me also mate. Any suggestions?[/QUOTE]


Well the fix for me was to turn of the minimap with the X and go outside, log and restart WoW. kind of annoying with no minimap functionality. It works outside, so you have to either log in one of the major cities or log outside the inn. Luckily it was useable enough to guide my toon outside and logout.

I couldn't get the plugin to work as it wouldnt even show as a plugin, out of date or otherwise. what title does it go under? Does the directory under the addons folder have to have a particular name?

---

### Post by FuzzBarber on 2006-06-22
Crashes on startup with both wine 0.9.15 and 0.9.12 with aforementioned GLX errors. Latest nvidia drivers.

---

### Post by Sin-D on 2006-06-22
Same problems, same GLX errors, latest Nvidia drivers can't get the game to boot.

I can boot with D3d but, as you know can't play in d3d.

---

### Post by thecwin on 2006-06-22
Finally got it working:
I used a WoW patched WINE 0.9.14 and the minimap hiding plugin. I disabled all shader effects (so that 3d stuff would appear) and disabled Vsync (which for some reason fixed the flickering).

---

### Post by zachtib on 2006-06-22
```
zach@notapowerbook:~$ cd /opt/drive_c/Program\ Files/World\ of\ Warcraft/
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ gedit WTF/
Account/     Config.wtf   Config.wtf~
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ gedit WTF/Config.wtf
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7bf80000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bf80000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbceeec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fbc8c24,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fbc7804,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ glxinfo | grep rendering
direct rendering: Yes
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ glxgears 3080 frames in 5.0 seconds = 615.877 FPS
2478 frames in 5.0 seconds = 495.567 FPS
2493 frames in 5.0 seconds = 498.149 FPS
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ sudo gedit /etc/X11/xorg.conf
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$
```

ugh, it worked, then it didn't, what am i doing wrong?

---

### Post by Sin-D on 2006-06-22
[QUOTE=thecwin]Finally got it working:
I used a WoW patched WINE 0.9.14 and the minimap hiding plugin. I disabled all shader effects (so that 3d stuff would appear) and disabled Vsync (which for some reason fixed the flickering).[/QUOTE]

Thanks! disabling the shaders did work!

---

### Post by sgtBiafra on 2006-06-22
So, just to clarify, the following have resolved most people's problems for these issues:

**X_GLXMakeCurrent error(s)** - disable shader effects (enter in d3d mode or alter Config.wtf)

**screen flicker** - disable vsync (enter in d3d mode or alter Config.wtf)

**crash to desktop** - disable minimap (enter in d3d mode or use Minimap Autohide or similar Interface plug-in)

Is anyone suffering a different dilemma and have more to add?

---

### Post by lleonard on 2006-06-22
"Different dilemma"

I got the crash-to-desktop problem fixed using the minimap fix, but now a new issue has emerged.

After authenticating and logging in, as soon as the game goes to display the UI, the update downloader launches and the display switches back to the desktop with a small, ~2.5cm x 2.5cm square a corner of the game window is visible. It can be maxed/moved to fix the problem, so it is more of an annoyance than a bug.

Is this behavior being caused by the bnet background loader or something else?

---

### Post by zachtib on 2006-06-22
[QUOTE=sgtBiafra]Is anyone suffering a different dilemma and have more to add?[/QUOTE]
Mine wouldn't even start in opengl mode, im trying a fresh install to see if it helps.

and has anyone tried using wine 0.9.16? I'm about to try 0.9.16 unpatched, cause i hear it works

---

### Post by sgtBiafra on 2006-06-22
lleonard, you can disable the background downloader which should stop it from popping up. You can run it separately with WINE and then go to the File->Preferences(?) menu option and turn off Background Downloading.

That may or may not also fix your problem where WoW drops to a small square on your screen as well. I've encountered that when the downloader opens and I've had other windows open to Alt-Tab into and out of which usually seems to do the trick.

I just tried it now with the downloader disabled and the game opened as expected (no square).

----

zachtib, please let us know if 9.16 works. I haven't had the courage to try it as I just got WoW working again on 9.15.

---

### Post by zachtib on 2006-06-22
[QUOTE=sgtBiafra]zachtib, please let us know if 9.16 works. I haven't had the courage to try it as I just got WoW working again on 9.15.[/QUOTE]

so far its a no-go, but i cant even get it to work with the patched 9.15

---

### Post by DotBot on 2006-06-22
I'm (still) getting the MakeCurrent error with the latest Nvidia drivers.  Game crashes on startup in OpenGL mode.  Nothing fixes it (WINE reinstalls, WoW reinstalls, WoW Windows working copies...).

Cedega seems to be going fine, according to the forums.  I've been thinking of purchasing a subscription, but $5 a month will end up costing more than Windows XP (which I own) too soon for me.  :( I hate updates.

---

### Post by JairunCaloth on 2006-06-23
Just a few things I've run accross that may help some folks. The background downloader causes me all kinds of problems, once I disabled it alot of my problems went away. I've run WoW in cedega and wine, and for some reason I always get better performance out of wine with WoW. I'm sure others may have different results, but for some reason with wine I have almost no problems. Cedega, it runs slow, and is very buggy for me.

---

### Post by 0okie on 2006-06-24
Anyone else having problems with the patch NOT installing after you've downloaded it and gone through the terminal? Warcraft keeps acting like it's the first boot and showing the cinematics, then redownloading the patch 1.11 and telling me to restart. I tried going into terminal and having wine install it.. it works and never tells me it's done, it just stops.. So I try running WOW again and get thrown into the same process.

---

### Post by KRavEN on 2006-06-25
Okay, so i've done a lot of work on my box to get everything working.

The problems with 0.9.15 and 0.9.16 should ONLY effect Nvidia users.  

There have been some reports of the "flickering" issue with 1.11, but that is only with ATI and can be resolved by turning going into WTF/Config.wtf and change SET pixelShaders "1" to SET pixelShaders "0"

There are 2 problems with Nvidia.

1.  It crashes if you do a fresh install and the movie starts.
Fix:  Set go into WTF/Config.wtf and add: SET movie "0" 

2. Crashes on start or when entering indoor areas.
Fix:  Install the addon that autohides the minimap 

Other fix is to get the 0.9.10 source and patch, compile it, and use it.  The Nvidia bug is not present in 0.9.10

If you are having problems patching look in your home directory for a folder called wine-patch.  It probably has your patch files in it.  Move it to your wine folder and kick off BNUpdate.exe manually.

---

### Post by glaze on 2006-06-30
There is a new patch available for Wine 0.9.16 that should fix flickering and crashing. I'm compiling Wine with that patch to see if it works for me.

---

### Post by JairunCaloth on 2006-07-01
[QUOTE=zachtib]```
zach@notapowerbook:~$ cd /opt/drive_c/Program\ Files/World\ of\ Warcraft/
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ gedit WTF/
Account/     Config.wtf   Config.wtf~
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ gedit WTF/Config.wtf
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7bf80000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bf80000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbceeec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fbc8c24,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fbc7804,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ glxinfo | grep rendering
direct rendering: Yes
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ glxgears 3080 frames in 5.0 seconds = 615.877 FPS
2478 frames in 5.0 seconds = 495.567 FPS
2493 frames in 5.0 seconds = 498.149 FPS
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$ sudo gedit /etc/X11/xorg.conf
zach@notapowerbook:/opt/drive_c/Program Files/World of Warcraft$
```

ugh, it worked, then it didn't, what am i doing wrong?[/QUOTE]


Are you running the game in OpenGL mode? try wine wow.exe -opengl

---

### Post by Will May on 2006-07-03
I've recently installed Ubuntu and am trying to install Wine (with the patch to get WoW working). Unfortunately, everytime I try and download the patch from RapidShare, I end up with this message:

> 
Download-session invalid. Please click here.

Possible reasons:

    * Download-session expired. Direct-links last a few minutes for free users and a few days for premium-users.
    * You requested this download-session from a different IP than yours. If you use AOL, try a different browser.


Anyone know of a way around this/willing to email me the patch?

For those interested, I'm not using AOL, I'm with BT Broadband

---

### Post by babisnet on 2006-07-05
I have also bizzare prob i cant click anything!! :confused:  
ANyone knows any solvation ?
For ex: Am trying to click at an NPC vendor and no Cursur appears so i can buy soemthing

Ps:Am using wine not Cedega or P2P

---

