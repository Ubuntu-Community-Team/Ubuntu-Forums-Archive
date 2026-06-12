---
title: "HOWTO: WoW under 6.06 with Wine - NVIDIA/ATI"
date: 2006-08-24
forum: Gaming &amp; Leisure
---

### Post by tokyovigilante on 2006-08-24
People on these boards seem to be struggling a lot with WoW, so I thought I'd turn my experiences running it into a wee Howto. These steps worked for me, I've tried to generalise them as much as possible.

It's broken down into 4 steps: Sorting out your system, installing Wine, and installing then configuring WoW. I'm assuming you know what hardware you have, that you can install Ubuntu/Kubuntu, and can drive the terminal, at least to the extent of copying and pasting commands. If not, seek guidance elsewhere, and return when you are ready, grasshopper. ;) On with the show!

---

### Post by tokyovigilante on 2006-08-24
**A. Sorting out your system.**

1. Obviously the first thing is a clean install of K/Ubuntu 6.06.1 LTS, fully patched, on a system that exceeds the minimum requirements for WoW, ie video card with Hardware Transform and Lighting and 32MB VRAM, anything recent from Nvidia or ATI should do the trick. Intel integrated may struggle a bit with performance. A fast processor, lots of RAM and 5+ gigs of hard drive space are also desirable.

Its important to note Wine only runs on i386 and amd64 kernels, sorry ppc guys, you're stuck running under MacOS.

2. Does sound work? If not seek help elsewhere, I don't know enough to debug all possible sound issues. One note I will make from my own experience is that WoW needs to run in OSS compatibility mode. We'll go more into this later, but for now, if you are running KDE (Kubuntu), open sound in the System Settings, and set the timeout at the bottom to 1 (one) second. This releases the sound card when KDE is not using it, and allows sound in WoW.

I don't know what the situation is in Gnome, as it uses a different sound server. If anyone wants to fill me in, please do. No-one seems to have had too much trouble under Gnome with sound anyway.

3. Does video work? type
```
glxgears
``` at the terminal. If you get some nice 3d spinning gears, hurray. If not, then you need to install and configure the proprietary drivers appropriate for your architecture. I suggest the easiest way is to use the repositories. Heres a [good guide for ATI users]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") and [here for NVIDIA]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). If the binary NVIDIA drivers don't work for you, try tseliot's [envy script]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html").

4. Once you have sound and video, proceed on to installing Wine.

---

### Post by tokyovigilante on 2006-08-24
**B. Installing Wine.**
 
 Latest Version = 0.9.22. The patched .deb in the torrent is patched for NVIDIA and ATI, but untested for ATI as I don't have the hardware, so let me know!

WoW will not work with anything under 0.9.16-18 or so, and it is best to install the latest version for all the bugfixes and performance goodness.

 The method depends on whether you are using 32 or 64 bit.

 **32 bit NVIDIA and ATI users:**
 Download and force-install the patched version:
[http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb](http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb)
```

sudo dpkg -i --force-architecture wine_0.9.22-1_amd64.deb
sudo apt-get -f install
winecfg
``` [B]

64 bit NVIDIA and ATI users:[/B]
 Download and install the patched version:
[http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb](http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb)[]("http://www.demonoid.com/files/details/490360/999695/")
```

sudo dpkg -i  wine_0.9.22-1_amd64.deb
sudo apt-get -f install
winecfg
``` [B]

If the mirror is down, here's the torrent: [/B][http://www.demonoid.com/files/details/490360/999695/](http://www.demonoid.com/files/details/490360/999695/)
[B]
Finally...[/B]
 If winecfg pops up, hurray! Check you have version 0.9.20/21 installed. Change the sound output system to OSS, map /media/cdrom to D: and proceed to part C. If not, check back to see you haven't missed anything, and repeat the above steps. If still nothing, post SPECIFIC info about your system, steps taken, output of ```
glxinfo | grep direct
```, and ```
cat /etc/X11/xorg.conf
```I'd like to hear any torrent problems/feedback you have as well (other than it's slow, I know ;) - it's my first one.

Thanks very much pablasso for hosting the build.

---

### Post by tokyovigilante on 2006-08-24
[B]Part C

(If WoW is already installed in Windows, copy the WoW directory to somewhere in your home directory and go to part D. If you later have problems running or configuring WoW, delete the WTF, WDB and Interface directories from your copied install.)

[/B]Insert your WoW CD/DVD. Some people have had issues installing from CD when changing discs, if you do try copying the disc contents to your hard drive. If you are copying to the hard drive, put all the Installer Tome.mpqs in the same directory as Installer.exe and run from there.
  
  Otherwise - 
  ```
wine /media/cdrom/Installer.exe
``` 
  The installer will (should) pop up. The buttons will most likely be blank. Just click the big one, and it will carry on. The licence agreement may also be blank, again just carry on. If you are asked to install the Mozilla control, say yes and Wine will download and carry on. Installing to the "c" drive actually puts it in your /home/user/.wine directory. I prefer to stick it under /home/me/Games/WoW.
  
  Once the install has completed, go to part D.

---

### Post by tokyovigilante on 2006-08-24
[B]D. Configuring and running WoW.
[/B]Assuming you have changed the sound option in winecfg to OSS, we'll set WoW up to use this. Change to the directory you installed WoW in:
   ```
cd /home/<wow directory>
   cd WTF
   nano Config.wtf
``` Add these lines to the bottom:
   ```
SET SoundOutputSystem "1"
   SET SoundBufferSize "50" 
``` (everyone says 100ms for the buffer but I think thats too noticeably laggy, 50 seems fine to avoid the crackling and other bugs)
   Ctrl-X and Y to save.
   
   Now, for the moment you've all been waiting for:
   ```
cd ..
   wine WoW.exe -opengl
``` 

I suggest disabling full-screen glow effects, this can double your framerate, and I certainly can't tell the difference.

(If you have an ATI card, -d3d instead of -opengl may give you better results, but bear in mind Wine's Direct3D support is less well implemented than OpenGL at the moment, so try -opengl first)

The patching system should function as well under Wine as on Windows. Again, you may be prompted to install the Mozilla control, say yes to allow you to read the patch notes.

   Now take the battle to the cowardly Alliance! (You're all proud members of the Horde right? ;))
   
   If you have errors at any stage, read them carefully, and try to work out whether they're about sound, video, configuration etc, then take all practical steps to solve the issue. I'm happy to answer any queries and help with problems, but I've got limited time with school, and I'd like to think you'd done everything you could first. 

If you do need to ask for help, feel free, but PLEASE post all relevant information, ie hardware type, software versions (Ubuntu, Wine and drivers), and SPECIFICS about the errors. I'm far more likely to be able to help you easily that way.

Remember that your performance is highly unlikely to be as good as in Windows, even with optimal hardware and configuration. Having said that, I get 40-60fps with everything on, so good results are possible.
   
   Also, my experience is primarily with 64 bit and NVIDIA hardware, so I'm more likely to know whats going on if thats you too. Anyway, good luck, and happy questing!

---

### Post by autrui on 2006-08-25
still working on this, but in ten minutes i'm already three times as far along as i was the last time u and i communicated!!  it's installing, whcih if i remember from my last windows install, will take forever.  plenty of time to post my appreciation!  

thanks so much!!

(can't wait to get to the update patches! ;))

autrui

(for the horde!!)

---

### Post by tokyovigilante on 2006-08-25
> **autrui said:**
> still working on this, but in ten minutes i'm already three times as far along as i was the last time u and i communicated!!  it's installing, whcih if i remember from my last windows install, will take forever.  plenty of time to post my appreciation!  

thanks so much!!

(can't wait to get to the update patches! ;))

autrui

(for the horde!!)


Stunning, don't forget if you still have that Windows install, you can just copy over the World Of Warcraft folder to your home directory, will be heaps quicker, and you won't have to patch.

---

### Post by autrui on 2006-08-25
> **tokyovigilante said:**
> Stunning, don't forget if you still have that Windows install, you can just copy over the World Of Warcraft folder to your home directory, will be heaps quicker, and you won't have to patch.

hopefully i didn't speak to soon.  i had not yet changed discs, and when i did, things didn't swim.  copied all the cds to HD, now it's asking to insert disc 2.. how do i tell it to go to my disc2 folder instead?

::edit:: just put all the Installer Tomes from discs 2-5 into the disc 1 folder.

(and yeah, i wiped windows off my OS drive like a day after i started running ubuntu.  and my girlfriend says i fear commitment!)

thanks,

autrui

---

### Post by tokyovigilante on 2006-08-25
I added a wee bit to the guide about mapping your /media/cdrom to drive D: in winecfg, try that and see how you go. If you are copying to the hard drive, put all the Installer Tome.mpqs in the same directory as Installer.exe and run from there. 

I highly recommend to everyone who plays WoW to go and put down a couple of bucks on the trial DVD, it's basically the full WoW client on a single disc, and will install into Linux under Wine with a minimum of fuss.

---

### Post by MakLeod on 2006-08-25
Very nice guide thank you!  So far I am at step 4 installing WoW, but it seems to have slowed to a standstill on disc 3.  The drive isn't being accessed at all.  This happened to me when I installed Starcraft last night...but eventually it finished installing but took FOREVER =)  Any ideas as to why it hit a brick wall?

---

### Post by MakLeod on 2006-08-25
Argh!  Nevermind.  The "please insert disc 4" window was hidden behind the installation progress window =(

---

### Post by MakLeod on 2006-08-25
Sorry to post so many times, but WOW!  Thank you so much, WoW is up and running almost perfectly (couple of sound glitches here and there).  Great job!

---

### Post by tokyovigilante on 2006-08-25
Good stuff. If you have sound issues, try increasing the sound buffer to 100ms.

---

### Post by autrui on 2006-08-25
i wish i was having your success.  

i have WoW running; i log in, select char, and enter world.  then, lovely blue bar.  it fills and fills and then is full.  then it sits there, and after a while (about the same amount of time as it took to fill), BOOM: "disconnected from server."  i tried 3 servers--even made an alliance toon!  always with the disconnect.

i didnt mention the lag.  serious sound and video lag--maybe 1 fps?  under ten.  SLOW.  i listen to a lot of experimental music, so i'm down with the sound problems--i kinda like it better like this--but the video is an issue.  (it's my feeling that the lag is related to the disconnect, but lord knows.. i wanted to try dropping my resolution and going into window mode, but i couldnt get into the game to try it.)

i am not confident that my video card is set up properly, but i am confident that my sound card is, and both those are lagging, so i attribute this elsewhere.  (i *think* my VC is set up right, but im not confident in it.)

watching the mouse move across the screen like theres a really slow strobe light at its own little party has left me writing like english isn't my first language.  it is, but im stupified.  (there's proof--that's a complex word usage.)

i've read up on the commonness of the fps problem with wine/WoW, but i haven't seen anyone mention the disconnect.

  ](*,) 

first time i've used that smiley.  and i have a feeling it won't be my last.  it's a good thing my hatred of m$ is so rich and longstanding.

and yet, now i go to my windows laptop to slaughter me some shadowmaw panthers.

autrui

ps: don't let my temporary frustration leave you with an impression of ungratefulness.  (ungratitude?  me = FRIED.)  this is, in its way, a gold-plated problem.  at least it's running. :)

---

### Post by tokyovigilante on 2006-08-25
Hmm, well progress at least. Certainly seems like a video card issue. Try 

glxinfo | grep rendering

Should say direct rendering: Yes. Then try 

glxgears --printfps and post the results.
Are you running WoW with the -opengl switch?

---

### Post by autrui on 2006-08-25
> **tokyovigilante said:**
> Hmm, well progress at least. Certainly seems like a video card issue. Try 

glxinfo | grep rendering

Should say direct rendering: Yes. Then try 

glxgears --printfps and post the results.
Are you running WoW with the -opengl switch?

thanks for the quick reply.  did a little real-job work, and i'm feeling much better. :)  
```

autrui@compy:~$ glxinfo | grep rendering
direct rendering: No
autrui@compy:~$ glxgears --printfps
Warrning: unknown parameter: --printfps
X connection to :0.0 broken (explicit kill or server shutdown).
autrui@compy:~$

```

when i saw the "unknown parameter" bit, i let it roll for a little while, and then killed it. (while they were running, btw, they started getting jerky.)

how do i change to direct rendering?  how do i make the gears work?

oh, and, yes: wine WoW.exe -opengl

autrui

ps: it looks like wine 0.9.20 is up.

---

### Post by tokyovigilante on 2006-08-25
Ah. You're not currently running 3D hardware acceleration. 1fps makes a little more sense ;).

Your ATI drivers aren't set up properly. Did you follow the instructions in the howto I linked? If you did, did you restart the X-server to load the drivers (Ctrl-Alt-BkSp)?

Yeah I did see 0.9.20, but binaries haven't been built. Compiling it from source is a bit of a stretch for me ;)

Sorry just noticed that there should only be a single hyphen before printfps, ie glxgears -printfps

---

### Post by autrui on 2006-08-25
> **tokyovigilante said:**
> Ah. You're not currently running 3D hardware acceleration. 1fps makes a little more sense ;).

Your ATI drivers aren't set up properly. Did you follow the instructions in the howto I linked? If you did, did you restart the X-server to load the drivers (Ctrl-Alt-BkSp)?

Yeah I did see 0.9.20, but binaries haven't been built. Compiling it from source is a bit of a stretch for me ;)

Sorry just noticed that there should only be a single hyphen before printfps, ie glxgears -printfps

i hadn't used that particular guide before, but i did now, and things are about the same:
```

autrui@compy:~$ glxinfo | grep rendering
direct rendering: No
autrui@compy:~$ glxgears -printfps
880 frames in 6.1 seconds = 145.382 FPS
570 frames in 6.0 seconds = 94.398 FPS
570 frames in 5.8 seconds = 97.652 FPS
570 frames in 6.0 seconds = 94.621 FPS
570 frames in 5.9 seconds = 96.085 FPS
570 frames in 6.1 seconds = 94.093 FPS
X connection to :1.0 broken (explicit kill or server shutdown).

```
(that's where my fps was at before i restarted x-server.)

this also concerns me:
```

autrui@compy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
wth is mesa?  could that be my onboard card?  the trick to getting my sound card to work was disabling the onboard sound card.  could a similar thing be going on here?

thanks,

autrui

---

### Post by tokyovigilante on 2006-08-25
That just confirms my suspicion that your drivers aren't set up. In the absence of the ATI accelerated drivers, your system is using the unaccelerated community drivers written by the Mesa group. These do not use hardware acceleration, instead having to software render 3D, which is really slow. 

Do you have onboard video as well as your X1300 Pro? I thought from the lspci (LiSt PCI devices)  you posted that you didn't have onboard video. Seeing as you are running fglrxinfo, the ATI drivers are installed, but indirect rendering means they are not being used. Try running

sudo dpkg-reconfigure xserver-xorg

and selecting fglrx when it asks for your video driver. Leave everything else the same, then restart your X-server by pressing Ctrl-Alt-Backspace when the wizard completes.

Basically WoW and Wine are set up and working, and as soon as you get your system to use the ATI accelerated drivers, you'll be away.

---

### Post by autrui on 2006-08-25
> **tokyovigilante said:**
> 

sudo dpkg-reconfigure xserver-xorg

and selecting fglrx when it asks for your video driver. Leave everything else the same, then restart your X-server by pressing Ctrl-Alt-Backspace when the wizard completes.


i actually just did that, before my last post... i dont know if i have an onboard or not, i've always used cards.  does it help/make any difference that in my device manager it's listed twice?  it's got the correct vendor (ati inc.), but "Device: unknown (0x7142)" and in the other entry "Device: unknown (0x7162)."

ok, the sun is up.  maybe the tooth fairy will make this thing work while i'm sleeping!

autrui

---

### Post by tokyovigilante on 2006-08-25
> **autrui said:**
> i actually just did that, before my last post... i dont know if i have an onboard or not, i've always used cards.  does it help/make any difference that in my device manager it's listed twice?  it's got the correct vendor (ati inc.), but "Device: unknown (0x7142)" and in the other entry "Device: unknown (0x7162)."

ok, the sun is up.  maybe the tooth fairy will make this thing work while i'm sleeping!

autrui
Hmm, shouldn't be, as long as you only have one card plugged in. 

I'm pretty much out of ideas sorry, I havent had too much experience with ATI cards, as I've always run NVIDIA cause of the better driver support. 

I know for a fact that your video acceleration (or lack of) is to blame. Somehow you need to get the ATI drivers working. I should apologise, i've just found [this great guide ]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")with a quick google. Sorry, I shouldve put it in before. Hopefully one of the methods gets you going.

---

