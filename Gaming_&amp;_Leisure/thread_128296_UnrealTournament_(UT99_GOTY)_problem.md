---
title: "UnrealTournament (UT99 GOTY) problem"
date: 2006-02-11
forum: Gaming &amp; Leisure
---

### Post by FitzChivalry on 2006-02-11
Okay, I've installed UT fine, extracted maps etc... Using the software rendered (on lappy with an Intel 8588 adapter, so I'm not sure how well OpenGL would work)...

The problem I have now is UT still won't load. I type 'ut' and the following gets outputted:

```
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
appError called:
fread failed: BufferCount=-3240855 Error=1
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down
```

What would be the cause of this? :S

Any help would be most appreciated

---

### Post by handy on 2006-02-11
Re;  the openGL issue: 

What output do you get when you run the following in a terminal:

glxgears -printfps

Could you post 6 lines of the terminal output?

It's not a true benchmark, but it is a readily used indicator.

---

### Post by FitzChivalry on 2006-02-11
Oki, heres the results:

```
william@gallifrey:~$ glxgears -printfps
3475 frames in 5.0 seconds = 694.814 FPS
3403 frames in 5.0 seconds = 680.544 FPS
3351 frames in 5.0 seconds = 669.008 FPS
3401 frames in 5.0 seconds = 680.076 FPS
3394 frames in 5.0 seconds = 678.471 FPS
3393 frames in 5.0 seconds = 678.481 FPS
```

---

### Post by handy on 2006-02-11
Hi thanks, 

look I think that you ***should*** be able to play openGL games with those numbers...

I would expect less than half in **fps** figures than what you have there, if you didn't have some form of 3d drivers installed for your card/gpu.

Which is all I can really help you with, I'm sorry.  Hopefully this post will bumb up your thread, & someone more knowledgable than me will interpret your error.  

Which is not easy by the way!
It looks like **Botpack.u** can't be found, or is broken, to me?

If no one helps you soon enough, you could try re-installing?

Good luck, I'll keep my eye on this one as time goes by...

---

### Post by happyponcho42 on 2006-02-11
For UT99 based game servers, appError and fread usually link to a bad configuration file, or can be fixed with a reinstall.  Try completely removing your UT install and starting from scratch.

---

### Post by obx-jdt on 2006-02-11
[QUOTE=FitzChivalry]Oki, heres the results:

```
william@gallifrey:~$ glxgears -printfps
3475 frames in 5.0 seconds = 694.814 FPS
3403 frames in 5.0 seconds = 680.544 FPS
3351 frames in 5.0 seconds = 669.008 FPS
3401 frames in 5.0 seconds = 680.076 FPS
3394 frames in 5.0 seconds = 678.471 FPS
3393 frames in 5.0 seconds = 678.481 FPS
```[/QUOTE]
what card are you running?
I get ```
6367 frames in 5.0 seconds = 1273.364 FPS
6315 frames in 5.0 seconds = 1262.834 FPS
6078 frames in 5.0 seconds = 1215.578 FPS
16028 frames in 5.0 seconds = 3205.470 FPS
18895 frames in 5.0 seconds = 3778.842 FPS
18982 frames in 5.0 seconds = 3795.998 FPS
18927 frames in 5.0 seconds = 3785.272 FPS
18681 frames in 5.0 seconds = 3736.192 FPS
14500 frames in 5.0 seconds = 2899.976 FPS
17777 frames in 5.0 seconds = 3555.121 FPS

``` on a Nvidia MX4000 (64bit 128 DDR)
do you know what chipset it is? I agree, install the GL driver

---

### Post by handy on 2006-02-11
I only got between 200 & less than 300, before I installed the nVidia drivers for my card.

Now its about 13000 fps.

That's why I think that there may be openGL support allready!

I could be wrong of course...:rolleyes:

From experience intel don't make very good graphics card.

---

### Post by FitzChivalry on 2006-02-12
BotPack.u is indeed there, I think after reading about that BotPack.u on UT GOTY with linux sometimes does go wrong apparently :|

As for OpenGL, I'll have a look at installing the drivers.

I don't think anything is wrong with the UT.ini, its the one off the CD, I haven't changed anything except the drivers from GL -> Software and now back to GL

You're right handy, Intel *don't* make good graphics cards... but this is on a laptop so I'm a bit stuck for choice heh :(

---

### Post by intentsly on 2006-07-01
Hi,
I b noob :) <- just a little short hand
Anyway, I'm not sure what to do with the loki installer for the goty edition.
I'm using kubuntu x64, and I have only the Windows Goty CD.
Is there any threads that may contain clues?  For I'm lacking them :)
Thank you!

Larry

---

### Post by deathbyswiftwind on 2006-07-01
While I dont know why your having errors I do know it does work under ubuntu. One problem is though it does die out after approx 20 mins on my computer. It doesnt leave an error message in the terminal either it just closes out

---

