---
title: "Supertuxkart 0.7b problem"
date: 2011-05-03
forum: Gaming &amp; Leisure
---

### Post by maverick555 on 2011-05-03
amit@Maverick:~$ supertuxkart
Irrlicht Engine version 1.8.0-alpha
Linux 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
Could not load sprite bank because the file does not exist: #DefaultFont
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart/'
Env var LANG = 'en_IN'
[IrrDriver] Creating NULL device
Irrlicht Engine version 1.8.0-alpha
Linux 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
Could not load sprite bank because the file does not exist: #DefaultFont
[IrrDriver] Trying OpenGL rendering.
[IrrDriver] Trying to create device with 32 bits
[IrrDriver Temp Logger] Level 3: Could not load sprite bank because the file does not exist: #DefaultFont
[Irrlicht Error] FBO has one or several incomplete image attachments
[Irrlicht Error] FBO error
supertuxkart: COpenGLTexture.cpp:888: bool irr::video::checkFBOStatus(irr::video::COpenGLDriver*): Assertion `!(true)' failed.
Aborted
amit@Maverick:~$ 


I could not able to start the game it starts just fine then when i select game its just crashes.I tried with low resolution and low graphics,still no loading.Please help !!

---

### Post by Arthur_D on 2011-05-04
Apparently you lack FBO support in your video driver, which is used in the "Select kart" screen which comes right after pressing 'Race'.

What graphics card do you have, and what driver do you use for it?

---

### Post by maverick555 on 2011-05-04
The graphics card is Intel graphics controller 82865g.I think its on board graphics,the drivers are installed automatically.The earlier versions use to play perfectly though.

---

### Post by Arthur_D on 2011-05-05
You say older versions worked. Does that include 0.7?

As a (hopefully) temporary workaround, you should be able to start races from the terminal. For example:
```
supertuxkart -N -t lighthouse --laps 5 --numkarts 20 --kart tux
```
You do not need all of these, since otherwise it will just use defaults.
For a list of possible commands, use 'supertuxkart -h'.

I'll ask the devs if we can solve this in a better way though, since it really is not a viable long-term solution.

---

### Post by danjjl on 2011-05-05
I also get this error : 
[FONT=Courier New] [IrrDriver Temp Logger] Level 3: Could not load sprite bank because the file does not exist: #DefaultFont

[FONT=Verdana]When I play the game elements of the scenery and player position (top left part of the screen) get all pixelized, once this happens more and more elements of the game become pixelized (eg. menu, nitro, ..)

It doesn't happen when the game loads but after playing for a while (usually before the end of the first race).

Is it a consequence of the above error?

@[/FONT][/FONT][FONT=Verdana]maverick555 : do you also get this problem?[/FONT]

---

### Post by Arthur_D on 2011-05-05
@danjjl: That error is not harmful and is expected. However, the video rendering problems you mention aren't (of course). Very weird behavior. I'll ask the programmers about this, though it would probably be best if you reported it yourself, either through the [SuperTuxKart forums]("http://supertuxkart.net/forum") or in our [bug tracker]("http://sourceforge.net/apps/trac/supertuxkart/report").

---

### Post by maverick555 on 2011-05-05
> **danjjl said:**
> I also get this error : 
[FONT=Courier New] [IrrDriver Temp Logger] Level 3: Could not load sprite bank because the file does not exist: #DefaultFont

[FONT=Verdana]When I play the game elements of the scenery and player position (top left part of the screen) get all pixelized, once this happens more and more elements of the game become pixelized (eg. menu, nitro, ..)

It doesn't happen when the game loads but after playing for a while (usually before the end of the first race).

Is it a consequence of the above error?

@[/FONT][/FONT][FONT=Verdana]maverick555 : do you also get this problem?[/FONT]

Yes as you can see in my post this exact same error.

---