### Post by autrui on 2006-08-25
that guide you just linked worked like a charm!  i used method 2 (after method 1 produced the same results i've gotten for days).

```

autrui@compy:~$ glxinfo | grep rendering
direct rendering: Yes
autrui@compy:~$ glxgears -printfps
622 frames in 5.0 seconds = 124.304 FPS
625 frames in 5.0 seconds = 124.994 FPS
625 frames in 5.0 seconds = 124.992 FPS
625 frames in 5.0 seconds = 124.992 FPS
autrui@compy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

just went into WoW, and it got jerky when i left the inn; it crashed when i tried to adjust video settings, but i can deal with that later.

finally, my graphics are working correctly!  thank you thank you thank you!

autrui

---

### Post by tokyovigilante on 2006-08-25
> **autrui said:**
> that guide you just linked worked like a charm!  i used method 2 (after method 1 produced the same results i've gotten for days).

```

autrui@compy:~$ glxinfo | grep rendering
direct rendering: Yes
autrui@compy:~$ glxgears -printfps
622 frames in 5.0 seconds = 124.304 FPS
625 frames in 5.0 seconds = 124.994 FPS
625 frames in 5.0 seconds = 124.992 FPS
625 frames in 5.0 seconds = 124.992 FPS
autrui@compy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

``` 
just went into WoW, and it got jerky when i left the inn; it crashed when i tried to adjust video settings, but i can deal with that later.

finally, my graphics are working correctly!  thank you thank you thank you!

autrui

Hurray! Pleased to hear. Not to rain on your parade, even though you have everything set up now, that is a shockingly low glxgears FPS (my 7800GT gets 12000+). Try running WoW with the -d3d option rather than -opengl and see if that makes a difference.

Theres really no way around the fact that ATI has poor Linux support, other than making your next card an nVidia. Oh well, at least you're running! There are a number of threads on optimising ATI drivers, have a quick google.

---

### Post by AJLChase on 2006-08-25
When I log into wow its really laggy sound and video...almost sounds like the sound is skipping..then when I go to move WoW automotically shuts off with no warning. The one question I have is this. You say to type in this 
cd ..
   wine WoW.exe -opengl

To run WoW. I've been going to my wow folder manually and clicking on the exe. is this incorrect? And When I put wine wow.exe -opengl into a terminal i get this.

wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found

What exactly am I doing wrong? Thanks for reading!

---

### Post by tokyovigilante on 2006-08-25
> **AJLChase said:**
> When I log into wow its really laggy sound and video...almost sounds like the sound is skipping..then when I go to move WoW automotically shuts off with no warning. 

Well, its hard to know what's wrong given you haven't posted any of the system information i requested in the howto, but I suspect your video and/or sound aren't set up. Also, not running in -opengl mode may do that.
> **AJLChase said:**
> 
The one question I have is this. You say to type in this 
cd ..
   wine WoW.exe -opengl

To run WoW. I've been going to my wow folder manually and clicking on the exe. is this incorrect? And When I put wine wow.exe -opengl into a terminal i get this.

wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found

What exactly am I doing wrong? Thanks for reading!
You need to change (cd) to the directory WoW is installed in, or else put that directory in when you are running WoW, ie ```
wine /home/<username>/World\ Of\ Warcraft/WoW.exe -opengl
```. Wine is complaining cause you haven't given it a path to WoW, and can't find it in the default location it searches, ie system32.

BTW, in the terminal, if file names or paths have spaces, you need to put in a backslash to indicate to the terminal that the name continues after the space.

---

### Post by AJLChase on 2006-08-25
I'm an idiot. This is how my .wine and wow folder are set up.

name/.wine/drive_c/program files/world of warcraft



so how would i put the opengl command into a termin the right why? I'm trying all these different paths but I must be that much an idiot to get this right...sorry.

---

### Post by tokyovigilante on 2006-08-25
> **AJLChase said:**
> I'm an idiot. This is how my .wine and wow folder are set up.

name/.wine/drive_c/program files/world of warcraft



so how would i put the opengl command into a termin the right why? I'm trying all these different paths but I must be that much an idiot to get this right...sorry.

Its no problem. For the above command:

wine /home/<name>/.wine/drive_c/program\ files/world\ of\ warcraft\WoW.exe -opengl

should get you going. Two things: Linux has a case-sensitive file system, so program files and Program Files would be different folders, and pressing Tab after the first couple of letters in a path will complete the file path, so Wo <TAB> will put World\ Of\ Warcraft in for you.

---

### Post by AJLChase on 2006-08-25
Yeah, its not working. keeps saying directory not found. I am gonna give this a rest, ive tried so many methods in the past few days that I really don't care anymore lol. Time to take a break.

---

### Post by jyank on 2006-08-26
Thanks! Got it working right away, first try.

Only thing I've noticed is my FPS has taken a hit from what it was on windows, but I guess that's to be expected or that I need to reconfigure some stuff wine. (or I have the settings to high from windows, just copied the folder)

Using a 7600GT and in windows I average around 70FPS, loading it now I get about 25 which is playable, so for that I'm greatful.

Now to get ventrillo installed via wine and i'm ready for raiding tomorrow night :)

edit: also, is there anyway to get BMP to play in the background while playing? Get a weird error when trying to listen to music

edit2: nevermind, just disabled the sound in wine, I never have it on anyways :)

---

### Post by nhimf on 2006-08-26
WoW is running on my system but the fps sucks deeply. Prolly its the ATI drivers that makes the performance so bad.

Your howto seems to be fine (although i used some other). The patched .19 works fine, for as the unpatched .19 and .20 wont load opengl mode and hangs.
if i start wow with the -D3D parameter my textures are scrambled outside any building but are fine within buildings (like AH and Bank in OG), even with the patched .19 one.

My specs:
AMD x2 3800+
ATI radeon x1900xt
2GB RAM (low latency corsair)

With glxgears i get the following:
14827 frames in 5.0 seconds = 2960.838 FPS
13950 frames in 5.0 seconds = 2789.955 FPS
13896 frames in 5.0 seconds = 2778.911 FPS
11658 frames in 5.0 seconds = 2331.540 FPS
9699 frames in 5.0 seconds = 1938.410 FPS
16857 frames in 5.0 seconds = 3371.393 FPS
10005 frames in 5.0 seconds = 1999.342 FPS
13917 frames in 5.0 seconds = 2783.358 FPS
10753 frames in 5.0 seconds = 2150.537 FPS
10431 frames in 5.0 seconds = 2086.192 FPS

Can anybody confirm that these are normal readings?

WoW @ windows gives me 60 fps for i have vsync on. Cause of my dual core i wont get more than 64fps anyway cause of the dual core bug.
WoW @ linux gives me like 5-10fps in OG in opengl mode and about 15fps in direct3d mode.

Anybody can tell me if i ever will get normal performance with my ATI card?
Still using windows for WoW and i really hate the constant OS switching.

---

### Post by tokyovigilante on 2006-08-26
[FONT=Verdana][SIZE=2]> **nhimf said:**
> WoW is running on my system but the fps sucks deeply. Prolly its the ATI drivers that makes the performance so bad.

Your howto seems to be fine (although i used some other). The patched .19 works fine, for as the unpatched .19 and .20 wont load opengl mode and hangs.
if i start wow with the -D3D parameter my textures are scrambled outside any building but are fine within buildings (like AH and Bank in OG), even with the patched .19 one.

My specs:
AMD x2 3800+
ATI radeon x1900xt
2GB RAM (low latency corsair)

With glxgears i get the following:
14827 frames in 5.0 seconds = 2960.838 FPS
13950 frames in 5.0 seconds = 2789.955 FPS
13896 frames in 5.0 seconds = 2778.911 FPS
11658 frames in 5.0 seconds = 2331.540 FPS
9699 frames in 5.0 seconds = 1938.410 FPS
16857 frames in 5.0 seconds = 3371.393 FPS
10005 frames in 5.0 seconds = 1999.342 FPS
13917 frames in 5.0 seconds = 2783.358 FPS
10753 frames in 5.0 seconds = 2150.537 FPS
10431 frames in 5.0 seconds = 2086.192 FPS

Can anybody confirm that these are normal readings?

WoW @ windows gives me 60 fps for i have vsync on. Cause of my dual core i wont get more than 64fps anyway cause of the dual core bug.
WoW @ linux gives me like 5-10fps in OG in opengl mode and about 15fps in direct3d mode.

Anybody can tell me if i ever will get normal performance with my ATI card?
Still using windows for WoW and i really hate the constant OS switching.

Hmm, you shouldn't need to patch as an ATI user, also, opengl mode should work for you. I don't use ATI cards as NVIDIA has better linux drivers, but so says the Wine AppDB. They do recommend some [tricks and tweaks post install]("http://appdb.winehq.org/appview.php?iVersionId=5606")
[/SIZE][/FONT]      [FONT=Verdana][SIZE=2] if you're having issues. Your glxgears framerate looks OK, don't think you can do much better on ATI, the driver support isn't there. You could try the latest ones from ATI, rather than the Ubuntu packaged ones.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
Is this:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
``` The error you get?
If so, try disabling desktop double buffering in winecfg.
[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]

---

### Post by Magiclamp on 2006-08-26
> sudo nano /etc/apt/sources.list

I added the wine deb, and installed world of warcraft, and everything is fine, but now my system will not update. I am using Kubuntu Dapper Drake, 32 bit....on 1ghz pentium, with 512 ram...

can anyone help me, so I can add the proper deb file or whatever so I can update my machine again? (I am a linux/kubuntu newb)

*Also, I have a 64 bit machine (AMD 3500, 512 ram, onboard video) and I got wine to work and WOW to install, however the login screen is buggy as well as the game. When you enter in your account name and password, the text is all jumbled....and when you actually play the game, the bottom bar is all weird as well. Anyone experience this? ](*,)

---

### Post by eqisow on 2006-08-26
Just a note, I've updated the WoW wiki with patched binaries for 0.9.20 so feel free to update your howto accordingly. Also, you should consider merging this howto with the wiki.

Edit: Oh, and another note, when you install the patched .deb from the wiki Synaptic will keep trying to update Wine even though you're running the same version. This can be solved by locking Wine to your current version. Just select Wine in Synaptic then go to package --> Lock Version. The only caveat is that the updater will not tell you when Wine 0.9.21 is released.

I should probably add that info to the wiki...

---

### Post by Tanth on 2006-08-26
I get this error in the terminal along with the Error:132 in WoW when I try to run wow.exe :

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eee0,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

any ideas?

---

### Post by eqisow on 2006-08-26
What video card do you have? Also, it would be helpful if you could post the contents of /etc/X11/xorg.conf.

---

### Post by Orunitia on 2006-08-26
Okay... it used to work under linux a few weeks ago before I cancelled. I feel like getting back into it, but I can't get it to start after reinstalling it. It says it can't start 3d acceleration. glxgears runs fine.

```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d670000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d670000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f14c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40M? [GeForce Go 6250]"
    Driver         "nvidia"
    Option "NoLogo"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40M? [GeForce Go 6250]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600"
    EndSubSection
EndSection


```

---

### Post by eqisow on 2006-08-26
Usualy that error is the result of a misconfigured xorg.conf. However, yours seems to be just fine.

If you haven't restarted X since instaling the drivers, do that with Ctrl + Alt + Backspace.

Other than that, I'm not sure... I'll continue to look into it.

Edit: What is the output of ```
glxinfo | grep rendering
```?

Edit again: Also, did you swap in a non-nvidia card then put the nvidia card back in? Since you're using an Go 6250 I'm going to assume that's a no, but leave no stone unturned, eh?

---

### Post by Orunitia on 2006-08-26
chaos@lunix:~$ glxinfo | grep rendering
direct rendering: No

I've had the nvidia drivers installed a few weeks now. And it's a laptop, no swapping of video cards going on here. :P

---

### Post by eqisow on 2006-08-26
OK, so lack of direct rendering is definitely the issue... but I'm still not sure why direct rendering isn't working.

Post your /var/log/Xorg.0.log.

Edit: Also, have you tried any other 3D applications? Do they work?

Edit again: Oh, and are you running XGL/Compiz?

Last edit: Are you using the repository nvidia-glx package or did you get drivers from nvidia.com?

---

### Post by Orunitia on 2006-08-26
> Edit again: Oh, and are you running XGL/Compiz?

I was a few days ago, but I uninstalled all that crap. Oddly enough I restarted one more time and everything is working fine.

direct rendering: Yes

WoW is running now. Thanks for trying to help though, I really appreciate it.

---

### Post by eqisow on 2006-08-26
You're welcome, congrats on getting it working.

---

### Post by JexicanMidget on 2006-08-26
I followed everything and WoW runs great except that I can't click on characters.  I can select bad guys using tab but I can't click on the people at the auction house or use griffin riders.  Anyone seen this before?

---

### Post by autrui on 2006-08-26
> **JexicanMidget said:**
> I followed everything and WoW runs great except that I can't click on characters.  I can select bad guys using tab but I can't click on the people at the auction house or use griffin riders.  Anyone seen this before?

that's weird.  i dont have any real solution, but to deal with the symptom, u might try Ctrl+Tab--that's how to tab thru friendly npcs and players.  (i think it's Ctrl+Tab, might be Shift+Tab.)

my mouse situation was weird at first, too--i didn't get that symptom, but i saw both a little arrow and and little pointing hand, and the latter was about an inch higher than the former.  my solution was screwing with the video settings; but i don't know if that's relavant to your problem.

good luck, and i hope someone is able to give you a real solution!

autrui

---

### Post by JexicanMidget on 2006-08-26
Ctrl + Tab does let me select friendlies but like with the griffin riders, I am then unable to right click on them to start talking.  Running all over the place and not being able to empty bags is frustrating.

---

### Post by tokyovigilante on 2006-08-26
> **eqisow said:**
> Just a note, I've updated the WoW wiki with patched binaries for 0.9.20 so feel free to update your howto accordingly. Also, you should consider merging this howto with the wiki.

Edit: Oh, and another note, when you install the patched .deb from the wiki Synaptic will keep trying to update Wine even though you're running the same version. This can be solved by locking Wine to your current version. Just select Wine in Synaptic then go to package --> Lock Version. The only caveat is that the updater will not tell you when Wine 0.9.21 is released.

I should probably add that info to the wiki...
Thanks, will do, I'm pretty much relying on your patched build while I muck round trying to get a 32-bit build environment in AMD64.

I'll look into adding all this to the Wiki, it pretty much complements what's already there, just a bit more nitty-gritty about system setup. I think wine is to the stage that when set up well, partic on NVIDIA, that WoW runs really well, what we really need is an easier way to set it all up.
> **JexicanMidget]
I followed everything and WoW runs great except that I can't click on characters. I can select bad guys using tab but I can't click on the people at the auction house or use griffin riders. Anyone seen this before?
[/quote]
You've got the mouse bug, weird, I thought that had been fixed a long time ago.
Try adding
```
  said:**
> 
 "MemoryLayoutOverride" = "0x10000000"
``` To ~/.wine/user.reg.
[quote=tanth]
	I get this error in the terminal along with the Error:132 in WoW when I try to run wow.exe :

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:razz:rocess_attach Could not create default context.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eee0,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

any ideas?

Set up your video card properly, then post the contents of /etc/X11/xorg.conf and the result of glxinfo | grep rendering.

---

### Post by JexicanMidget on 2006-08-26
> 
You've got the mouse bug, weird, I thought that had been fixed a long time ago.
Try adding
```
 ;; App default settings
 ;; World of Warcraft settings
 [AppDefaults\\WoW.exe\\memory]
 "MemoryLayoutOverride" = "0x10000000"
``` To ~/.wine/user.reg.



Is there a certain spot to put it?  I am quite the noob and i just placed it at the bottom of the .reg file.  After pasting it in and closing out of WoW and opening it back up, the problem was still present.  Let me know what I should have done differently.

---

### Post by tokyovigilante on 2006-08-26
> **JexicanMidget said:**
> Is there a certain spot to put it?  I am quite the noob and i just placed it at the bottom of the .reg file.  After pasting it in and closing out of WoW and opening it back up, the problem was still present.  Let me know what I should have done differently.

No it shouldn't matter. Hmm. Thats actually a Cedega hack to fix the same problem under that platform. I'm at a bit of a loss to explain it really, cause it had to do with a WoW bug that was apparently fixed in both WoW and Cedega. Have a google and see if anyone running wine has seen it. Also, try upgrading to 0.9.20, i've just updated the howto.

---

### Post by yfronto on 2006-08-26
So, I've been reading through forums and HOWTOs all day, and I was able to install and run WoW just fine (after a bit of work with my nvidia drivers), the intro movie was beautiful. I connected and the downloader and updater worked fine, but now I can't start the program back up. Each time I try, I receive an error relating to "InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4", then a BadMatch. Any ideas what could be the problem here? I don't believe any other settings were changed. Thanks all.

---

### Post by JexicanMidget on 2006-08-26
> **tokyovigilante said:**
> No it shouldn't matter. Hmm. Thats actually a Cedega hack to fix the same problem under that platform. I'm at a bit of a loss to explain it really, cause it had to do with a WoW bug that was apparently fixed in both WoW and Cedega. Have a google and see if anyone running wine has seen it. Also, try upgrading to 0.9.20, i've just updated the howto.

I have wine 0.9.6 right now.  Does that matter?

---

### Post by JexicanMidget on 2006-08-27
> **yfronto said:**
> So, I've been reading through forums and HOWTOs all day, and I was able to install and run WoW just fine (after a bit of work with my nvidia drivers), the intro movie was beautiful. I connected and the downloader and updater worked fine, but now I can't start the program back up. Each time I try, I receive an error relating to "InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4", then a BadMatch. Any ideas what could be the problem here? I don't believe any other settings were changed. Thanks all.

