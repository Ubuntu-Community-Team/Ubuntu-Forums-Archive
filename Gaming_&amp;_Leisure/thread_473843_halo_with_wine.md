---
title: "halo with wine?"
date: 2007-06-14
forum: Gaming &amp; Leisure
---

### Post by kdarkentity on 2007-06-14
i have installed halo using wine but i cant get it to run

---

### Post by hikaricore on 2007-06-14
Have you read all the info here [http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720) ?

Also you might want to be more specific.

What kinda error output do you get when you run it from a terminal?
What kind of video card do you have, what drivers are installed, and is 3d acceleration working properly?

---

### Post by kdarkentity on 2007-06-15
here is the output from the terminal when i try running halo.exe with wine

err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

---

### Post by hikaricore on 2007-06-15
> **kdarkentity said:**
> 
err:module:import_dll Library **_ntoskrnl.exe_** (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

Now I'm not a wine dev so I may be wrong about this, but it appears that ntoskrnl.exe is [already part of WINE]("http://source.winehq.org/source/dlls/ntoskrnl.exe/") so you shouldn't need to get this file from anywhere.

By any chance when you installed wine did you run winecfg?

```

winecfg
```

And I havn't had time to look, did you find any mention of this error on the Halo WINEApp page?

---

### Post by kdarkentity on 2007-06-15
yes i have run winecfg multiple times and i have changed the settings multiple times

---

### Post by The Noble on 2007-06-15
What version are you running (of wine)? 0.9.39 just came out, andthe recent cvs gave some good reports for running halo; maybe this release will have the changes to make halo fully playable.

---

### Post by kdarkentity on 2007-06-15
im running 9.33 ...how do i update my current version?

---

### Post by hikaricore on 2007-06-15
Information on how to add the repository containing the latest version of WINE is located here:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

You can always download the most recent package here and install it without adding the repo:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

And you can download past releases here:
[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)


[B]Please keep in mind that for most users these builds are not needed, and they can keep using the version
in the Ubuntu repos.  These are the most bleeding edge versions of WINE you can get without compiling from
their SVN and may contain new bugs and regressions.  Though with certain games and applications, these versions
allow you to run games/applications which were not possible to run before their release.  Use common sense here folks.  ^_^[/B]

---

### Post by The Noble on 2007-06-16
I made the post on the .9.38 release (on appdb, just look) and I have to add some say to this: It works quite well the first level, but tweeks out on my ATI card. If you have an Nvidia card and my drivers happen to be causing the problem, you may actually come out with a 99% working game. I got online and even had the flashlight working ingame. Just make sure you disable shadows (they caused porblems for me) and get that extra .dll that appdb tells you to. And, please, if you get this working any better than I, tell the wine devs! It would be good to know that the fglrx drivers ar ethe problem.

---

### Post by lordhebe on 2007-06-16
WOW. I just got this running after several attempts and by golly it works incredibly well, I never would've expected a game like this to run a wine, not now anyway if not ever. I found by using these setting I could get the best play experience

I use these flags on the end of my desktop shortcut:  ```
-novideo -vidmode 1024,768,60 -use11
```

-novideo because with videos enabled, they would run, pretty well I might add, but after playing the Microsoft one it would lock up, disabling videos get the game straight to the main menu.

-vidmode sets the resolution the way I want it (changing it in game  crashes it)

-use11 tells it to use 1.1 shaders, i found that this provided the least graphical glitches for me, -use20, which forces it to use 2.0 shaders works as well, but when using them the gun flare doesnt show up, so all you see when you fire a gun is the rebound. -useff (fixed function card) causes severe graphical glitches and terrible performance, so avoid it like the plague.

my winecfg setting are standard, win 2k emulation, desktop:1024x768, ALSA driver, sound emulation.


There are only a few problems, enabling specular, shadows and decals cause major graphical glitches, and sound is a bit dodgy. I haven't yet upgraded to 0.9.39, so mabye these problems will be gone. I haven't tested multiplayer yet, but will do soon.  Now if you'll excuse I'm gonna whoop some covenant butt, finally on linux!

UPDATE: I took a few pictures of me playing:

---

### Post by kdarkentity on 2007-06-16
ok i went to winehq's website and i cannot figure out how to update to the newest version... can someone plz explain this to me

---

### Post by kdarkentity on 2007-06-16
Ok i have updated to version 9.38 with my updtae manager... now when i try to run halo.exe with the terminal i get this output

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

what am i missing now?

---

### Post by domat00 on 2007-06-16
[http://ubuntuforums.org/showthread.php?t=454814&highlight=Call+of+Duty]("http://ubuntuforums.org/showthread.php?t=454814&highlight=Call+of+Duty")

Perhaps a skip back to OSS drivers might become an alternative to ALSA?

---

### Post by lordhebe on 2007-06-16
> **kdarkentity said:**
> Ok i have updated to version 9.38 with my updtae manager... now when i try to run halo.exe with the terminal i get this output

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

what am i missing now?

Remember to apply a nocd crack, I had that problem, it just gives me that message in the terminal and then dies abruptly afterwards. Applying a no-cd crack made the game run, but read my earlier post on which aurguments to use.

---

### Post by kdarkentity on 2007-06-16
what do u mean by no cd crack?

---

### Post by Jockboy98295 on 2007-06-16
can i get some help?
I just installed wine 0.9.39 and tried to install halo
put in the key, and it says i need "PidGen.dll"
I found it on the cd but dont know if i need to install it or what, kinda new to wine and new to running around in the terminal on ubuntu.  I have run winecfg several times and changed the settings as well.  still no change.
what are your suggestions?
thanks

---

### Post by kdarkentity on 2007-06-16
hey man im still trying to get this to work myself... did u run the setup.exe on the cd?

---

### Post by Jockboy98295 on 2007-06-16
i did run setup.exe
i just found out that pidgen.dll will not run without mfc42.dll
i have downloaded it, but i dont know how to install it!!!
any suggestions?

---

### Post by lordhebe on 2007-06-17
> **kdarkentity said:**
> what do u mean by no cd crack?

I mean a cracked exe that remove copy protection, meaning it can be run without the disc. You can get them for many games at [http://www.megagames.com]("http://www.megagames.com") under PC fixes


> **Jockboy98295 said:**
> i did run setup.exe
i just found out that pidgen.dll will not run without mfc42.dll
i have downloaded it, but i dont know how to install it!!!
any suggestions?

copy it to your /.wine/drive_c/Windows/System32/ directory.

---

### Post by kdarkentity on 2007-06-17
ok now im running wine 9.39 

can you plz explain to me what i need from the pc game fixes for halo at megagames.com and what to do with them to make a cracked exe?

---

### Post by The Noble on 2007-06-19
To install the game, download mfc42.dll ( [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) ) and place it in your system32 folder. To find that folder, open up your home folder, press ctrl-H, and scroll down to .wine. Look in there and copy the downloaded file. This should allow you to install Halo (I would not use the express Install). 

Next, use the haloupdate.exe file in your /Program Files/Microsoft Games/Halo folder to update the game to the latest 1.07 version. To crack the exe, go to this page ( [http://www.gameburnworld.com/dl/dl.php?file=HaloCombatEvolvedv1.07NoCDFixedexeEng.rar](http://www.gameburnworld.com/dl/dl.php?file=HaloCombatEvolvedv1.07NoCDFixedexeEng.rar) ) and use one of the mirrors to download a zip file. Unzip it and copy the halo.exe in that folder into the Main halo folder. It should replace the original file.

If you have direct rendering, simply double-clicking the desktop icon for halo after the install should run the game.

And lordhebe, what wine version are you using? The main menu does not show up in .9.39 for me, so I wand to see if there is a regression or if it is just me.

---

### Post by lordhebe on 2007-06-19
I was using 0.9.38, but have since upgraded and seen no changes, for better or worse.

---

### Post by ketzerei on 2007-06-28
Hello. I am a fairly experienced ubuntu user who is having a bit of difficulty running halo on wine. I've looked on the winehq site and havent really found an answer to my problem. The thing is is that I cant run halo period. It boots with the splash but it doesn't go completely into fullscreen and my mouse gets grabbed and I cant kill the window and endup having to reboot. any ideas?

---

### Post by kdarkentity on 2007-06-28
yea thats pretty much my problem too but in my case i keep getting an error telling me that /shaders/vsh.bin is missing or corrupt... and it is neither missing or corrupt... sooo idk

---

### Post by The Noble on 2007-06-28
> **ketzerei said:**
> Hello. I am a fairly experienced ubuntu user who is having a bit of difficulty running halo on wine. I've looked on the winehq site and havent really found an answer to my problem. The thing is is that I cant run halo period. It boots with the splash but it doesn't go completely into fullscreen and my mouse gets grabbed and I cant kill the window and endup having to reboot. any ideas?

Weird. Try un-selecting ths "grab mouse pointer" option under the graphics tab. Otherwise, I don't really know what to tell you. Wine has some pretty big problems; this is especially true when it decides to lock up the system for no good reason. Could you not ctrl-alt-backspace? That should solve your problems and would not require the time for rebooting. Just make sure you are running the latest version of wine. If you are, try reverting  a version or two.

---

### Post by ketzerei on 2007-06-28
> **The Noble said:**
> Weird. Try un-selecting ths "grab mouse pointer" option under the graphics tab. 

Its unselected.

Also, ctl-alt-backspace never works when I run games on wine.

Edit: Im a little miffed that winehq said it worked flawlessly. I dont understand what they did to get it to work.

---

### Post by hikaricore on 2007-06-28
> **ketzerei said:**
> Im a little miffed that winehq said it worked flawlessly. I dont understand what they did to get it to work.

A [user]("http://ubuntuforums.org/member.php?u=251742") of this forum made that review stating specific hardware and settings were used.
I believe he even mentioned it in this very thread.

Even he was amazed to get it to work.

Halo has pretty much never worked well before so give it some time and have some patience, making sure to follow any setup instructions exactly.  You may also want to be sure your video driver and everything work correctly.

---

### Post by lordhebe on 2007-06-28
That would be me, and yes, I was suprised to get it working. I had been trying to get it working since I moved to linux, but there have been advances in wine since then.

And here is the post you were referring to (earlier on in the thread) :

> **lordhebe said:**
> WOW. I just got this running after several attempts and by golly it works incredibly well, I never would've expected a game like this to run a wine, not now anyway if not ever. I found by using these setting I could get the best play experience

I use these flags on the end of my desktop shortcut:  ```
-novideo -vidmode 1024,768,60 -use11
```

-novideo because with videos enabled, they would run, pretty well I might add, but after playing the Microsoft one it would lock up, disabling videos get the game straight to the main menu.

-vidmode sets the resolution the way I want it (changing it in game  crashes it)

-use11 tells it to use 1.1 shaders, i found that this provided the least graphical glitches for me, -use20, which forces it to use 2.0 shaders works as well, but when using them the gun flare doesnt show up, so all you see when you fire a gun is the rebound. -useff (fixed function card) causes severe graphical glitches and terrible performance, so avoid it like the plague.

my winecfg setting are standard, win 2k emulation, desktop:1024x768, ALSA driver, sound emulation.


There are only a few problems, enabling specular, shadows and decals cause major graphical glitches, and sound is a bit dodgy. I haven't yet upgraded to 0.9.39, so mabye these problems will be gone. I haven't tested multiplayer yet, but will do soon.  Now if you'll excuse I'm gonna whoop some covenant butt, finally on linux!

UPDATE: I took a few pictures of me playing:



PLUS: I would like to apologize if I have wrongly got people siked up about the game. I would like to point out that a gold rating is NOT flawless and just because I had a fairly smooth ride with running Halo on wine doesn't mean you will. I will write up a tutorial tonight as I reinstall the game (I have it working on crossover as well, so if I break my install I have a backup which I can refer to. There's not enough documentation about this.

---

### Post by GMU_DodgyHodgy on 2007-06-28
Lord Hebely - I look forward to your tutorial. 

As you mentioned I am quite suprised you got Halo running with Wine.  I have it at home (for my Windows partition).  it would be amazing to get it running on my linux box.

Cheers.

---

### Post by lordhebe on 2007-06-28
Okay I've written the tutorial. Here is the link: [http://ubuntuforums.org/showthread.php?t=486986](http://ubuntuforums.org/showthread.php?t=486986)

oh and it's lord**hebe** :D

---

### Post by GMU_DodgyHodgy on 2007-06-28
> **lordhebe said:**
> Okay I've written the tutorial. Here is the link: [http://ubuntuforums.org/showthread.php?t=486986](http://ubuntuforums.org/showthread.php?t=486986)

oh and it's lord**hebe** :D

Oh my goodness - Sorry Lord Hebe - I wrote that quickly during my lunch break.  My sincere apologies. 

I look forward to reviewing your tutorial.  

Running Halo would be sweet.

---

### Post by lordhebe on 2007-06-29
No worries. I really hopes it helps you all get it running, I know for a fact that this plan works because I uninstalled Halo, and went through the install process again, writing this guide as I went along, so the procedure worked for me and got it working to it's "Gold" status. I did testing just to make sure.

---

### Post by Doug52392 on 2007-07-02
I tried installing Halo, and it installed OK, but I cant play it. The installation worked, but when I tried running it with the downloaded Halo.exe program, the computer just freezes. When I restarted the computer and ran it again, I got a dialog that said the program didnt exit correctly and I should run Halo in safe mode. When I clicked safe mode, it still froze. Again i can see the computer at least switches the display resolution to load the game, but nothing comes up. I just see my desktop, which is bigger than normal because the display resolution at least changes. I have a Toshiba Satellite 1905 laptop with 16mb ATI Radeon Mobility M6 graphics card (I know 16mb is low, but the game worked fine in Windows despite the old graphics card) and 256mb RAM. I tried changing some settings using winecfg, and tried several other patches, but none work. Why wont it work for me?
_________________

---

### Post by mouseboyx on 2007-07-12
is there any way to get it working without the nocd crack? because it limits the servers to the ones with the same cdcrack as u?

---

### Post by hikaricore on 2007-07-12
> **mouseboyx said:**
> is there any way to get it working without the nocd crack? because it limits the servers to the ones with the same cdcrack as u?

Generally if it's not mentioned, it can't be done.

It might be possible but I'm very very doubtful.

---

