---
title: "Choppy video and sound with emulators in Edgy"
date: 2006-11-08
forum: Gaming &amp; Leisure
---

### Post by me1on on 2006-11-08
I've been having a strange problem ever since I upgraded from Dapper to Edgy. The video and sound in emulators is really choppy. This happens with gfceu, zsnes, gens, and visualboy advance (although visualboy advance had problems with Dapper also). I didn't have this problem with Dapper- all my emulators ran smoothly. Is there any way to fix this? I don't have any problems with SuperTux, Battle for Wesnoth, Gnuboy, or any of my other games. It might have something to do with sdl or opengl; I'm not sure. Also, some emulators are more affected than others (for example, gfceu is only slightly choppy but gens is extremely choppy). Any help would be appreciated! :)

On a side note, my right "alt" key isn't working. Any ideas?

---

### Post by hikaricore on 2006-11-08
Check the output of:

```
glxinfo | grep rendering
```

See if it says yes.

Just to be sure..  Alot of your native games might work seemingly perfect using indirect rendering if you have a good enough system.  But emulators tend to be very graphic/hardware demanding which would completely kill your system so to speak.

Also if you upgraded and were using nvidia drivers or anything of that sort you may need to reinstall them to get your system up to full speed, I know most drivers are kernel specific and with a new system kernel via upgrade they may not be loading or just loading and not working.  :)

---

### Post by me1on on 2006-11-08
Thanks for the quick reply. Here's the output of glxinfo | grep rendering:
```
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

```

I haven't installed any video card drivers on either Dapper or Edgy.

---

### Post by hikaricore on 2006-11-08
Ok it was just a quick thought.  Do you have a video card that would require any drivers?

Also since you upgraded you may want to try reinstalling emulators.  Or if all else fails, compile them yourself.  Since package libraries have majorly changed in edgy from dapper, this could be causing issues with applications built dependant on the previous libraries.

---

### Post by me1on on 2006-11-08
> **hikaricore said:**
> Ok it was just a quick thought.  Do you have a video card that would require any drivers?
I don't think so, it's just an onboard video card. Running lspci gives me:
```
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)
``` 
> **hikaricore said:**
> Also since you upgraded you may want to try reinstalling emulators.  Or if all else fails, compile them yourself.  Since package libraries have majorly changed in edgy from dapper, this could be causing issues with applications built dependant on the previous libraries.
Sorry I should have been more specific, I did a complete reinstall instead of an upgrade. I'll try compiling one of the emulators from source to see if that helps, though. Thanks for your help!

Edit: compiling didn't help :(

Edit: I think I'm getting somewhere. By enabling opengl video mode on zsnes, everything works perfectly. I'll see if there are similar options for the other emulators.

Edit: Got GFCEU working perfectly with opengl. Unfortunately, I can't get Gens to work yet. Enabling opengl makes the game screen go white then a couple seconds later it freezes my computer. I guess I'll try compiling gens myself and see how that works.

---

### Post by hikaricore on 2006-11-09
> **me1on said:**
> I don't think so, it's just an onboard video card. Running lspci gives me:
```
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)
``` 

Sorry I should have been more specific, I did a complete reinstall instead of an upgrade. I'll try compiling one of the emulators from source to see if that helps, though. Thanks for your help!

Edit: compiling didn't help :(

Edit: I think I'm getting somewhere. By enabling opengl video mode on zsnes, everything works perfectly. I'll see if there are similar options for the other emulators.

Edit: Got GFCEU working perfectly with opengl. Unfortunately, I can't get Gens to work yet. Enabling opengl makes the game screen go white then a couple seconds later it freezes my computer. I guess I'll try compiling gens myself and see how that works.

Good to hear you made some progress, opengl slipped my mind lol I wasn't quite awake last night.  :)

Good luck with gens.

--Aaron

---

### Post by me1on on 2006-11-15
Thanks hikaricore for helping me with my video issues. Unfortunately I just realized that even though the video is smooth the sound is still bad. It makes a crackling sound with every emulator I have. :( Does anybody else have this problem or know how to fix it?

---

### Post by po0f on 2006-11-15
Just a me too.  I've noticed that there is static when playing zsnes under Ubuntu, Debian and Gentoo have no problems.  Sound card in question: SB Live! 24-bit.

---

### Post by TrueJk7 on 2006-11-20
Hey me1on, how did you enable the OpenGL for ZSNES? I've looked through the command line options and in the gui. Kinda lost. Any hint?

Thanks

Edit. Nevermind I found it out. Still didnt fix the issue though

---