It kinda sounds like you don't have the MozillaControl installed right.  Did you get an error when installing that?  Here's what i found under another post:

Get the two Windows .dll files necessary:
[http://www.dll-files.com/dllindex/dl....shtml?msvcp60](http://www.dll-files.com/dllindex/dl....shtml?msvcp60)
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

Now we can put the .dll files in the system folder:
$ mv msvcp60.dll mfc42 ~/.wine/drive_c/windows/system32/

Now we need to install MozillaControl under wine:
$ wine MozillaControl1712.exe

Not sure if that helps you but its what I did and the updaters worked just fine.

---

### Post by yfronto on 2006-08-27
MozillaControl installed fine and I copied the dlls, but no dice. I does look like a dll issue or maybe a configuration error, though.

---

### Post by tokyovigilante on 2006-08-27
> **yfronto said:**
> So, I've been reading through forums and HOWTOs all day, and I was able to install and run WoW just fine (after a bit of work with my nvidia drivers), the intro movie was beautiful. I connected and the downloader and updater worked fine, but now I can't start the program back up. Each time I try, I receive an error relating to "InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4", then a BadMatch. Any ideas what could be the problem here? I don't believe any other settings were changed. Thanks all.
The internet timeout you're seeing is a separate issue and shouldn't affect gameplay. The real issue is the BadMatch, and generally relates to video. Post up your config and /etc/X11/xorg.conf.

---

### Post by tokyovigilante on 2006-08-27
> **JexicanMidget said:**
> I have wine 0.9.6 right now.  Does that matter?
Absolutely ;) that version just won't work. I only wanted people to install wine 0.9.6 so that apt would install dependencies at the same time. You absolutely have to have 0.9.18 or higher, otherwise it just won't work. No wonder you're having the mouse bug, it wasn't fixed till wine 0.9.16 or so. 

Go back to the howto, and follow the wine install instructions appropriate to your hardware.

---

### Post by yfronto on 2006-08-27
Here it be:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung SyncMaster 955b"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

As far as I can tell everything looks right, but I'm no expert. Thanks for the help.

EDIT:

Okay, now I'm getting a different error... when I start it, my screen resizes from 1280x1024 to 1024x768, goes blank, then it comes back on and stays at 1024x768, I have to manually put the resolution back. Here's the info from the command line:

```

$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c250000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c250000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)X connection to :0.0 broken (explicit kill or server shutdown).

```

---

### Post by tokyovigilante on 2006-08-27
> **yfronto said:**
> Here it be:


As far as I can tell everything looks right, but I'm no expert. Thanks for the help.

EDIT:

Okay, now I'm getting a different error... when I start it, my screen resizes from 1280x1024 to 1024x768, goes blank, then it comes back on and stays at 1024x768, I have to manually put the resolution back. Here's the info from the command line:

```

$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c250000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c250000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)X connection to :0.0 broken (explicit kill or server shutdown).

```

Well, that's promising...

There's nothing there I don't get when I run it. Is your monitor being correctly detected? What happens when you set it to 1024x768 then run WoW? Also, try adding SET gxWindow "1" to Config.wtf to start WoW in windowed mode. Seems you're having issues with the mode switch to get WoW up.

---

### Post by yfronto on 2006-08-27
If I set my resolution to 1024x768 then start WoW, the music starts playing, but then the program closes and gives me errors related to the program itself (ie, "Submit feedback to Blizzard on this issue"), windowed mode does the same thing.

Here's what my Config.wtf looks like now, if it helps:

```

SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxWindow "1"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"

```


EDIT: 

Screenshot:

---

### Post by yfronto on 2006-08-27
Sorry for the double post.
I tried running wine WoW.exe -d3d and the game seems to work perfectly, all the way until I enter the world. Then everything looks okay but the environment. My UI is fine, and my character is fine, but all graphics are completely impossible to distinguish, like I'm having clipping issues. It works the same way for either full screen or windowed mode.

EDIT: 
So long as I stay outside, everything is fine... but the minute I get close to buildings, wagons, etc, shapes start going crazy. I'm off to bed for the night, maybe I'll have some fresh ideas in the morning.

---

### Post by JexicanMidget on 2006-08-27
I uninstalled my version of wine and followed the instructions here and have 9.20 now.  Couple things are funny though.  For starters when I click on the audio tab in winecfg it dumps me out and i get this error:

Creating link /home/pschaefer/.kde/socket-pschaefer-desktop.
can't create mcop directory

I started the install of WoW (yes, going from scratch here) and all the text on the buttons were small.  I hope this isn't an indication of what is to come.

Other than that its off to a good start.  I'll let you know how it goes.

---

### Post by highmage on 2006-08-27
Brilliant. After countless days and hours throwing myself against obsticles in other howto's, I went from scratch to cruising around Ironforge in less than 15 minutes. 

I encountered the same problem when selecting the Audio tab, but sound seems to be working fine. Much thanks for the howto and subsequent support.

---

### Post by tokyovigilante on 2006-08-27
> **JexicanMidget said:**
> I uninstalled my version of wine and followed the instructions here and have 9.20 now.  Couple things are funny though.  For starters when I click on the audio tab in winecfg it dumps me out and i get this error:

Creating link /home/pschaefer/.kde/socket-pschaefer-desktop.
can't create mcop directory

I started the install of WoW (yes, going from scratch here) and all the text on the buttons were small.  I hope this isn't an indication of what is to come.

Other than that its off to a good start.  I'll let you know how it goes.
Hmm, that is strange. Did you set the ALSA timeout in System Settings to 1 second?
[quote=highmage]

Brilliant. After countless days and hours throwing myself against obsticles in other howto's, I went from scratch to cruising around Ironforge in less than 15 minutes. 

I encountered the same problem when selecting the Audio tab, but sound seems to be working fine. Much thanks for the howto and subsequent support.
[/quote]
Good to hear, one happy customer at least ;)

---

### Post by JexicanMidget on 2006-08-27
Did not change any system settings.  I'm not to worried about that error anyway cause IT WORKS!!!!

I am a right clickin fool!  The new version of Wine worked wonderfully!  Thank you for all your help!

Now to destory the Alliance...

---

### Post by nhimf on 2006-08-27
> **tokyovigilante said:**
> [FONT=Verdana][SIZE=2]

Hmm, you shouldn't need to patch as an ATI user, also, opengl mode should work for you. I don't use ATI cards as NVIDIA has better linux drivers, but so says the Wine AppDB. They do recommend some [tricks and tweaks post install]("http://appdb.winehq.org/appview.php?iVersionId=5606")
[/SIZE][/FONT]      [FONT=Verdana][SIZE=2] if you're having issues. Your glxgears framerate looks OK, don't think you can do much better on ATI, the driver support isn't there. You could try the latest ones from ATI, rather than the Ubuntu packaged ones.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
Is this:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
``` The error you get?
If so, try disabling desktop double buffering in winecfg.
[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]

I have installed the latest ATI drivers, i always use the drivers from ATI itself cause they arrive before ubuntu has them packaged :wink: 

As for my hangup without the patched one, The game hangs and hard. No ctl-alt-backspace, ctrl-2 or alt-tab will make me be able to look at any errors. I have to reset my machine.
So actually i have no clue about any error :P
But i'll try to kill the desktop double buffering and see if it helps

edit:
I have tried to disable the doublebuffering and it didnt work. I removed all of wine and the .wine dir before i reinstalled it.
For some reason it wont work and the patched does.

---

### Post by eqisow on 2006-08-27
Hmm, can anybody duplicate nhimf's findings? Perhaps there is a regeression in 0.9.20?

Edit: It should be noted that I applied the 0.9.18 (nvidia) patch to 0.9.20 before the AppDB was updated (it's actually still not updated), so I was simply assuming that it was still needed. There is another patch from [here]("http://wine.getcontinuum.com/compile.php") installed as well.

---

### Post by nhimf on 2006-08-27
> **eqisow said:**
> Hmm, can anybody duplicate nhimf's findings? Perhaps there is a regeression in 0.9.20?
...

If somebody want to try to reproduce i can give some additional info:
The 0.9.18 worked fine, besides the very low FPS, but it didnt crash or something. Also 0.9.18 did worked fine with D3D, as others also noticed that 0.9.19 & 20 have broken D3D.

I work on Ubuntu AMD64, have selected the K8-SMP kernel (although it seems to be the same as the K8 kernel).
Everything is up-to-date and i work with the latest (8.28.8) ati drivers taken from the ati site.

My specs:
Radeon x1900xt
AMD Athlon 64 x2 3800+
2GB RAM
Asus K8N-E motherboard

edit:
I have tried the 0.9.20 with wow patch and that one doesnt work either.
So at this moment i'm running 0.9.19-wow and that one works. Still not very playable but it runs.

---

### Post by msgyrd on 2006-08-27
Just adding my experience:

Installed Ubuntu at noon.
Ran Automatix and installed most of the stuff there (including nVidia drivers).

Copied WoW over, clicked on the icon, and it actually ran (I was surprised).  The framerate was horrible and sound didn't work, so I tried the -opengl flag.  That made the video problems worse (verticle sync issues and screen tearing), so I went and found this guide.

Followed directions for my videocard (nVidia 7600), and configuring wine and config.wtf, had WoW running with sound at 30fps by 1:30pm.


Some observations:

I'm fairly certain my dual core chip isn't being used fully, but I havn't messed with my kernel yet. Yes, I'll admit I skipped that 'performance kernel' step.  That may be some of my performance issues.

My framerate is almost half of what it was in Windows.  30fps in IF, but when I'm in combat, it can drop into the mid teens.  I'm going to mess with things later, but I'm satisfied that it's working.

The sound is certainly acceptable, but it's perceptibly different than windows. Maybe it's a slight lag or something, but it just sounds a tad different. I probably won't mess with it because it's not worth the effort, but it's there.




Thank you for writing this guide.  It certainly made the process much easier.  Overall I'm very pleased at how easy it was to get it working.  Thanks again.

P.S -   Has anyone had any luck getting the Windows Ventrilo client to work under wine?

---

### Post by tokyovigilante on 2006-08-27
> **nhimf said:**
> If somebody want to try to reproduce i can give some additional info:
The 0.9.18 worked fine, besides the very low FPS, but it didnt crash or something. Also 0.9.18 did worked fine with D3D, as others also noticed that 0.9.19 & 20 have broken D3D.

I work on Ubuntu AMD64, have selected the K8-SMP kernel (although it seems to be the same as the K8 kernel).
Everything is up-to-date and i work with the latest (8.28.8) ati drivers taken from the ati site.

My specs:
Radeon x1900xt
AMD Athlon 64 x2 3800+
2GB RAM
Asus K8N-E motherboard

edit:
I have tried the 0.9.20 with wow patch and that one doesnt work either.
So at this moment i'm running 0.9.19-wow and that one works. Still not very playable but it runs.

Hmm. everyone with ATI seems to be having issues. Can everyone with ATI who has WoW working/not working post their driver version and whether WoW is working or not? 

Everyone seems to be using the patched version of 0.9.19. My understanding from the AppDB page was that only NVIDIA cards needed the patch. If anyone on ATI is keen for an experiment, try installing the unpatched 0.9.20 and add the following modes to your xorg.conf:
> 
One thing to note, in earlier versions of WoW (1.11) i had posted problems with Desktop double buffering being enabled in winecfg and wow crashing. X Error of failed request:  BadMatch (invalid parameter attributes)
  ....
The solution to my problem was to alter my xorg.conf file in /etc/X11 directory and add 32 bit screen modes like so:
```
Section "Screen"
        SubSection "Display"
                Depth     32
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

EndSection
```  
If you are having sound issues, try fiddling the SoundBufferSize in Config.WTF between 50-150. The lowest you can get without skipping is best for latency.

If you get poor framerates with ATI cards, the best option is to ebay it and get an NVIDIA, ATI has awful linux support, and we should really be voting for good driver support with our wallets.

---

### Post by yfronto on 2006-08-27
Okay, I did a complete removal of wine, and let Synaptic download and install 0.9.19, then installed WoW from scratch. Everything looks beautiful and works great, no clipping issues or screen tearing (d3d still has major issues with tearing, but opengl has no problems). The only problem I have now is an inability to go indoors. Whenever I try to enter any building, town, etc, the game crashes. And I get:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  488
  Current serial number in output stream:  488

```

Everything looked and sounds perfect otherwise, so I must be close. ;)

---

### Post by tokyovigilante on 2006-08-27
> **yfronto said:**
> Okay, I did a complete removal of wine, and let Synaptic download and install 0.9.19, then installed WoW from scratch. Everything looks beautiful and works great, no clipping issues or screen tearing (d3d still has major issues with tearing, but opengl has no problems). The only problem I have now is an inability to go indoors. Whenever I try to enter any building, town, etc, the game crashes. And I get:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  488
  Current serial number in output stream:  488

``` 
Everything looked and sounds perfect otherwise, so I must be close. ;)
You need the patched version from piratecove, the official package won't work. This bug is why the patch exists. Replace the repository version with the patched one and you'll be fine.

---

### Post by yfronto on 2006-08-27
Well that fixed the inside/outside problem, but I've lost sound, any ideas what could be wrong there?

EDIT: 

Also, my mouse is not functioning properly. The wheel scrolls in/out and pushing the wheel makes me move, but I can't actually select anything. I can use the TAB to select, and I can use the mouse to navigate menus, but I just can't select any objects.

EDIT:

If I set my Audio in winecfg to be ALSA, I get sound, but I have to crank the SoundBufferSize up to 150 for it to sound smooth, and then it's pretty delayed. OSS seems to be the prefered choice, any ideas why it doesn't work?

---

### Post by eqisow on 2006-08-27
ALSA works with more cards than OSS, so maybe your sound card works with ALSA  and not OSS? What card do you have?

---

### Post by yfronto on 2006-08-28
```

lspci|grep audio

0000:00:1f.5 Multimedia audio controller: 
Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio 
Controller (rev 01)

```

It's just onboard. It's crap, but everything else on my computer (CDs, sound files, midis) work fine, just wine seems to have issues.

EDIT:

Oh, jeez, I broke it. I tried installing additional packages for OSS support, and now when I bring up winecfg and try to click on the audio tab, I get:

```

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/kas/.kde/socket-Darkstar.
can't create mcop directory

```

Winecfg then crashes.

---

### Post by yfronto on 2006-08-28
Okay, so sound problems aside, anyone have any idea what's wrong with selecting? I read somewhere that the game has problems switching the foreground/background, and that if you look all the way up and select something standing on top of you it works, So I tried that, and it's true, I can select anything as long as I'm standing on top of it and look all the way up. The recommended fix for this was to get a patched version of wine, which I did.

EDIT:

BTW, the fix for the sound issue was to make the directory it was looking for. Now I don't have sound issues. I guess I installed some sort of missing library and in the process ended up installing something related to KDE. Not sure what fixed the sound exactly, but if you're getting a similar error, try  making the dir, it worked for me.

---

### Post by nhimf on 2006-08-28
> **tokyovigilante said:**
> Hmm. everyone with ATI seems to be having issues. Can everyone with ATI who has WoW working/not working post their driver version and whether WoW is working or not? 

Everyone seems to be using the patched version of 0.9.19. My understanding from the AppDB page was that only NVIDIA cards needed the patch. If anyone on ATI is keen for an experiment, try installing the unpatched 0.9.20 and add the following modes to your xorg.conf:
 
If you are having sound issues, try fiddling the SoundBufferSize in Config.WTF between 50-150. The lowest you can get without skipping is best for latency.

If you get poor framerates with ATI cards, the best option is to ebay it and get an NVIDIA, ATI has awful linux support, and we should really be voting for good driver support with our wallets.

I have tried this and it wont make 0.9.20 work.

Also i quite noticed that after a fresh startup i get as many as twice the FPS in glxgears.
After i started wow and leave it will drop to the 2000-3300 as i said before and when i have a fresh startup (or ctrl-alt-backspace) i get as many as 5400-6600.
Quite odd if you ask me.

---

### Post by tokyovigilante on 2006-08-28
> **nhimf said:**
> I have tried this and it wont make 0.9.20 work.

Also i quite noticed that after a fresh startup i get as many as twice the FPS in glxgears.
After i started wow and leave it will drop to the 2000-3300 as i said before and when i have a fresh startup (or ctrl-alt-backspace) i get as many as 5400-6600.
Quite odd if you ask me.

That is odd. Try running KinfoCenter (or the Gnome equiv), and check to see you don't have something running thats leaking memory. I can't imagine what else would give you a drop off like that.

---

### Post by JexicanMidget on 2006-08-29
I have another tower with an ATI Radeon x600 that is having some problems.  I have the most current ATI Drivers and the same version of Wine as on my box with an Nvidia card (.0.9.20).  When I run WoW.exe -opengl everything is shakey and you can't really make anything out.  Running it with the -d3d tag everything is smooth excecpt it doesn't display right.  The interface is correct (the menu buttons and what not) but the picture behind it is shifted down about half the screen so I can't see the bottom half.  Direct Rendering is Yes and here is my xorg.conf is:

[HTML]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL 2007FP"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Monitor    "DELL 2007FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
[/HTML]

My glxgears fps is only 25 fps.

Any suggestions?  I really don't want to have XP for just World of WarCraft.

---

### Post by tokyovigilante on 2006-08-29
> **JexicanMidget said:**
> I have another tower with an ATI Radeon x600 that is having some problems.  I have the most current ATI Drivers and the same version of Wine as on my box with an Nvidia card (.0.9.20).  When I run WoW.exe -opengl everything is shakey and you can't really make anything out.  Running it with the -d3d tag everything is smooth excecpt it doesn't display right.  The interface is correct (the menu buttons and what not) but the picture behind it is shifted down about half the screen so I can't see the bottom half.  Direct Rendering is Yes and here is my xorg.conf is:

[html]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath     "/usr/share/X11/fonts/misc"
    FontPath     "/usr/share/X11/fonts/cyrillic"
    FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/Type1"
    FontPath     "/usr/share/X11/fonts/100dpi"
    FontPath     "/usr/share/X11/fonts/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "vbe"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc104"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "DELL 2007FP"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
    Driver      "vesa"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
    Monitor    "DELL 2007FP"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection
[/html] 
My glxgears fps is only 25 fps.

Any suggestions?  I really don't want to have XP for just World of WarCraft.

That's the most confusing xorg.conf i've ever read. It would seem the ATI config tools have made a mess.

Clean it up by
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
sudo dpkg-reconfigure xserver-xorg 
```
and selecting fglrx as the video driver, then defaults for everything else. Restart the xserver (Ctrl-Alt-Backspace) and see what you get from glxgears then.

