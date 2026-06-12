---
title: "Problem with sound in Gens"
date: 2006-08-02
forum: Gaming &amp; Leisure
---

### Post by zcal on 2006-08-02
Hey folks,
So I've installed Gens via one of those guides floating around out there.  Anyway, it works great but for one thing.  There is a sound delay problem.  That is, once an action has occurred onscreen, the sound for that action happens about a second afterwards.  Has anyone else had this problem, and if so, do you know how to fix it?  Or, does anyone have any suggestions as to what could be going wrong?  I've fiddled as much as I can with the emulator's settings, so I'm guessing it must be another issue. :-k

---

### Post by zcal on 2006-11-04
I've recently installed Frozen Bubble 2.0 and I'm getting the same problem with the game that I get with Gens: sound delay.  I'm of the understanding that both of these apps use the SDL libraries, so I'm wondering if the problem could be stemming from that.

Also, I just installed a forum member's precompiled Gens package [HERE]("http://www.ubuntuforums.org/showthread.php?t=290008&highlight=gens"), used the OpenGL graphic setting, and I still have the delay problem.  Anybody know anything about this?

---

### Post by Tommerz on 2006-11-07
I've got the exact same problem also, and have had on several installs :( the package is great (should be in dapper backports and/or multiverse) but sadly playing Sonic with lagged sound sucks big fish.

Anyone got any ideas what the problem is?

---

### Post by mustang on 2006-12-10
I'm getting a sound delay as well. Nothing too major but slightly annoying.

Using a chaintech av-710 w/ALSA.

---

### Post by jpeddicord on 2006-12-16
Found a solution, as I was also getting these delays as well.

Install the "libsdl1.2debian-all" package. It will remove the -alsa version, but it fixes the lag problem. :)

Set the display in Gens to OpenGL, and set the sound rate to 44100. Tada!

---

### Post by zcal on 2006-12-16
> **jacobmp92 said:**
> Found a solution, as I was also getting these delays as well.

Install the "libsdl1.2debian-all" package. It will remove the -alsa version, but it fixes the lag problem. :)

Set the display in Gens to OpenGL, and set the sound rate to 44100. Tada!

The weird thing is that I had discovered this solution before, only it broke the sound in Flash, and I wasn't willing to give that up.  The sound in Gens, Frozen Bubble, and Flash all seem to be working fine now though...well that's a problem solved for me.

Thanks for posting this solution.  I hadn't actually bothered with Gens for a while now and so haven't even been thinking about the problem (except when I play the odd game of Frozen Bubble).

---

### Post by MikeReiner on 2006-12-24
Hate to bump this, but i've used the suggested solution and it didn't work for me... 

This applies to more than just gens for me though, Diablo2, Quake4, and Unreal Tournament99,

There are no sound delays in UT2004 (native client) and quake3 under wine. 

Is there anything else that can be done?

---

### Post by zcal on 2007-01-11
I've just installed a fresh Dapper, and the problem has resurfaced.  Even though I have the libsdl1.2debian-all package installed, the sound is still laggy in Gens.  I'm trying to work through what I might have done differently with my previous install.  I'm sure it's something I modified in my xorg.conf...

---

### Post by InGunsWeTrust on 2008-01-14
I hate to nag but per chance is that gens package available in 64 bit? it crashes trying to run it on 64 bit with the --force-architechture switch

---

### Post by zcal on 2008-01-15
I'm not sure...haven't had the need for a 64-bit package myself.  You'll want to poke around in [the package's thread]("http://ubuntuforums.org/showthread.php?t=290008&highlight=gens") to get some real answers, though.

---

### Post by jukingeo on 2008-06-12
I have a similar problem with GENS.

I DO have sound, but it is severely choppy and distorted.  Changing the settings within Gens doesn't help.  It does affect the choppiness by making it slightly better or much worse, but I cannot get it clear.

I am hoping someone can help me get the sound going correctly.

Thank You.

Geo

---

### Post by zcal on 2008-06-12
Are you running it with software rendering or OpenGL?

---

### Post by jukingeo on 2008-06-12
> **zcal said:**
> Are you running it with software rendering or OpenGL?

I am not sure.  How would I figure that out?

I know there are a bunch of settings in Gens that allow you to alter the way the audio plays back, but nothing seems to work right, no matter what I do.

---

### Post by acoustibop on 2008-06-13
See if Graphic -> OpenGL is ticked, jukingeo.

---

### Post by jukingeo on 2008-06-13
> **acoustibop said:**
> See if Graphic -> OpenGL is ticked, jukingeo.

Ok, I found it and it wasn't ticked, so I checked it off.

Now the game is doing something really weird.

With the audio enable on the game plays at super fast at like 100mph, but no sound.  

If I uncheck "sound enable" the screen speed goes back to normal, no sound.