---

### Post by JexicanMidget on 2006-08-29
I'll give it a go when I get home tonight and post my results.  Thanks!

---

### Post by justin whitaker on 2006-08-29
> **msgyrd said:**
> P.S -   Has anyone had any luck getting the Windows Ventrilo client to work under wine?

Not to my knowledge. Teamspeak reportedly works, with some ALSA hacking. :(

---

### Post by lmandrake on 2006-08-29
Overall WoW is running nicely (after switching to the lowest graphical setting it's even playable) with wine 0.9.19 and the latest Ati drivers. Problem is that when I switch back to the KDE Desktop my system completly freezes :( This does not happen instantly but always after a short time, like writing the first sentence of an email. This only happens when I switch during playing and start doing some stuff; programs running in the background (kmail, music) are not doing any harm for example kopete fading in its online status windows. Is somebodyelse experiencing this behavior?
Should I upgrade to 0.9.20?

---

### Post by JexicanMidget on 2006-08-29
well that did not seem to fix the problem.  I do notice this in my terminal after closing WoW:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  144 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x2400059
  Serial number of failed request:  491
  Current serial number in output stream:  491


Not sure what that means...

---

### Post by jadugartir on 2006-08-29
I finally finished this guide, and got wine working with no errors. I got wow copied and set up, updated my ati drivers to 8.27.10, and started up wow.

When i launched in OpenGL it wasnt working, so i launched by just right clicking wow.exe and selecting "Open with Wine"

That worked beautifully, the graphics were nice and smooth framerate, good sound. Then about 10-15 seconds later it freezes and i have to reboot. How do i fix it?

---

### Post by tokyovigilante on 2006-08-29
> **jadugartir said:**
> I finally finished this guide, and got wine working with no errors. I got wow copied and set up, updated my ati drivers to 8.27.10, and started up wow.

When i launched in OpenGL it wasnt working, so i launched by just right clicking wow.exe and selecting "Open with Wine"

That worked beautifully, the graphics were nice and smooth framerate, good sound. Then about 10-15 seconds later it freezes and i have to reboot. How do i fix it?

Having read all the issues people are having with ATI cards and random kernel panics, I honestly don't think that there is a fix. Running in OpenGL mode is the only really supported mode from Wine's point of view, the Direct3D support is not sufficiently there to prevent conflicts with the driver. You could try different versions of the ATI driver, but realistically it just doesn't work well with ATI. If anyone else knows different or better I'm all ears, but otherwise my advice is, if you want to play WoW under Ubuntu with wine, get an NVIDIA card.

---

### Post by jadugartir on 2006-08-29
so no one has gotten it to run on an ATI card?

---

### Post by AriseNow on 2006-08-29
Thanks :)  Refreshingly straightforward HowTo, of course, only now after a few  months am I going to reactivate my WoW account and BAM right in my face version 1.12 465MB :-# 
Let's see if everything goes along well when it finishes (I half expected wine to act all crazy like it does for some apps :p ).

---

### Post by gdoyel on 2006-08-30
This is a great guide, but I'm wondering if you can shed any light on another issue: what about for Intel?

I was in the processes of converting from XP to Ubuntu back in the last release, but I couldn't seem to get WoW working under Wine or Cedega (again, another Intel graphics). My WoW addiction kept me from sticking around in the linux world.

I finally bought a new lappy (I was not impressed with my ThinkPad) and I'd like to _try_ to make the jump to Ubuntu again.

Please, any help / guidance is appreciated.

---

### Post by tokyovigilante on 2006-08-30
> **jadugartir said:**
> sI recently got wow to stop freezing on my ati card, but then it started doing it again, i think maybe if i disable the sound somehow it could make it run. is there a config file i can edit?
Try disabling it under sound options in WoW itself, or set SoundOutputSystem to "0" in WTF/Config.wtf. I sincerely doubt this will solve the issue however. In future please ask questions in the thread where everyone can have the benefit of seeing problems and solutions.

---

### Post by tokyovigilante on 2006-08-30
> **gdoyel said:**
> This is a great guide, but I'm wondering if you can shed any light on another issue: what about for Intel?

I was in the processes of converting from XP to Ubuntu back in the last release, but I couldn't seem to get WoW working under Wine or Cedega (again, another Intel graphics). My WoW addiction kept me from sticking around in the linux world.

I finally bought a new lappy (I was not impressed with my ThinkPad) and I'd like to _try_ to make the jump to Ubuntu again.

Please, any help / guidance is appreciated.
I guess it's just a matter of enabling direct rendering - ie glxinfo | grep rendering returns "Yes". That will depend on your chipset (ie 810/15, 845, 965 etc.) Intel has open source drivers so in theory Ubuntu should enable this by default, but i've had no experience with this. [This]("https://help.ubuntu.com/community/i915Driver") should be what you need though.

---

### Post by Zoglarfy on 2006-08-30
EXCELLENT guide, tokyovigilante.  WoW is running on my system with only minimal issues.

The main issue is the choppy video.  It starts out smooth as silk, but after you go into an area that's even slightly crowded, it starts chopping like crazy.  I don't know if this is a common issue or not.  There were a few people with similar problems, but I couldn't find a solution that worked for me.

The choppiness doesn't seem to have anything to do with the in-game video settings.  It chops just as much on the lowest settings as it does on the highest.  Enabling/Disabling all sound has no effect.

One thing I'll say: Trying to get games running properly on Linux almost becomes a game itself. :D

---

### Post by Rody on 2006-08-30
This is a pretty good gide, thanks a bunch.

that being said...

  I am having a problem with the Wine part. everything works fine as long as I use a 386 kernal, if I use 686,k7, or k8 winecfg hard locks the system and trying to play world of warcraft hardlocks the system. This seems really weard to me. I can understand it hardlocking on K8 64bit system, but with the 686 or k7 it seems that it should just work. 

  is there some switch i need to run to make it work with the other kernals? I would just run it in 386 mode... but i only get about 20fps not even close to playable.


thanks for any help
rody

ps 
system specs

mobo  :msi dimond plus ( 7220 )
cpu   :amd 4400x2
Ram   :2GB supertalent
vid   :Nvidia gforce 7800 gtx 512
sound ::onboard audige + soundblaster live

---

### Post by larsemil on 2006-08-31
> **tokyovigilante said:**
> 
   Now, for the moment you've all been waiting for:
   ```
cd ..
   wine WoW.exe -opengl
``` 



for some users wine WoW.exe -d3d gives better performance. for me for instance the opengl gives about 1-5fps while -d3d gives about 30.

---

### Post by ksponge on 2006-08-31
Thanks for the effort.  I'm having a problem.  Like others, -opengl does not work for me (ati x800 xt pe).  The screen is scrambled and I can't make much out.  With d3d this is not the case.  However, whenever I try to connect, it sticks at authenticating... and stays there.  Something with the network and wine obviously(connected through router).  Any idea how a linux noob can fix this?

---

### Post by tokyovigilante on 2006-08-31
> **Rody said:**
> This is a pretty good gide, thanks a bunch.

that being said...

  I am having a problem with the Wine part. everything works fine as long as I use a 386 kernal, if I use 686,k7, or k8 winecfg hard locks the system and trying to play world of warcraft hardlocks the system. This seems really weard to me. I can understand it hardlocking on K8 64bit system, but with the 686 or k7 it seems that it should just work. 

  is there some switch i need to run to make it work with the other kernals? I would just run it in 386 mode... but i only get about 20fps not even close to playable.


thanks for any help
rody

ps 
system specs

mobo  :msi dimond plus ( 7220 )
cpu   :amd 4400x2
Ram   :2GB supertalent
vid   :Nvidia gforce 7800 gtx 512
sound ::onboard audige + soundblaster live

Hmm, I'm a bit confused. Which distribution (32 or 64 bit) are you running? If you are trying to use a 386, 686 or k7 kernel with amd64, or an amd64 kernel with i386, this just won't work. However if you mean that you get lockups with amd64 kernels with an amd64 install, or using the k7 kernel on i386, that is bad and shouldn't happen. 

I have a similar system and have not had issues with instability. I recommend using 64 bit, installing the -amd64-k8 kernel, and using the envy script to get the latest nvidia drivers, as I've found this to be the most stable platform. If you still get lockups, you may have a hardware failure. Try running memtest from the boot menu.

---

### Post by tokyovigilante on 2006-08-31
> **ksponge said:**
> Thanks for the effort.  I'm having a problem.  Like others, -opengl does not work for me (ati x800 xt pe).  The screen is scrambled and I can't make much out.  With d3d this is not the case.  However, whenever I try to connect, it sticks at authenticating... and stays there.  Something with the network and wine obviously(connected through router).  Any idea how a linux noob can fix this?
If you have networking enabled and can access the internet through Ubuntu, WoW should be fine. Post up the results of 
ping [www.google.com](www.google.com) (press Ctrl-C after a few seconds)
ifconfig -all

---

### Post by Rody on 2006-08-31
I use 386,k7, and 686 for a 32bit install, and k8 for a 64 bit install. i have reinstalled several times now to try diferent things. :)

The problem is not the the gfx, but a problem whith Wine trying to set up.

I wonder, i have 4 hard drives in my system,3 sata, 2 raptors in raid 0 ,one 200gb WD for storage, and the drive i am instaling on is an old ibm 20gb drive. I wonder if i am geting a conflict some where. this evening i might unplug some drives and see. Of couse for it to work witha 386 kernal with no errors and hard lock with any other kernal is still odd.

rody

---

### Post by tokyovigilante on 2006-08-31
> **Rody said:**
> I use 386,k7, and 686 for a 32bit install, and k8 for a 64 bit install. i have reinstalled several times now to try diferent things. :)

The problem is not the the gfx, but a problem whith Wine trying to set up.

I wonder, i have 4 hard drives in my system,3 sata, 2 raptors in raid 0 ,one 200gb WD for storage, and the drive i am instaling on is an old ibm 20gb drive. I wonder if i am geting a conflict some where. this evening i might unplug some drives and see. Of couse for it to work witha 386 kernal with no errors and hard lock with any other kernal is still odd.

rody
In linux, user mode programs cannot cause a kernel panic and lock up the system, only device drivers can do that. So you must have a kernel or device driver issue, or alternatively a hardware issue.

Did you try the envy script on amd64?

---

### Post by deboring21 on 2006-08-31
Hey, I followed other guides and got WoW working through them. So when I reloaded the other Ubuntu 64 Bit distros (Xubuntu and Kubuntu, both which I didn't like), I decided to come back to Ubuntu 6.06 64 Bit. I came across your guide and thought I'd give it a try. But when I tried one of the first steps, "sudo apt-get install wine," I got the message:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
I enabled all of the repositories in Synaptic hoping that might fix it, but no go. If you need any more info, let me know.
-Ryan

** Nevermind, I followed: [https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64) and got it working fine, thanks anyways...

---

### Post by AriseNow on 2006-09-01
Hey, the game worked! Funny enough, my game works best on the -opengl option. When I tried the -d3d one graphics were noticeably faster and smoother, but some buildings looked like a smart bomb had blown them up :tongue: textures were crazy and blocked doors and such.

What I want to ask is: what settings can we use to optimize the video, sound, fps, etc. ?

I have a nvidia 6600 and pretty much everything has gone smoothly up until now.

---

### Post by tokyovigilante on 2006-09-01
> **AriseNow said:**
> Hey, the game worked! Funny enough, my game works best on the -opengl option. When I tried the -d3d one graphics were noticeably faster and smoother, but some buildings looked like a smart bomb had blown them up :tongue: textures were crazy and blocked doors and such.

What I want to ask is: what settings can we use to optimize the video, sound, fps, etc. ?

I have a nvidia 6600 and pretty much everything has gone smoothly up until now.
I'm not surprised OpenGL runs better, as Direct3D support in Wine is patchy at best. Other than the Video settings in WoW, there's not much you can do to speed things up, other than overclocking your video card with Coolbits.

---

### Post by Allrab on 2006-09-01
Hi I was trying this guide:

Got this when I went to the Audio tab:

guran@gurans-laptop:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7bf6b5f0 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

The terminal wont respond after this and I have to shut it down.
I wonder what I should do and how to do it.

// Allrab

.edit.
I am soon installing that crappy window$ again as I can handle that one. The problems keep stacking up. I do LOVE Ubuntu and wish to continue using it but the troubbles I get is to big. I need help
All I need is to get World of Warcraft running and Im a happy penguin.

---

### Post by Seryozha on 2006-09-02
worked perfect!  THANKS

---

### Post by Seryozha on 2006-09-02
> **Seryozha said:**
> worked perfect!  THANKS

AHH!:(   I guess i spoke to soon.  It did work perfectly then it installed the patch.  Now i have no sound :(  i go in and edit the Config.wtf and save it then run the game.. no sound.. i check my Config.wtf the buffer line is missing.  i add it back save the file and exit then check the file again to make sure its there... it is.  I run the game.. no sound.  I go bacl to my Config.wtf and the buffer line is gone again.:confused:

---

### Post by eqisow on 2006-09-03
Change the line one more time, then do the following.

```
chmod 555 ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```

That makes your Config,wtf unwriteable, so it won't get changed again. :)

To change it back, replace 555 with 755.

---

### Post by Seryozha on 2006-09-03
> **eqisow said:**
> Change the line one more time, then do the following.

```
chmod 555 ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```

That makes your Config,wtf unwriteable, so it won't get changed again. :)

To change it back, replace 555 with 755.

well it didnt remove the line this time but still no sound :(

---

### Post by Seryozha on 2006-09-03
WOOO HOOOO I got my sound back by running the script found [HERE]("https://help.ubuntu.com/community/WineForAMD64")!!!!

---

### Post by DrunkenSheep on 2006-09-03
ya, low fps, too. And Disconnect after Loading.

ATI Radeon 9800 XT
AMD64 3200+
Asus K8V Se Deluxe
2GB Ram

-opengl just ****** up, blue flashing...
-d3d low fps and disconnect after loading (timeout becuz of the lag, i think)

Winecfg error at clicking on the "Audio" tab -_-

*cry*

---

### Post by Seine on 2006-09-04
Thanks for the guide. I had a brief hiccup, but its working well now with good framerates, latency and sound.

One problem I do have is with keyboard input. If I switch to another desktop and come back again, almost all keyboard input is disabled.

A and D will turn my character left and right as normal, but W and S will not send the character forward and back. Strangely Enter will bring up the chat window, but neither A, D nor any other key will work.

I have followed the thread that creates a panel shortcut that doesn't run in  a terminal, but this has not helped.

Does anybody have any suggestions?

Thanks
Jem

---

### Post by -Race- on 2006-09-04
For this command
cd /home/<wow directory>
   cd WTF
   nano Config.wtf
What do I modify the first line to so that it can show that is in the desktop?
cd /home/Desktop/World of Warcraft/WoW.exe

Is that right or wrong?

---

### Post by TigerCR1200 on 2006-09-05
I am having the flickering screan issue when loading into wow with wine WoW.exe -opengl I found the link below that has a patch for this issue.
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

However I am not real sure how to install it. The only thing I can find on installing it is to manually configure wine. It has been a really long time since I did that so I would like to avoid it but if thats the only way so be it. Any help would be appreicated.

I am getting direct rendering and plenty of FPS in glxgears. 

Thanks,
Tiger

---

### Post by Davidios on 2006-09-05
I have a problem.

I installed WOW with the free drivers and it worked good. BUT, when I moved and changed the zone where I was, there was an strange graphic error with the green letters of the new zone (the name).

Ok, I installed the ATI drivers and the error isn't exist now but it is SLOWER. The camera movement is slow. The free drivers was perfect, except the zone name:( :( :(

I have an ATI 9250

---

### Post by Seryozha on 2006-09-06
> **TigerCR1200 said:**
> I am having the flickering screan issue when loading into wow with wine WoW.exe -opengl I found the link below that has a patch for this issue.
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

However I am not real sure how to install it. The only thing I can find on installing it is to manually configure wine. It has been a really long time since I did that so I would like to avoid it but if thats the only way so be it. Any help would be appreicated.

I am getting direct rendering and plenty of FPS in glxgears. 

Thanks,
Tiger


I think i fixed this by going back to x.19.  You also might try without the -opengl switch.

---

### Post by TigerCR1200 on 2006-09-06
> **Seryozha said:**
> I think i fixed this by going back to x.19.  You also might try without the -opengl switch.
I tried with the D3D option but I get massive graphic artifacts. I will try dropping down to .19 and see what happens.

---

### Post by girkid920 on 2006-09-06
I need help getting WoW to run in Cedega 5.0 



 .... if anyone knows .. e-mail me at [email]dscott@mccanntech.org[/email]

---

### Post by DrunkenSheep on 2006-09-06
Fix for ATI User:
goto your WoW/WTF/ Folder
type:
sudo nano Config.wtf
go to the buttom of the file
type:
SET gxWindow "1"

CTRL + O to save, + X to close.

now run with wine WoW.exe -d3d

Frames are good, but window mode :)

Edit:
SET gxMaximize "1"
Then it's fullscreen :D
(it's allready in the file, just search)

Edit2: works with -opengl, too. No flickering.

---

### Post by girkid920 on 2006-09-06
im running ubuntu dapper drake and i installed cedega ver 5.0 .. i installed WoW .. it installed fine other then the error at the end of the install that ive read up .. means nothing but when i go to play it in cedega nothng happens .. so i try playing it in the terminal and i get this neat error message :
            For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
tid 9173 received signal 11. Raising signal 3
/home/dave/.cedega/.winex_ver/winex-5.1.1/bin/winex3: line 374:  9167 Quit               $SHELL -c "$RUNWINE $FULL_COMMAND_LINE"

    ~any help could be nice ! :D

---

### Post by russianbandit on 2006-09-07
Thanks for all of your help Tokyo.
I used the front page guide of this thread and WoW worked great. Except my FPS is slightly worse than in Windoze, but I can't seem to change the video settings. Like I'm not presented with any other options that everything pretty much maxed out. I want to be able to decrease the resolution from max (1920x1200) to slightly smaller to get better FPS, but I can't. I tried even editing the config.wtf file, but changes in there, just get overwritten. Any ideas?

---

### Post by girkid920 on 2006-09-07
I've been trying to get WoW working under cedega for the past week and finaly gave up on it .. i came across your forum on how to install and play WoW via Wine... I installed Wine ver. 0.9.20, i copyed WoW that was installed on my windows XP hardrive to my ubuntu dapperdrake hardrive ... then i run sudo wine WoW.exe -opengl ... after typing this .. i get the following message :

wine: Unhandled page fault on read access to 0xa7278922 at address 0x7eec4eb0 (thread 0009), starting debugger...

any help !! i would really like to start playing games on my linux box! lol 8)

---

### Post by Allrab on 2006-09-07
Hahaha  Thank you all, Finally got it working. :eek: 

However I am forced to run   wow.exe -d3d
If I run it with the -opengl i get insane flimmers on my screen.
Also I can not have the 3D accelerated button in winecfg activated as that would make WoW hang after a few seconds.
I would like hardware support for my WoW and get rid of that mouspointer showing thrugh. Tips of tweaking greatly accepted.

OpenGL Vendor String: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

direct rendering: yes

---

### Post by tokyovigilante on 2006-09-10
> **Allrab said:**
> Hahaha  Thank you all, Finally got it working. :eek: 

However I am forced to run   wow.exe -d3d
If I run it with the -opengl i get insane flimmers on my screen.
Also I can not have the 3D accelerated button in winecfg activated as that would make WoW hang after a few seconds.
I would like hardware support for my WoW and get rid of that mouspointer showing thrugh. Tips of tweaking greatly accepted.

OpenGL Vendor String: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

direct rendering: yes
Have responded to your PM. As I said there the issues you are having are due to imperfect ATI driver support, tweaking WoW or Wine is unlikely to solve these.

---

### Post by tokyovigilante on 2006-09-10
> **girkid920 said:**
> I've been trying to get WoW working under cedega for the past week and finaly gave up on it .. i came across your forum on how to install and play WoW via Wine... I installed Wine ver. 0.9.20, i copyed WoW that was installed on my windows XP hardrive to my ubuntu dapperdrake hardrive ... then i run sudo wine WoW.exe -opengl ... after typing this .. i get the following message :

wine: Unhandled page fault on read access to 0xa7278922 at address 0x7eec4eb0 (thread 0009), starting debugger...

any help !! i would really like to start playing games on my linux box! lol 8)
Any requests for help MUST be accompanied by the information I requested on the front page, ie DETAILED hardware configuration, what software (Wine, Ubuntu, driver) you are using, and specifics about the error. Otherwise you waste your time posting and I waste my time repeating myself. 

By the way, why are you trying to run WoW as root?

---

### Post by tokyovigilante on 2006-09-10
> **russianbandit said:**
> Thanks for all of your help Tokyo.
I used the front page guide of this thread and WoW worked great. Except my FPS is slightly worse than in Windoze, but I can't seem to change the video settings. Like I'm not presented with any other options that everything pretty much maxed out. I want to be able to decrease the resolution from max (1920x1200) to slightly smaller to get better FPS, but I can't. I tried even editing the config.wtf file, but changes in there, just get overwritten. Any ideas?
That's an odd one. Again post details of your system and configuration.

I remember something about this from older Wine versions. Try running with -d3d and see if it lets you change the options, then switch back to opengl to run the game. 

If you want your changes to Config.wtf to stick, use chmod 555 Config.wtf. This sets it to read only. To get write access back, use 755 instead of 555.

---

### Post by deboring21 on 2006-09-10
Ok, got a problem here.... when I get into winecfg and click on the sound tab, the winecfg menu quits out and I'm just left with my terminal. I think it's defaulted to OSS, but I'm not sure. Any ideas?

---

### Post by russianbandit on 2006-09-11
> **tokyovigilante said:**
> That's an odd one. Again post details of your system and configuration.

I remember something about this from older Wine versions. Try running with -d3d and see if it lets you change the options, then switch back to opengl to run the game. 

If you want your changes to Config.wtf to stick, use chmod 555 Config.wtf. This sets it to read only. To get write access back, use 755 instead of 555.

I'm running on Edgy Knot 2 (with all updates). Nvidia GeForce Go 6800 card, 2GHZ of Ram, 2.0 GHZ Intel Centrino. Could my problem be connected to copying over from the Windows partition (in there my setting is set to 1920x1200). I can't see any graphics (blank black screen and sound) with d3d option. So I can't try to change options like that. I could try to change permissions on the wtf config file, but I read in this post that wine just ignores any changes in config.wtf if it can't rewrite them. Are you able to change the config.wtf fine?

Update: just ran it with d3d option in widowed mode and was able to see everything fine, but still do see any other options for resolution other than 1920x1200. Is it because my desktop resolution set to that?

---

### Post by Mammal on 2006-09-12
So far I've gotten Wow to work, but the FPS is Terrible. Right now I'm working with an 32bit and Radeon x800GT updated drivers. Using Wine 1.19 and opengl. When I try -d3d I get a black screen, but if I type my password in and press enter a couple times I log in and just get an Orange screen. So -OpenGL works fine. I just want to be able to do PVP or any encounter with a lot of people. Hopefully there are some things I can do to tweek my FPS up.

---

### Post by tokyovigilante on 2006-09-12
> **russianbandit said:**
> I'm running on Edgy Knot 2 (with all updates). Nvidia GeForce Go 6800 card, 2GHZ of Ram, 2.0 GHZ Intel Centrino. Could my problem be connected to copying over from the Windows partition (in there my setting is set to 1920x1200). I can't see any graphics (blank black screen and sound) with d3d option. So I can't try to change options like that. I could try to change permissions on the wtf config file, but I read in this post that wine just ignores any changes in config.wtf if it can't rewrite them. Are you able to change the config.wtf fine?

Update: just ran it with d3d option in widowed mode and was able to see everything fine, but still do see any other options for resolution other than 1920x1200. Is it because my desktop resolution set to that?
Hmm, it shouldn't be in theory, but it might be. Do you have other resolutions defined in your xorg.conf? I would try setting your desktop res down and running the game, that might help. 

My experience with Config.WTF is that modifying it how you want then chmod 555ing it (ie readonly) works fine. WoW will overwrite it with impugnity unless you set it read only, but it seems to apply those preferences fine, unless it conflicts with your hardware (ie trying to force pixel shaders on on old hardware).

---

### Post by tokyovigilante on 2006-09-12
> **deboring21 said:**
> Ok, got a problem here.... when I get into winecfg and click on the sound tab, the winecfg menu quits out and I'm just left with my terminal. I think it's defaulted to OSS, but I'm not sure. Any ideas?
More info about your setup would be a good way to start. Wine does default to OSS in my experience, but crashing when selecting the sound tab suggests none of the possible sound systems on your machine are set up correctly, and winecfg can't cope with that. Do you get sound in WoW? Does winecfg give you a specific error?

---

### Post by tokyovigilante on 2006-09-12
> **Mammal said:**
> So far I've gotten Wow to work, but the FPS is Terrible. Right now I'm working with an 32bit and Radeon x800GT updated drivers. Using Wine 1.19 and opengl. When I try -d3d I get a black screen, but if I type my password in and press enter a couple times I log in and just get an Orange screen. So -OpenGL works fine. I just want to be able to do PVP or any encounter with a lot of people. Hopefully there are some things I can do to tweek my FPS up.
Define terrible? Terrible like 20, or terrible like 5? You should be able to achieve reasonable (15-30fps) rates with that hardware, but you certainly won't get Windows-rivalling performance on ATI cards, the drivers just aren't there.

On the other hand if you're getting 5fps it suggests your drivers aren't set up properly. Check glxinfo | grep direct outputs "Yes".

BTW, where can I get Wine 1.19? I thought the latest version was 0.9.20? ;) Seriously, the dev team has been thoroughly reworking Direct3D and OpenGL for the 0.9.21 release, which should be in the next fornight or so, so hold on!

---

### Post by girkid920 on 2006-09-12
im running wine version 0.9.20 and my computer is an amd 800mhz running ubuntu dapperdrake 6.06 ive got 720mhz of ram and a 64bit ati graphics card .. 
  i have WoW installed on a windows hardrive that is located in the same machine as my linux .. so in other words its dual booted with 2 harddrives .. i copyed the WoW from my windows hardrive onto my linux and ran wine WoW.exe -opengl appon doing this i get this error message: 

wine: Unhandled page fault on read access to 0xa7278922 at address 0x7eec4eb0 (thread 0009), starting debugger...

---

### Post by Mammal on 2006-09-12
> **tokyovigilante said:**
> Define terrible? Terrible like 20, or terrible like 5? You should be able to achieve reasonable (15-30fps) rates with that hardware, but you certainly won't get Windows-rivalling performance on ATI cards, the drivers just aren't there.

On the other hand if you're getting 5fps it suggests your drivers aren't set up properly. Check glxinfo | grep direct outputs "Yes".

BTW, where can I get Wine 1.19? I thought the latest version was 0.9.20? ;) Seriously, the dev team has been thoroughly reworking Direct3D and OpenGL for the 0.9.21 release, which should be in the next fornight or so, so hold on!

Terrible like 20fps outside when no one else is around me, and terrible like 10fps inside any city. glxinfo | grep direct output = yes. I've set up the lastest drivers for my video card.

I followed the unbuntu guide [Here]("https://help.ubuntu.com/community/WorldofWarcraft") so I downloaded 1.19 since 1.20 seems not to work for ATI. Lets hope 1.21 is much better.

---

### Post by tokyovigilante on 2006-09-13
> **Mammal said:**
> Terrible like 20fps outside when no one else is around me, and terrible like 10fps inside any city. glxinfo | grep direct output = yes. I've set up the lastest drivers for my video card.

I followed the unbuntu guide [Here]("https://help.ubuntu.com/community/WorldofWarcraft") so I downloaded 1.19 since 1.20 seems not to work for ATI. Lets hope 1.21 is much better.

That pretty much sounds like things are set up correctly,  and the issue is just the poor 3D performance of ATI's Linux drivers. They are getting better, but for most things an equivalent NVIDIA card under Linux gets double the frame rates. 

I know that from my comments throughout this thread I must sound like an NVIDIA salesman, but realistically the choice under Linux is pretty clear with the current driver state.

Check out the [redblog]("http://www.phoronix.com/redblog/?p=home") at phoronix.com, its a good resource for ATI on Linux.

There is some grumbling on the Wine dev lists about 0.9.20 regressions from 0.9.19 in terms of graphics, so ATI users may be better off with 0.9.19 until 21 is out. I really don't know though, I only get details from people who have issues ;)

---

### Post by tokyovigilante on 2006-09-13
> **girkid920 said:**
> im running wine version 0.9.20 and my computer is an amd 800mhz running ubuntu dapperdrake 6.06 ive got 720mhz of ram and a 64bit ati graphics card .. 
  i have WoW installed on a windows hardrive that is located in the same machine as my linux .. so in other words its dual booted with 2 harddrives .. i copyed the WoW from my windows hardrive onto my linux and ran wine WoW.exe -opengl appon doing this i get this error message: 

wine: Unhandled page fault on read access to 0xa7278922 at address 0x7eec4eb0 (thread 0009), starting debugger...
OK, your hardware sounds a little on the low side for WoW, particularly considering you're trying to run it under Linux, which does have a performance penalty compared with Windows.

I still need more information on how your video card drivers are set up, what sound system you're using, and how you went about setting up Wine. Also, what specific model is your ATI card?

General troubleshooting: Try deleting the WTF, WDB and Interface subdirectories from your WoW folder. This will reset WoW to the default configuration (added to guide).

---

### Post by autrui on 2006-09-13
hi,

so ive been running WoW in wine for a while now, since this thread started, but there's still some issues... and i realized that i've been playing a lot more on my windows laptop than on my ubuntu desktop..and the reason, i think, is because of a few relatively minor issues.  but if they're keeping me from playing, then i should get some help to fix them, right?  

i'm gonna include a screenshot, because it says 1000 words.  i saw another thread where someone posted a screenshot with this same issue, but i didnt have the issue at the time, and now i can't, no matter how many searches i do, find it.  maybe someone will remember?  

outside of the obvious problem in the screenshot, there are two issues.

1) WoW often freezes for a split second--maybe 1/2 a second or so--in very specific circumstances: when i change form (100% of the time), and when i target something/someone (50-75% of the time).

2) my mouse pointer shows both the gauntlet-hand-pointing-finger, as normal, but also the little arrow which is normal when not playing WoW.

i hope these are all connected!  if not, i'll take whatever solutions i can gt a la carte.  

thanks!

autrui

---

### Post by Seryozha on 2006-09-14
> **autrui said:**
> hi,

so ive been running WoW in wine for a while now, since this thread started, but there's still some issues... and i realized that i've been playing a lot more on my windows laptop than on my ubuntu desktop..and the reason, i think, is because of a few relatively minor issues.  but if they're keeping me from playing, then i should get some help to fix them, right?  

i'm gonna include a screenshot, because it says 1000 words.  i saw another thread where someone posted a screenshot with this same issue, but i didnt have the issue at the time, and now i can't, no matter how many searches i do, find it.  maybe someone will remember?  

outside of the obvious problem in the screenshot, there are two issues.

1) WoW often freezes for a split second--maybe 1/2 a second or so--in very specific circumstances: when i change form (100% of the time), and when i target something/someone (50-75% of the time).

2) my mouse pointer shows both the gauntlet-hand-pointing-finger, as normal, but also the little arrow which is normal when not playing WoW.

i hope these are all connected!  if not, i'll take whatever solutions i can gt a la carte.  

thanks!

autrui

  I posed the same issue you were having with the grafix in [this thread]("http://www.ubuntuforums.org/showthread.php?t=185557")  I fixed it by following the instructions on the first page of the thread for wow.  there is a special build of wine and also a script u can run to setup wine.  Hope this helps.

---

### Post by autrui on 2006-09-17
> **Seryozha said:**
> I posed the same issue you were having with the grafix in [this thread]("http://www.ubuntuforums.org/showthread.php?t=185557")  I fixed it by following the instructions on the first page of the thread for wow.  there is a special build of wine and also a script u can run to setup wine.  Hope this helps.

i did all that and there's still the grafx problem.  i completely removed wine .9.21, and followed the WoW instructions, and did the sidenet thing.  i fired WoW up, and there was slightly less sound stuttering in the load screen, but all the issues i whined about above were still there.  any ideas?

thanks!

autrui

---

### Post by tokyovigilante on 2006-09-17
> **autrui said:**
> i did all that and there's still the grafx problem.  i completely removed wine .9.21, and followed the WoW instructions, and did the sidenet thing.  i fired WoW up, and there was slightly less sound stuttering in the load screen, but all the issues i whined about above were still there.  any ideas?