So it seems like I am back to square one.   I don't know why Gens is so stubborn with the sound.  I just about managed to get any other emulator to work.

Geo

---

### Post by zcal on 2008-06-13
jukingeo,
I'd guess that you fiddled something up when you were playing with your audio settings before.  I'm not sure what setting it could be (I don't currently have Gens installed and haven't used it in a while), so I'm not sure what to tell you to try to change.

That said, I'd suggest simply deleting the .gens folder in your home directory.  Don't worry, the next time you run the emulator it will create a new folder for your configurations.  Just be sure to backup any saved game files that are in the folder before deleting it!  Then, when you run the emulator again, turn on OpenGL rendering without doing anything to the audio settings.  I suspect that will solve your problem.

---

### Post by jukingeo on 2008-06-13
[QUOTE=zcal;5179221]jukingeo,
I'd guess that you fiddled something up when you were playing with your audio settings before.  I'm not sure what setting it could be (I don't currently have Gens installed and haven't used it in a while), so I'm not sure what to tell you to try to change.

That said, I'd suggest simply deleting the .gens folder in your home directory.  Don't worry, the next time you run the emulator it will create a new folder for your configurations.  Just be sure to backup any saved game files that are in the folder before deleting it!  Then, when you run the emulator again, turn on OpenGL rendering without doing anything to the audio settings.  I suspect that will solve your problem.[/Q

Doesn't the game have to be properly uninstalled?  Wouldn't just deleting it cause problems with reinstallation?

---

### Post by zcal on 2008-06-14
jukingeo,
By "the game," I'm assuming you're talking about the emulator.  Deleting the .gens folder in your home directory does not affect your installation, it only affects the configurations that you've done with the emulator and the games you've saved, screenshots, etc.  That is, you don't need to worry about reinstalling because you're just trashing config files, not the application itself.

---

### Post by acoustibop on 2008-06-14
In fact, you should only need to delete the actual configuration file, gens.cfg, jukingeo.

---

### Post by zcal on 2008-06-14
> **acoustibop said:**
> In fact, you should only need to delete the actual configuration file, gens.cfg, jukingeo.

Good call.  What am I thinking?

---

### Post by jukingeo on 2008-06-14
> **zcal said:**
> jukingeo,
By "the game," I'm assuming you're talking about the emulator.  Deleting the .gens folder in your home directory does not affect your installation, it only affects the configurations that you've done with the emulator and the games you've saved, screenshots, etc.  That is, you don't need to worry about reinstalling because you're just trashing config files, not the application itself.

Oh, OK.  I have the saved games in a separate folder anyway.

At any rate, I was trying to fix another problem with my sound and streaming audio on the internet...unfortunately that procedure whacked my sound out completely, no I have no sound at all.  So I am back to square one.

I figured upgrading to Ubuntu Studio would help in that aspect (since that is what I wanted to do anyway), but it didn't fix the problem.  Ubuntu Studio looks really really NICE though.  I can't wait to get the sound going so I can try some of the cool programs out that came with it.

Geo

---

### Post by jukingeo on 2008-06-14
> **acoustibop said:**
> In fact, you should only need to delete the actual configuration file, gens.cfg, jukingeo.

That is it?  So the whole program isn't corrupt?  Would it be safer just to delete it and re-download it?

Anyway, as I said in another reply, my sound is knocked out altogether and I have to fix that problem first and then come back here.

Thanx,

Geo

---

### Post by clarkec321 on 2008-07-29
My graphics and sound seem to be fine... I can't get my ps3 joypad working via USB, (my laptop doesn't have bluetooth)

Can someone please point me in the right direction

---

### Post by jukingeo on 2008-07-29
> **clarkec321 said:**
> My graphics and sound seem to be fine... I can't get my ps3 joypad working via USB, (my laptop doesn't have bluetooth)

Can someone please point me in the right direction


This thread discusses sound problems with GENS.  Your post will probably get lost in here.  I would do a search for USB-PS3 Joypad and if nothing conclusive comes up, create your own main post, this way it would come up if someone does a title search.

---

### Post by gimmerealroot on 2008-08-07
After you've fixed the sound problem and have system sound back->

Once you've copied your ~/.gens/gens.cfg to, say, ~/.gens/gens.cfg.old, just start the program via command line again by typing....duh,.....gens  :D

This recreates the gens.cfg file.  Fixed it for me.

---

### Post by Mmmbopdowedop on 2008-12-14
Just found this thread via google whilst looking for a solution, but then found one of my own.

I've had many problems with Pulseaudio, with Wine, FireFox and several other applications. Usually closing the Pulseaudio process solves alot of my problems, as it did with this. Sound worked perfectly in Gens after closing the process. 

Just thought I would put this here incase anybody else finds this thread as I did and hope it helps.

---