thanks!

autrui
I'm thinking about making this an NVIDIA only HOWTO, ATI users just aren't having any fun. ;)

Apparently 0.9.21 broke ATI support for WoW completely. Theres a patch up at the Wine AppDB, but you'd have to build from source to take advantage of that.

AFAIK at the moment the easiest way for ATI users to run with Wine at the moment is to stick with 0.9.20 UNPATCHED and use the -opengl switch. Its slower but more accurate than -d3d. This is why i'm advising people to stick with 0.9.20 for now, although I note eqisow has thrown up 0.9.21 NVIDIA packages on his site, and my 32-bit cross-compile of 0.9.21 is working well.

For the sound setting SoundBufferSize "100" in Config.WTF works for me. I haven't had to set it readonly for this to be picked up by WoW. As for the double cursor bug thats due to the ATI hardware cursor interfering with the WoW cursor, i cant give more specific help than advising you to play around with the ATI and WoW cursor settings until it works.

Sorry to paint a bleak picture, but I don't have ATI hardware or the time at the moment to troubleshoot ATI-specific issues (finals in 6 weeks :S)

---

### Post by tokyovigilante on 2006-09-17
I really would appreciate people on ATI who are successfully running WoW with Wine to let me know about it, particularly experiences with 0.9.21. Have you used the AppDB patch, are you using 64-bit, do you know if there are patched binary packages around, what if any hacks you had to use to get running, fixes for sound/video/mouse bugs etc. 

If you've got anything to contribute to the howto that'd be really useful, post here, or flick me a PM or email.

---

### Post by eqisow on 2006-09-17
Just an fyi, the 0.9.21 I put up on the Wiki has the ATI patch, though I haven't been able to test it myself.

---

### Post by tokyovigilante on 2006-09-17
> **eqisow said:**
> Just an fyi, the 0.9.21 I put up on the Wiki has the ATI patch, though I haven't been able to test it myself.
Great thanks, i'll update the howto. If it doesn't work we'll know soon enough... ;)

---

### Post by cdevilrun on 2006-09-19
Disclaimer: I have spent perhaps 3 hours working on getting WoW up and running in Wine. Obviously I've just started my work on this, but I have some time this evening and I'd really love to get it working. 

I installed the wow specific version of Wine that's floating around the forums. Obviously I've got Dapper. The laptop is on the low end of the reqs for the game, but it should work:

1.6 Ghz Pentium M
512MB Ram
Radeon Mobility 9000

My graphics are shattered on objects, much like Autrui's screenshot above, except for it is every object that deigns to show itself. My realm was down so I was testing in the human starting area. (Proud Hordie myself, hope this doesn't keep me from getting some tips ;-) ) No toons are showing up, though I do get the targeting circle upon mouseover. I'm getting the double cursor, gauntlet and pointer, as well as many missing objects (fences, npcs, vendor carts, etc.) I haven't even attempted sound yet.

Who has had these same issues, and how did you overcome them?

I've heard that 0.9.20 worked better with ATI in OpenGL, so I'm thinking of picking up this package: [http://thepiratecove.org/files/wine-0.9.20_wow_i386.deb](http://thepiratecove.org/files/wine-0.9.20_wow_i386.deb)

What's the word folks?

---

### Post by Shamanix on 2006-09-19
Hi, working fine for me except 2 things:

1. The Sound has sparkling in it, and it's annoying^^.  I use the built-in soundcard in my motherboard (Abit NF7-S 2.0)

2. The cursor is slow and laggy. I'm using Logitech MX510

Could i get a PM with how to fix it?

---

### Post by kick6 on 2006-09-19
I have WoW running on my amd64/nvidia desktop quite well right now, and am struggling to get it working on my amd65/ATI laptop.  The current situation is that WoW.exe runs, but only in d3d.  OpenGL causes an immedate crash, and brings up the WoW "report a problem" dialog.  When the game DOES run (in d3d) it downloads the patch, and then the patcher crashes which brings up a wine debug request dialog.  

I'm going to try to purge wine, and install the latest patched build listed in the wiki.  I'll report back on whats going on so hopefully someone can either learn from successes or help me figure out the failiure.

---

### Post by kick6 on 2006-09-19
results are:  0.9.21 doesn't work, but using the piratescove .20 deb works great.  Apparently the cause is ATI's drivers sucking, but I can't confirm this.

---

### Post by MakLeod on 2006-09-20
WoW has been working fine for me for weeks now, but I just installed Compiz/XGL and now I get an error message saying world of warcraft is unable to start 3d acceleration.  Any ideas on how to fix this?  Thanks.

---

### Post by tokyovigilante on 2006-09-20
> **MakLeod said:**
> WoW has been working fine for me for weeks now, but I just installed Compiz/XGL and now I get an error message saying world of warcraft is unable to start 3d acceleration.  Any ideas on how to fix this?  Thanks.

Remove XGL. The accelerated X server running on top can't spawn other OpenGL apps. This won't work until the get_texture_from_pixmap OpenGL extension is implemented by ATI/NVIDIA, and we can use AIGLX.

---

### Post by tokyovigilante on 2006-09-20
> **kick6 said:**
> results are:  0.9.21 doesn't work, but using the piratescove .20 deb works great.  Apparently the cause is ATI's drivers sucking, but I can't confirm this.
They do ;), but there has been a regression in 0.9.21 for ATI users. There's a patch up on the WoW AppDB page, I'd be interested to know if anyone's tried it.

---

### Post by tokyovigilante on 2006-09-20
> **Shamanix said:**
> Hi, working fine for me except 2 things:

1. The Sound has sparkling in it, and it's annoying^^.  I use the built-in soundcard in my motherboard (Abit NF7-S 2.0)

2. The cursor is slow and laggy. I'm using Logitech MX510

Could i get a PM with how to fix it?
I've answered both these questions multiple times in the thread. You need to use OSS and increase your SoundBufferSize to 100 or greater in Config.wtf, and manipulate your hardware cursor settings.

---

### Post by MakLeod on 2006-09-21
> **tokyovigilante said:**
> Remove XGL. The accelerated X server running on top can't spawn other OpenGL apps. This won't work until the get_texture_from_pixmap OpenGL extension is implemented by ATI/NVIDIA, and we can use AIGLX.

So is there anyway to keep XGL and somehow have an option to boot to my original theme setup?  I'd like to keep Compiz/XGL around and still be able to play WoW.  Thanks.

---

### Post by tokyovigilante on 2006-09-21
> **MakLeod said:**
> So is there anyway to keep XGL and somehow have an option to boot to my original theme setup?  I'd like to keep Compiz/XGL around and still be able to play WoW.  Thanks.

There's a dirty hack floating around the forums that I think kills the accelerated server when you start an OpenGL application, then brings it back up when you exit that will do what you want, but I wouldn't recommend it. 

The whole XGL thing is nice in theory, but without the driver support the implementation is awful. It won't play well with other 3D apps until the drivers support the required extensions. Should be possible with the 9-series NVIDIA drivers which are out soon though.

---

### Post by MakLeod on 2006-09-21
> **tokyovigilante said:**
> There's a dirty hack floating around the forums that I think kills the accelerated server when you start an OpenGL application, then brings it back up when you exit that will do what you want, but I wouldn't recommend it. 

The whole XGL thing is nice in theory, but without the driver support the implementation is awful. It won't play well with other 3D apps until the drivers support the required extensions. Should be possible with the 9-series NVIDIA drivers which are out soon though.

Is there any possible way to boot to the terminal (thus bypassing GNOME completely) and starting WoW?  If that is possible how would I go about booting directly to the terminal?

---

### Post by Ferrat on 2006-09-21
> **tokyovigilante said:**
> They do ;), but there has been a regression in 0.9.21 for ATI users. There's a patch up on the WoW AppDB page, I'd be interested to know if anyone's tried it.

I've tried if works great in OpenGL except in cities and houses, entering crashes the minmap and all text >_< Mega Suxxor =( 

But other than that it works without any problems with OpenGL

With Direct3D everything works but everytime you target a new target you freeze for about 0,5sec and buildings have major Grafic error making it impossible to navigate cities and buildings =/

---

### Post by tokyovigilante on 2006-09-22
> **Ferrat said:**
> I've tried if works great in OpenGL except in cities and houses, entering crashes the minmap and all text >_< Mega Suxxor =( 

But other than that it works without any problems with OpenGL

With Direct3D everything works but everytime you target a new target you freeze for about 0,5sec and buildings have major Grafic error making it impossible to navigate cities and buildings =/
Thanks, that pretty much confirms what I was thinking. Looks like the minimap bug affects ATI too. Are you using the patched .debs from piratecove?

---

### Post by tokyovigilante on 2006-09-22
> **MakLeod said:**
> Is there any possible way to boot to the terminal (thus bypassing GNOME completely) and starting WoW?  If that is possible how would I go about booting directly to the terminal?
No, the accelerated drivers require a running X server. You could run the xserver without a desktop environment, but it's more trouble than its worth without any real performance gains. If you're looking for a more lightweight desktop environment, try Xubuntu (Xfce).

---

### Post by Ferrat on 2006-09-22
> **tokyovigilante said:**
> Thanks, that pretty much confirms what I was thinking. Looks like the minimap bug affects ATI too. Are you using the patched .debs from piratecove?

Im using the one single patch from the wine appDB =) 

PLUS!! =D I found a fix to avoid any grafic errors, just hide minimap before you go in to cities and buildings = no more grafic errors =) wee

---

### Post by Jargon64 on 2006-09-23
I've justed done the whole 0.9.21 from source with all the nVidia fixes and stuff and it runs almost perfectly in opengl except for an unexpected flickering, kind of looks like a refresh rate problem. Anyway, I found this guide and removed my version of wine and installed the prebuilt one from here. Exactly same problem (I guess I compiled my version with exactly same set up as the one here).

Regardless of running in windowed mode or fullscreen, the flickering still persists. D3D is pretty much unplayable, but I don't really like D3D to begin with :). I can see the game underneath the flickering problem and it looks REALLY good and runs really fast... 'tis mocking me :/

As a side note, I can't seem to change my resolution, refresh rate, bit depth in either xorg.conf or Config.wtf. In xorg.conf all the settings are being ignored (and I've run the xorg-server reconfigury thing) and Config.wtf is just reverting back to previous settings (I guess that's the WoW hardware detector thing and xorg is feeding it crap information). I had this inability to change xorg resolution problem in Breezy and I can't remember how I fixed it. It was like xorg was detecting wrong settings and I had to turn it off (think it was something to do with DPMS, but not sure). Running on a Dell Inspiron 5150 with 1400x1050 screen.

Anyway, really hope someone out there knows what the problem is. Really wanna get WoW running on my laptop :) Thanks in advance.

---

### Post by Ferrat on 2006-09-23
> **Jargon64 said:**
> I've justed done the whole 0.9.21 from source with all the nVidia fixes and stuff and it runs almost perfectly in opengl except for an unexpected flickering, kind of looks like a refresh rate problem. Anyway, I found this guide and removed my version of wine and installed the prebuilt one from here. Exactly same problem (I guess I compiled my version with exactly same set up as the one here).

Regardless of running in windowed mode or fullscreen, the flickering still persists. D3D is pretty much unplayable, but I don't really like D3D to begin with :). I can see the game underneath the flickering problem and it looks REALLY good and runs really fast... 'tis mocking me :/

As a side note, I can't seem to change my resolution, refresh rate, bit depth in either xorg.conf or Config.wtf. In xorg.conf all the settings are being ignored (and I've run the xorg-server reconfigury thing) and Config.wtf is just reverting back to previous settings (I guess that's the WoW hardware detector thing and xorg is feeding it crap information). I had this inability to change xorg resolution problem in Breezy and I can't remember how I fixed it. It was like xorg was detecting wrong settings and I had to turn it off (think it was something to do with DPMS, but not sure). Running on a Dell Inspiron 5150 with 1400x1050 screen.

Anyway, really hope someone out there knows what the problem is. Really wanna get WoW running on my laptop :) Thanks in advance.

If you scroll down on the WOW appDB page for wine I belive there is a fix for the flickering and for the resolution ect, when you start and wow says new hardware, just click no? =)

---

### Post by Jargon64 on 2006-09-23
Heh, I totally missed that :) thanks for point that out. At least its an easy uncomplicated fix :)

---

### Post by Ferrat on 2006-09-23
np that's what the forum is for =)

---

### Post by Ramla on 2006-09-28
I was desperately searching for an answer to static low FPS in WoW running in Wine. Couldn't find it in this thread, but google helped. 

Found this page [http://appdb.winehq.com/appview.php?iVersionId=5606]("http://appdb.winehq.com/appview.php?iVersionId=5606") with a very suspicious looking tweak that originally seemed to just fix something. For me (Nvidia user) it doubled my FPS. No kidding. 7fps in Ironforge at it's worst before, 14 after. Scientifically tested.

Also, you are supposed to "wine regedit" and do the modifications there. I didn't have the Wine key in HKEY_LOCAL_MACHINE\Software\ (installed from the .deb linked in the first post) but you can make it yourself.

> Corrupt or Missing Text - here's the fix for ATI cards

If you are suffering from corrupt or missing text you will need to add the DisabledExtensions key to the registry.

Here's how you do it ... 

Find HKEY_LOCAL_MACHINE\Software\Wine\ 

Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder 

Click right on the wine folder and select [NEW] then [KEY] 

Replace the text "New Key #1" with OpenGL 

Click right in the right hand pane and select [NEW] then [String Value] 

Replace "New Value #1" with "DisabledExtensions" 
(Notice it's case sensitive) 

Then double click anywhere on the line, a dialog box will open. In the value field type "GL_ARB_vertex_buffer_object" (without the quotes). 

Here's what regedit should look like once you have finished adding this new key and it's value. 

appdb.winehq.org/appimage.php?iId=3746 


Do you need 100% boost to your FPS ?

Then apply the same DisabledExtensions registry key as described above.

28/Sep/06 NL & JK

---

### Post by kick6 on 2006-09-28
that trick works quite well on my ATI powered laptop.  I hope it works equally as well on my nvidia powered desktop.

---

### Post by tokyovigilante on 2006-09-30
I'm testing Wine 0.9.22 now, if all goes well i'll try and put a .deb up for amd64 at least.

---

### Post by lintila on 2006-10-01
I just wanted to throw out a HUGE thank you for this post!

WoW is currently downloading the humonstorous patch and it is working.

Your directions are awesome. I know a little about linux but not enough to be compiling my own wine and such as other WoW instructions suggest. I always got errors trying to compile wine for amd64.  Thank you for providing links to pre-compiled wine, 

See you in Warsong Gultch!

Lintia

---

### Post by Pablasso on 2006-10-10
wich version of the patched wine should i install for the integrated graphics video of intel? (i just see one from nvidia and one from ati)

or i just install the regular version? :-s

---

### Post by tokyovigilante on 2006-10-10
Try your luck with the standard version, either from winehq.com, or is in the repositories if you're running edgy. If not switch to the patched version. 

I have an patched 0.9.22 .deb available, which is just a checkinstall of my amd64 cross-compile, so should work on amd64 and i386, but it's 11.1mb and I don't have anywhere to host it, so I'm torrenting it out. It's only 128k up so will be slow, but should be up 24/7.

If anyone wants to download and test it feel free, and feel free to mirror it for me, let me know if you do. Let me know if you have any feedback, questions etc. If you're missing dependencies and have to install them, I'd appreciate knowing that too.

[http://www.demonoid.com/files/details/490360/999695/](http://www.demonoid.com/files/details/490360/999695/)

---

### Post by myname on 2006-10-10
Uggg!!!!!

I've tried every possible option that every post has suggested, and WoW hard locks my system with stuttering sound 10 seconds after I enter the world.  

I am using the following to launch WoW "wine WoW.exe -opengl"

I even tried -d3d option and nothing.

I have:
Ubuntu 6.06
Latest version of the following as of 10/10/2006
Wine  (even tried the patched versions)
ATI Drivers
All Ubuntu updates

I can play the cinematic, no problem, I can select a character no problem, but when I enter a world within 10 seconds the sound stutters and my system hard locks.  Any ideas on what's wrong?

I'm fairly new to Ubunut (linux in general), so if you need any info on my system, let me know, and I can get it to you. 

I would really love to get this going, as I have a free weekend coming up and want to play wow the entire weekend.

Is there a tool out there that will monitor the temps of my CPU and video card?

--Kevin

---

### Post by tokyovigilante on 2006-10-10
> **myname said:**
> Uggg!!!!!

I've tried every possible option that every post has suggested, and WoW hard locks my system with stuttering sound 10 seconds after I enter the world.  

I am using the following to launch WoW "wine WoW.exe -opengl"

I even tried -d3d option and nothing.

I have:
Ubuntu 6.06
Latest version of the following as of 10/10/2006
Wine  (even tried the patched versions)
ATI Drivers
All Ubuntu updates

I can play the cinematic, no problem, I can select a character no problem, but when I enter a world within 10 seconds the sound stutters and my system hard locks.  Any ideas on what's wrong?

I'm fairly new to Ubunut (linux in general), so if you need any info on my system, let me know, and I can get it to you. 

I would really love to get this going, as I have a free weekend coming up and want to play wow the entire weekend.

Is there a tool out there that will monitor the temps of my CPU and video card?

--Kevin

Hmm, did you set your sound buffer to 100 and the sound system to "1" (ie OSS) in WTF/Config.wtf, and your sound system to OSS in winecfg as per the howto?

What CPU type, audio card and driver (probably onboard AC97) are you using?

Are you running KDE or Gnome?

As for your temp monitoring, look for lm-sensors in the forums.

---

### Post by Pablasso on 2006-10-10
> **tokyovigilante said:**
> Try your luck with the standard version, either from winehq.com, or is in the repositories if you're running edgy. If not switch to the patched version. 

I have an patched 0.9.22 .deb available, which is just a checkinstall of my amd64 cross-compile, so should work on amd64 and i386, but it's 11.1mb and I don't have anywhere to host it, so I'm torrenting it out. It's only 128k up so will be slow, but should be up 24/7.

If anyone wants to download and test it feel free, and feel free to mirror it for me, let me know if you do. Let me know if you have any feedback, questions etc. If you're missing dependencies and have to install them, I'd appreciate knowing that too.

[http://www.demonoid.com/files/details/490360/999695/](http://www.demonoid.com/files/details/490360/999695/)

i tested the 'standard' version wich i installed with aptitude (0.9.9), all went ok until WoW tried to download the patches, it throws an error and the client never starts to download. and when i try running it with -opengl it just crashes right away.

i haven't tried with your patched wine yet, i'll do it when i get a chance

i have a mirror up for you if you like (the torrent was pretty slow):
[http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb](http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb)

---

### Post by Pablasso on 2006-10-10
nevermind, the patch is downloading now, lets see if it works with that wine :)

---

### Post by Pablasso on 2006-10-11
it works, but with distorted graphics, not very playable

---

### Post by tokyovigilante on 2006-10-11
> **Pablasso said:**
> i tested the 'standard' version wich i installed with aptitude (0.9.9), all went ok until WoW tried to download the patches, it throws an error and the client never starts to download. and when i try running it with -opengl it just crashes right away.

i haven't tried with your patched wine yet, i'll do it when i get a chance

i have a mirror up for you if you like (the torrent was pretty slow):
[http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb](http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb)
Cool, i do like. Thanks for hosting that.

As for your problems with graphics, since you're running Intel integrated, i'd say firstly performance won't be good unless you have a GMA 950, and not great even with that. Distortion is another issue entirely, and I'd suggest sticking with the standard deb from winehq.com if that's the case. 

As i mentioned in the howto, 0.9.9 won't work at all, and you need wine 0.9.16 at least. Edgy has this version but Dapper is stuck with 0.9.9. 

Also, make sure direct rendering is enabled with:

glxinfo | grep direct.

---

### Post by myname on 2006-10-11
> **tokyovigilante said:**
> Hmm, did you set your sound buffer to 100 and the sound system to "1" (ie OSS) in WTF/Config.wtf, and your sound system to OSS in winecfg as per the howto?

What CPU type, audio card and driver (probably onboard AC97) are you using?

Are you running KDE or Gnome?

As for your temp monitoring, look for lm-sensors in the forums.

Here is my system specs:

AMD64 3700+ (non dual core)
2 Gigs memory
ATI Radeon X1600 512 megs Ram
SB Audidgy 2ZS  (default drivers in Gnome)
Gnome
Yes, tried the sound at 150, 100, 50, in the Config.wtf with all the same results.  I also tried the OSS sound system, as well as the ALSA system when I had the non patched Wine installed.  

Question, if I had the soundsystem set to 1 in the Config.wtf, and the ALSA set in Winecfg, would that cause problems, or would the Config.WTF override?

I really want to get this running in Linux, as I would hate to have to install Windows XP to play WoW, then re-install Linux for a dual boot system.

Any help is greatly appreciated.

--Kevin

---

### Post by myname on 2006-10-11
I found a temp solution for the locking up problem that ATI card users are experiencing in WoW.  So far no lockups, where before it would lockup immediately.

---

### Post by dasuberdog on 2006-10-12
Everything seems to work for me until I patch then I seem to download everything unti I get a message saying I do not have enough disk space and need to free up space.

scribble@Scribble:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             8.7G  3.5G  4.8G  42% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  112K  505M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.15-27-k7/volatile
/dev/hda5              65G   57G  8.2G  88% /media/hda5
/dev/hdc              2.9G  2.9G     0 100% /media/cdrom-1
scribble@Scribble:~$

I have world of warcraft installed in hda5 which has 8.2 g available the message is saying i need atleast 1.8g

---

### Post by dasuberdog on 2006-10-12
One more thing....

what exactly does "map /media/cdrom to D:" do in winecfg?

that is the only thing i believe i have not done exactly like this thread.

---

### Post by myname on 2006-10-12
Not sure what that does, but I didn't mess with it to get WoW working.  Thought I would assume that this is something that the Wine "Registry" uses for games that require a CD to play.

---

### Post by dasuberdog on 2006-10-12
I'm running wine 9.22  the newest one

Still getting the hard drive is full message....

I tried

" Installation errors
[edit]
Not Enough Hardrive Space error

If you experience this, you need to open regedit(wine regedit) and change the following values: TEMP value needs to be set to \ instead of f:\ or whatever it's set for yours. TMP also needs to be set to the same value. These settings can located in  .HKEY_CURRENT_USER\Environment

This should fix your problem with it saying not enough hard drive space. It corrected the problem on mine and now it's installing as we speak." 


There was no HKEY_CURRENT_USER\Environment so I created one and created a Temp value and a tmp value.

Now I am getting a message from the installer saying that the installer was unable to start because I don't have enough hard drive space.

weird...

if anyone could help my patience sure would appreciate it.

---

### Post by iiiears on 2006-10-13
This is listed under my nvidia card. 

    Option "RenderAccel" "true" 


Lathrop* see you in Azeroth!

---

### Post by -Race- on 2006-10-17
I installed the latest patch and once I try to open it I get this.
Exception raised
Unhandled page fault on read access to 0x0000000 at adress
0x6092b2ff8
Do you wish to debug it?

With either object the patching progress screen doesnt show. What can I do to get WoW patched and ready to go?

---

### Post by myname on 2006-10-17
I've normally updated WoW with the patches by downloading them from Fileplanet, I've never relied on the WoW client to patch itself, even under windows.

This will be my first patching process since getting WoW to run under Ubuntu, so I guess when I get home, I will be downloading from fileplanet and see what happens.

--kevin

---

### Post by -Race- on 2006-10-17
Same here just its wierd since no window shows. Maybe it just works in the background I"ll let it run then see whats going on.

---

### Post by kkellyc on 2006-10-18
> **dasuberdog said:**
> Everything seems to work for me until I patch then I seem to download everything unti I get a message saying I do not have enough disk space and need to free up space.


I am also having this problem.  I am using the latest WINE version 9.23, hot off the presses, and ubuntu 6.06.  I was able to log in to my account and allow blizzard downloader to do its thing with the patch, but as soon as it tries to apply the patch, i get the message described above.

I have also just gone into the directory where the patch exe was downloaded and run it from there directly by typing "wine patchfilename.exe".  This launches the blizzard updater which then gives a similar error (wants 1.8G, thinks I have 0.0G, etc.).

I have messed with the TEMP and TMP registry keys, setting them to \ rather than the c:\windows\temp that they were set to, though I don't see why they would have anything to do with this.  c:\windows\temp (with c:\ mapped to home\kkellyc\.wine\c_drive) is a valid directory with write permissions.  And changing the keys did nothing, so I put them back the way they were.  Seems other apps might need that temp directory, and \ does not have the same open permissions as the location under home.

Incidentally, these keys were not under the path .HKEY_CURRENT_USER\Environment, but rather under .HKEY_LOCAL_MACHINE\System\CurrentControlSet\control\Session Manager\Environment.

This leads me to believe there has been a change from wine 9.22 to 9.23 that is playing into this problem, rendering the previously successful fix obsolete.  I just don't have enough background in linux or with wine to begin to hone on on a new solution!  I am hoping there are some wine/WoW gurus out there monitoring this thread who are on to this. :-)

Thanks!

---

### Post by dasuberdog on 2006-10-19
> **kkellyc said:**
> I am also having this problem.  I am using the latest WINE version 9.23, hot off the presses, and ubuntu 6.06.  I was able to log in to my account and allow blizzard downloader to do its thing with the patch, but as soon as it tries to apply the patch, i get the message described above.

I have also just gone into the directory where the patch exe was downloaded and run it from there directly by typing "wine patchfilename.exe".  This launches the blizzard updater which then gives a similar error (wants 1.8G, thinks I have 0.0G, etc.).

I have messed with the TEMP and TMP registry keys, setting them to \ rather than the c:\windows\temp that they were set to, though I don't see why they would have anything to do with this.  c:\windows\temp (with c:\ mapped to home\kkellyc\.wine\c_drive) is a valid directory with write permissions.  And changing the keys did nothing, so I put them back the way they were.  Seems other apps might need that temp directory, and \ does not have the same open permissions as the location under home.

Incidentally, these keys were not under the path .HKEY_CURRENT_USER\Environment, but rather under .HKEY_LOCAL_MACHINE\System\CurrentControlSet\control\Session Manager\Environment.

This leads me to believe there has been a change from wine 9.22 to 9.23 that is playing into this problem, rendering the previously successful fix obsolete.  I just don't have enough background in linux or with wine to begin to hone on on a new solution!  I am hoping there are some wine/WoW gurus out there monitoring this thread who are on to this. :-)

Thanks!

I ended up installing an older version of wine then reinstalling Wow.  Now I am getting the same message but initially when I go to install wow from the dvd.

---

### Post by russianbandit on 2006-10-20
I've installed the latest wow wine and it works as usual!

I've got one small complaint: the graphics on Linux do not look as good as on my WinXP partition. I see alot of jaggies especially on diagonal lines in Linux. Almost as if the anti-aliasing was not on. I couldn't find anywhere in the options to set some kind of anti-aliasing config either. So am I just being too picky and ungratful that Linux can run WoW as it is. Or is there a way to optimize my video configs to show smooth graphics?

---

### Post by Scotty562 on 2006-10-21
All I have to say is wow ;). Great guide, everything worked for me the first time through. Frame rates are a bit sketchy but I expected that. With all my settings turned down and next to no addons loaded I was hitting between 20 and 30 fps running around outside and about 10-15 when I even looked at a town. Although, I hit as high as 45 fps inside a bu!ilding.

All in all I'm very please, just have to figure out why the sound isn't working :). Back to searching!

Thanks!

---

### Post by crimson_legion on 2006-10-21
I am having trouble installing becuase I am using .iso's (4 discs) anyone know how to get the installer to read the next disc?

---

### Post by Bonk on 2006-10-21
Everything works fine, I just have no idea where all the files are.

The installer said c:\Program Files\Games\WoW

Sooo, where do I go on here?

---

### Post by hoagie on 2006-10-22
Great guide and great effort to help the comunity. But how can copy my 7 gigabyte wow directory to ubuntu. I don't even have a dvd writer. Any ideas?
](*,)

---

### Post by Juzz on 2006-10-22
> **hoagie said:**
> Great guide and great effort to help the comunity. But how can copy my 7 gigabyte wow directory to ubuntu. I don't even have a dvd writer. Any ideas?
](*,)
From where to where do you need it?
Is it on the same machine, or is it from one machine to the other?

If it is on the same machine - then you 'just' need to mount the partition with the game on it and copy it over.
If it is on two separate machines, then you can share the game directory on the remote machine and copy it over the network.

---

### Post by hoagie on 2006-10-22
It's form the same machine(windows to ubuntu. The two operating systems are on different hard disks.

---

### Post by hoagie on 2006-10-22
Can anyone help me mount my windows hard disk?

---

### Post by dasuberdog on 2006-10-22
I've finally gotten the installer to work again.  

I need to install Wow on my fat32 partition which I want to set up as d: because I do not have enough room on my ubuntu partition.  Will I be able to do this?

If not is there a similar program to partition magic that I can move that empty space over?

---

### Post by dasuberdog on 2006-10-22
I reinstalled wine reinstalled wow and got same problem.  The installer thinks my hard drive is full.  It may be because I am having to install on D: fat 32 partition becuase I have no room on linux partition.  I have messed with the TEMP and TMP registry keys, setting them to \ rather than the c:\windows\temp that they were set to.

Incidentally, these keys were not under the path .HKEY_CURRENT_USER\Environment, but rather under .HKEY_LOCAL_MACHINE\System\CurrentControlSet\contr ol\Session Manager\Environment.

Anyway that just changed the way in which Wow told me that I don't have enough hard drive space.

I give up.  It seems like only a few people are having the same problem and no one knows how to fix it.  I love not having windows but it sure does suck not being able to play games.  It's kind of like having a crippled computer that you will never be able to use to it's full potential.  I guess when I have the money to buy an external drive I can reformat and try installing in the linux partition.

---

### Post by DraeLee on 2006-10-22
I have wow copied on my fat32 partition which is my d:  i am stuck at using the 

wine Installer.exe command  I dont know how to go to the directory for my fat32 any advice on what command I should type  

My folder where it is stored is WoWInstaller and the file is Installer.exe

edit: I figured it out it was in /media/fat32 

so I am installing it now hopefully it will go all the way through ill keep ya posted

---

### Post by Juzz on 2006-10-22
You can just copy it over without having to install it...

---

### Post by Juzz on 2006-10-22
> **hoagie said:**
> Can anyone help me mount my windows hard disk?
Your windows hard disk should be found somewhere under:
```
/media/hdaN
```
Where N is a number (if your windows harddrive is on a normal ATA controller), if it is on a SATA controller the it is named sdaN

---

### Post by DraeLee on 2006-10-22
woot it installed I am downloading the update right now ill keep ya posted

Oh got a question since I got it installed now should i got ahead and delete what i copied on the fat32 because I got both the copied and the installed on that partition and now i dont need the copied so should i delete it?

---

### Post by DraeLee on 2006-10-22
ok got a problem I tried to download the update and it did download but i got an error that said need at least 1.8g of free space drive present has 0.0 

now that makes absolutely no sense since its on a 33g fat32 partition any ideas?

---

### Post by Juzz on 2006-10-22
You can copy over the fully updated version from Windows on top of the version you just installed.
(I also reinstalled on my linux and then copied over the updated version from my windows drive)

---

### Post by DraeLee on 2006-10-22
so what you are saying is that I can copy the full patch and all from windows over the folder in my fat32 for ubuntu and it should work?

---

### Post by Juzz on 2006-10-22
You can copy over the entire World of Warcraft directory and everything should in theory be great...

---

### Post by DraeLee on 2006-10-22
oooooh snap ok then Ill write back when i do that gonna restart into windows since I got to install it there again ill let ya know shortly  hope it works.  It does make since tho

---

### Post by DraeLee on 2006-10-22
Ok got a problem I installed WoW on windows and then updated it. After that I copied the contents from windows over to Fat32 folder.  when i do the command 

wine WoW.exe -opengl it boots up and then when i log in it still says I need to download the updates which I know itsnt right.  And plus even if I did download it apparently the temp file where its held is not where I have wow at on the fat32 partition.  I dont know how to change it so I thought I could bypass it.  But yet it is still asking for it to be updated.  Any help would be appreciated

---

### Post by DraeLee on 2006-10-22
alrighty i got it installed and copied over, problem my fps is sucking reallllly bad the moust moves but its like for every stroke i move the mouse it will move every 5 seconds later any suggestions?

---

### Post by Juzz on 2006-10-23
Dunno if you mentioned it before, but what gfx are you running?

---

### Post by DraeLee on 2006-10-23
nvidia 5200 128mb
using ubuntu 6.06 dapper
amd64 3200+ 
1gig ram
using wine 0.9.23


well i think i fixed the fps thing my refresh rate was wrong.  I have two problems atm one is the flickering and the other is no sound(which is ok atm ill deal with that part)

---

### Post by DraeLee on 2006-10-23
well I fixed the flickering problem, but nnnooowww it keeps crashing on me and produces this err or

ERROR #131 (0x85100083) File Corrupt
Program:	D:\World of Warcraft\WoW.exe
File:	Data\patch.MPQ


as soon as i start to move forward it will crash

---

### Post by Juzz on 2006-10-23
Try and delete your Config.wtf in the WTF dir

---

### Post by dasuberdog on 2006-10-23
DraeLee how did you fix this problem.  I have not been able to get around this exact problem.


QUOTE=DraeLee;1650230]Ok got a problem I installed WoW on windows and then updated it. After that I copied the contents from windows over to Fat32 folder.  when i do the command 

wine WoW.exe -opengl it boots up and then when i log in it still says I need to download the updates which I know itsnt right.  And plus even if I did download it apparently the temp file where its held is not where I have wow at on the fat32 partition.  I dont know how to change it so I thought I could bypass it.  But yet it is still asking for it to be updated.  Any help would be appreciated[/QUOTE]

---

### Post by Juzz on 2006-10-24
Either don't run it in opengl while updating - or copy over from a working windows install (as I wrote to DraeLee)

---

### Post by DraeLee on 2006-10-24
> DraeLee how did you fix this problem. I have not been able to get around this exact problem.

I did this by downloading all of the current updates on windows and then copying it over to my fat32 and it worked beautifully.  Once i fixed the flickering problem it loaded up WoW with no problem.  my only problem now is that as soon as i start to run arond the game crashes and im not sure why

---

### Post by DraeLee on 2006-10-24
Ok I tried deleting the Config.wtf and That didnt work it still kicked me out as soon as i chose my charcter  and went to the screen before im in it kicked me

---

### Post by Juzz on 2006-10-24
Did you run WoW from terminal? If not try it and let us see, what the output from wine is.

---

### Post by DraeLee on 2006-10-24
I did run from terminal as I always do

do you want me to print it here

well unfortunately WoW is doing their updates atm lol so i cant fully log in.  I can get to the login screen and character screen (when available) with no issue at all but as soon as i get to the main screen i get kicked

> fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cf50000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf50000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub


now in there it says something about my audio i wonder if that is why i cant get any audio for WoW?

---

### Post by DraeLee on 2006-10-24
as soon as i click audio the winecfg disappears and I get this error

> ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/draelee/.kde/socket-draelee-desktop.
can't create mcop directory


i dont know how to solve this

---

### Post by chinson on 2006-10-24
I found that Esound works for my world of warcraft. My system is ubuntu dapper.
Just execute "winecfg" and enable Esound as well as OSS disabled.
The other settings are the same as this post.

---

### Post by dasuberdog on 2006-10-24
I tried without open gl and i got the same message about hard drive not having enough space.

---

### Post by DraeLee on 2006-10-24
> I found that Esound works for my world of warcraft. My system is ubuntu dapper.
Just execute "winecfg" and enable Esound as well as OSS disabled.
The other settings are the same as this po

well I would but everytime i click the audio tab winecfg closes.  so i am at a lost for now any ideas?

---

### Post by DraeLee on 2006-10-24
well i tried to log into WoW again and it Froze.  I cant post the full display from the terminal here because it said something about to many smileys.  So I am not sure what I should post, but If anyone has any clue as to how to fix this problem I am all ears.  Thx in advance

---

### Post by DraeLee on 2006-10-24
ok i dont think its anything i did heres why.  I am (trying) playing wow on windows xp (bleh) Now I get a little further in the game but then all of a sudden I get kicked and not once might i add but four times in a row 

so it may not be linux but a patch downloaded from wow or something cause its doing the exact same thing and giving me the same error on windows

---

### Post by DraeLee on 2006-10-24
Woot I got it working lol.  I did a repair on the windows version and then tested it and then i deleted the copy on my fat32 and recopied the corrected WoW folder over and it played fine my fps on a regular is 15 peaked at 26  I still have no sound at all.  Does anyone know how to up the FPS??

also thanks to all that has tried to help me out

---

### Post by tjalve on 2006-10-24
Hi, great guide. I copied over my windows install and edited the Config.wtf as described.

USING OPENGL
=================
[email]zaphod@beeblebrox:~/.wine[/email]/drive_c/WoW$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7deb0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7deb0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eee0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f15c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f654,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f654,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f654,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f654,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f640,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  29 ()
  Serial number of failed request:  493
  Current serial number in output stream:  493


USING D3D
=================
First time I could actually log in and select char but it crashed (WowErorr) while entering world. I then deleted WTF, WTB and Interface folders, re-created Config.wtf with the sound settings and now I get this when I try to run it:

[email]zaphod@beeblebrox:~/.wine[/email]/drive_c/WoW$ wine WoW.exe -d3d
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7deb0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7deb0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eee0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f15c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x184f40) : stub, simulating 64MB for now, returning 64MB left
err:d3d:IWineD3DDeviceImpl_SetRenderState Multisample antialiasing not supported by gl
err:d3d:IWineD3DDeviceImpl_SetRenderState Multisample antialiasing not supported by gl
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x184f40) Unhandled query type 8
fixme:win:EnumDisplayDevicesW ((null),0,0x33f15c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)


My system
==================
AMD X2 3800+
ASRock Dual 939 SATAII (a weirdo of a mobo!)
2GB DDR
Nvidia 6800LE APG (NV42)
Ubuntu 6.10 RC amd64
Beryl / Emerald XGL setup


Any help appreciated :) WoW is the only thing I need windoze for now.

T

---

### Post by chinson on 2006-10-24
> **DraeLee said:**
> well I would but everytime i click the audio tab winecfg closes.  so i am at a lost for now any ideas?

Well, you must ever enable alsa. Go "/usr/lib/wine/" and rename "winearts.drv.so". You should be able to go into Audio in "winecfg" now.

[http://www.winehq.com/pipermail/wine-users/2006-June/022620.html]("http://www.winehq.com/pipermail/wine-users/2006-June/022620.html")

---

### Post by chinson on 2006-10-24
Does anyone else experience a keyboard stick?
The character keeps moving or turnning after I release those "move" key, such like "W,S,A,D,Q,E". I have to re-click it again to stop it.
It isn't always but usually. 

Any suggestion?

---

### Post by DraeLee on 2006-10-24
[QUOTE]Well, you must ever enable alsa. Go "/usr/lib/wine/" and rename "winearts.drv.so". You should be able to go into Audio in "winecfg" now.{/QUOTE]

i dont have that folder in lib any other suggestion

---

### Post by Juzz on 2006-10-25
> **chinson said:**
> Does anyone else experience a keyboard stick?
The character keeps moving or turnning after I release those "move" key, such like "W,S,A,D,Q,E". I have to re-click it again to stop it.
It isn't always but usually. 

Any suggestion?
The keyboard stick happens for me, when I move my mouse out of the window while having a key pressed.

---

### Post by jadugartir on 2006-10-26
Anyone know where i can get the icon for my wow launcher? I want it to be like the original icon. I had one before but i had to reformat! it was a vector graphic, fully resizable icon. If anyone knows how to get it back please, because i forgot where i got it!

Also. My text is all jumbled and its black where the minimap should be! my framerate is great but the interface is pretty messed up. Any way to get it looking like it should? Im running an nvidia 6500 chipset, could it be my drivers?

---

### Post by puppy on 2006-10-26
Well I use this one:
[http://www.my-workstation.com/uploads/Icons/World_of_Warcraft_icon.png](http://www.my-workstation.com/uploads/Icons/World_of_Warcraft_icon.png)

64x64 png file so works rather well...

---

### Post by T3h_Dohtem on 2006-10-26
> **DraeLee said:**
> [QUOTE]Well, you must ever enable alsa. Go "/usr/lib/wine/" and rename "winearts.drv.so". You should be able to go into Audio in "winecfg" now.{/QUOTE]

i dont have that folder in lib any other suggestion

Im having this same problem and I dont have that directory either.

---

### Post by DraeLee on 2006-10-26
does anyone know a way around this cause im at a loss

---

### Post by Juzz on 2006-10-26
Try sudo winecfg first?

---

### Post by jadugartir on 2006-10-26
Thanks for the icon, but im still having problems with my text being all jumbled. Has anyone else had this issue? Its with an nvidia 6500 chipset.

---

### Post by reazn on 2006-10-27
when i install wine, its fine. then i goto install wow.. either by the cd or the files which i've copied to my HD. 

i get this error "Sorry, The Installer was unable to start up. You may be out of hard drive space"

I never actually get to the stage to install wow.. 

help ! :(

edit: not to worry, i figured out what the problem was..

autodetect in winecfg had selected the wrong directory for c: 

why can't they just make the games for linux?! ubuntu - it just works.

---

### Post by dasuberdog on 2006-10-28
I have wow installed and working really well BUT I am getting the flickering problem when I enter buildings.  So I am trying to patch wine using ...

-Download your wine source archive (see the download links above) and save it somwhere. For the
purposes of this explanation I will use /home/[yourlogin]/downloads/wine


> cd /home/[yourlogin]/downloads/wine // change to directory

> tar -xvjf wine-0.9.22.tar.bz2 // extract the source from the archive, this will create the directory
/home/[yourlogin]/downloads/wine/wine-0.9.22

> cd /home/[yourlogin]/downloads/wine/wine-0.9.22 // change to directory

- Download the appropriate "wow-patch" patch depending on which version of Wine you are
installing(see download links above) and copy it to /home/[yourlogin]/downloads/wine/wine-0.9.22/
(Important ! Where you copy the patch is important it should be in the same directory
as the extracted wine-0.9.22)


We are installing wine 0.9.22, so this is the command to use

> patch -p0 < wine-wow-0.9.21.diff for systems with an NVIDIA graphics card, which fixes a flickering problem.

If it complains about not being able to find files makesure you have the patch in the correct directory as
described above and check you have actually unpacked the source... look for the mmap.c file etc..

then compile & link wine as follows ..

I get to this part and I cannot get it to patch....


scribble@Scribble:~/downloads/wine$ dir
wine-0.9.23  wine-0.9.23.tar.bz2
scribble@Scribble:~/downloads/wine$ cd wine-0.9.23
scribble@Scribble:~/downloads/wine/wine-0.9.23$ dir
aclocal.m4    documentation  Make.rules.in
ANNOUNCE      fonts          programs
AUTHORS       include        README
ChangeLog     libs           server
configure     LICENSE        tools
configure.ac  LICENSE.OLD    VERSION
COPYING.LIB   loader         wow_patch_nvidia_flicker_fix_0.9.23.diff
dlls          Makefile.in
scribble@Scribble:~/downloads/wine/wine-0.9.23$ > patch -p0 < wine-wow-0.9.23.diff
bash: wine-wow-0.9.23.diff: No such file or directory
scribble@Scribble:~/downloads/wine/wine-0.9.23$ > patch -p0 < wine-wow_patch_nvidia_flicker_fix_0.9.23.diff
bash: wine-wow_patch_nvidia_flicker_fix_0.9.23.diff: No such file or directory
scribble@Scribble:~/downloads/wine/wine-0.9.23$ > patch -p0 < wine-wow_patch_nvidia_flicker_fix_0.9.23.diff
bash: wine-wow_patch_nvidia_flicker_fix_0.9.23.diff: No such file or directory
scribble@Scribble:~/downloads/wine/wine-0.9.23$


what am i doing wrong????

---

### Post by DraeLee on 2006-10-28
ok maybe i can help with this since i just did it.  First off I didnt do it right the first time either because i didnt do the steps exactly right.  You need to put both files in the same directory for one.  I had both files sitting right next to each other.  I am using the same wine also. 

[http://appdb.winehq.org/appview.php?versionId=4031](http://appdb.winehq.org/appview.php?versionId=4031)

I used the section for compiling to do my compiling and it worked.  I did it exactly the only thing i changed was the name of the patch and wine version used.  Hope it helps.  I did have a lot of problems before I finally did this.  Uninstall wine completely if you got it installed and do the instructions like so  Ill check back to see if everything works.

---

### Post by dasuberdog on 2006-10-28
Woot!!!!  Thanks.  The key seemed to be that the patch file has to be next to the tar file.  Also I changed the directy name that it makes when you unpack it from wine-0.9.23 to just wine.  I believe that may have been just as important because I had the file there once when I tried it earlier.


Thanks again,
scribble

---

### Post by DraeLee on 2006-10-28
cool glad i could help good luck "FOR THE HORDE"

---

### Post by pardu on 2006-10-29
hello to all, first you have done a great job!! with your guide i could install the right ati drivers and so on. but i still can't play wow ](*,) the screen freez after +- 5' and i don't no why. i'm a totaly newbe (thats one of the reasen i suppose..) can anybody help me please?
thx a lot

technical date:
acer notebook 2000series
centrino 1,6ghz
ati mobility radeon 9200  (glxgears -printfps => 2368fps)
xubuntu
wine 9.23

if you need more date i try to finde them ;-)

---

### Post by spacyspacy on 2006-10-30
I have the same problem, I can get into the character screen, then select a char, login. After the laoading screen I can see the world for some seconds with moving people, then the graphics freezes. Music is still playing normally. The mouse is still there and movable (not the 3d-mouse, the normal white one using d3d). And I have to do a hard reboot. The same problem also on wine 0.9.23 and 0.9.22, and using the 8.29 fglrx driver.

Another point is: It seemes to work fine if you don't are in Orgrimmar. WoW was fine when logging in with a char in the middle of Mulgore, only the "Orgrimmar-Chars" have the freezing problem.

Any news about this problem? 

My settings are:
Intel Core2Duo
2GB RAM
Ati X1900 XT 256MB
Ubuntu 6.10
Wine 0.9.24 compiled
fglrx 8.28.8

---

### Post by myname on 2006-11-01
> **tokyovigilante said:**
> **B. Installing Wine.**
64 bit NVIDIA and ATI users:[/B]
 Download and install the patched version:
[http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb](http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb)[]("http://www.demonoid.com/files/details/490360/999695/")
```

sudo dpkg -i  wine_0.9.22-1_amd64.deb
sudo apt-get -f install
winecfg
``` [B]


I just tried to install this file on a Ubuntu edgy64 (fresh/clean) install, and I get a bunch of errors when running winecfg.

any idea on how to get wine installed in Ubuntu Edgy 64?

--Kevin

---

### Post by chinson on 2006-11-06
> **DraeLee said:**
> [QUOTE]Well, you must ever enable alsa. Go "/usr/lib/wine/" and rename "winearts.drv.so". You should be able to go into Audio in "winecfg" now.{/QUOTE]

i dont have that folder in lib any other suggestion

Sorry, I don't know why you don't have it.
I am using ubuntu 6.06 and I do have this folder.
And it did fix my crash problem.

Can you find "winearts.drv.so" in your system?

---

### Post by dasuberdog on 2006-11-07
Downloaded the new restricted drivers and new nvidia driver today and now I am crashing before I even get to the login screen...  Anyone having the same problem?  How do I reverse the driver?

---

### Post by dasuberdog on 2006-11-07
I restarted computer and went back to default settings for wow and seem to now be in business.  Looks like I may have spoken too soon.  :O)

---

### Post by Pablasso on 2006-11-12
anyone knows if this is true?

> Version 0.9.25 of Wine got released. It contains the usual bugfixes and a number of improvements. For players of WoW the most noticeable one is that they won't need special OpenGL patches anymore for running it correctly in OpenGL mode. The game should work correctly out of the box.

[http://www.linux-gamers.net/modules/news/article.php?storyid=1844](http://www.linux-gamers.net/modules/news/article.php?storyid=1844)

i havent tried it yet

---

### Post by douglett on 2006-12-13
> **tokyovigilante said:**
> **B. Installing Wine.**
 
 Latest Version = 0.9.22. The patched .deb in the torrent is patched for NVIDIA and ATI, but untested for ATI as I don't have the hardware, so let me know!

WoW will not work with anything under 0.9.16-18 or so, and it is best to install the latest version for all the bugfixes and performance goodness.

 The method depends on whether you are using 32 or 64 bit.


64 bit NVIDIA and ATI users:[/B]
 Download and install the patched version:
[http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb](http://files.pablasso.com/opensource/wine_0.9.22-1_amd64.deb)[]("http://www.demonoid.com/files/details/490360/999695/")
```

sudo dpkg -i  wine_0.9.22-1_amd64.deb
sudo apt-get -f install
winecfg
``` [B]

Finally...[/B]
 If winecfg pops up, hurray! Check you have version 0.9.20/21 installed. Change the sound output system to OSS, map /media/cdrom to D: and proceed to part C. If not, check back to see you haven't missed anything, and repeat the above steps. If still nothing, post SPECIFIC info about your system, steps taken, output of ```
glxinfo | grep direct
```, and ```
cat /etc/X11/xorg.conf
```I'd like to hear any torrent problems/feedback you have as well (other than it's slow, I know ;) - it's my first one.

Thanks very much pablasso for hosting the build.

I did exactly as was listed above to no avail.  For some reason it's not acknowledging that winecfg exists.

Here's what I get in the command prompt.

```

ouglett@Cornelius:/usr/local/bin$ winecfg
exec: 29: /usr/local/bin/wine: not found
douglett@Cornelius:/usr/local/bin$ cd /usr/local/bin
douglett@Cornelius:/usr/local/bin$ ls wine*
wine         winebuild    winecpp   winefile  wine-kthread  winemine          wine-preloader  wineshelllink
wineboot     winecfg      winedbg   wineg++   winelauncher  winepath          wine-pthread
winebrowser  wineconsole  winedump  winegcc   winemaker     wineprefixcreate  wineserver
douglett@Cornelius:/usr/local/bin$ ./winecfg
exec: 29: /usr/local/bin/wine: not found

```

I'm running an AMD 3800+ X2, geforce FX7300 PCI-E, with plenty of ram and hd space, Edgy (6.10) AMD64 version.  Should I just use the 6.06 x386 version?  I've been monkeying around with this for about 11 hours straight now with no luck.  Although I think I may have installed my video drivers twice on a previous install since glxgears wasn't working before.  It works now, I get around 1450fps.

---

### Post by kannz on 2007-01-07
when i do the command to install wow wine /media/cdrom/Installer.exe it says sorry but the installer wasnt able to start up. you may be out of harddrive space. did i mess something up? you have an awsome howto by the way ^^ helped me alot up untill i got stuck with this.

---

