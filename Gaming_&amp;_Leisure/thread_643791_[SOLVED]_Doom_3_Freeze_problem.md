---
title: "[SOLVED] Doom 3 Freeze problem"
date: 2007-12-18
forum: Gaming &amp; Leisure
---

### Post by steelklvr on 2007-12-18
Hi,

I have just installed Doom3 and it loads, but when i actually start the game (as in just after selecting  the difficulty mode) a planet spins forward and then i get a prompt window with nothing in it and my system will then freeze with no errors and i have to reboot.

My video card is an nVidia 6800 XT with driver version 100.14.19, if that helps.

I've looked in all of the threads here and spent an hour or so looking on google for an answer and have yet to find one.

Any assistance would be appreciated.

---

### Post by graspit on 2007-12-18
maybe you should reinstal your operating system.
If the problem persists then maybe you better change your graphic card.

---

### Post by steelklvr on 2007-12-18
ok i have more information regarding the problem.

Errors include:

```
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
WARNING: Unknown string id #str_07187
WARNING: Unknown string id #str_07187

```

and

```
WARNING: Unknown string id #str_07202

```

Reinstalling my operating system seems like a Windows fix and i'm sure there's a way around this.

Also, I have Enemy Territory: Quake Wars installed and running perfectly on this same machine.

Thanks for the suggestion though.

---

### Post by ahaslam on 2007-12-19
> i get a prompt window with nothing in it
That prompt should be requesting your key. Try making ~/.doom3/base/doomkey - it should look like:
```
1ST16CHARACTERSOFKEY
// Do not give this file to ANYONE.
// id Software and Activision will NOT ask you to send this file to them.

```

What version of the client are you using & have you tried using oss (./doom3 +set s_driver oss)?
If you're not using the latest version (1.3.1.1304), I recommend installing it as user somewhere within your home directory.

;)

---

### Post by steelklvr on 2007-12-19
i have the 1.3.1.1304 version of the linux client from the zerowing servers.

setting that oss parameter brings up a few more messages in the terminal but no further progress in game.

i got my version of doom3 from steam :( and the cd key prompt asks for a 16+2 character key. The doomkey and d3xpkey files from steam have the 16characters but not the extra 2 to have a valid cd key to play the game.

Moving pak000.pk4 to the ~/.doom3 folder gets around this but then i get the problem that i described above.

Also when i try to launch Doom3:RoE i get an error where about a missing parameter "netfiring".

Alll of this works fine on windows and i think the steam key is the main problem, don't know why the key is missing the last two characters...

---

### Post by ahaslam on 2007-12-19
> i got my version of doom3 from steam and the cd key prompt asks for a 16+2 character key. The doomkey and d3xpkey files from steam have the 16characters but not the extra 2 to have a valid cd key to play the game.
You don't need the last 2 characters if you create a (doom/xp)key as above (if you've got ROE, you'll need both). 
> Moving pak000.pk4 to the ~/.doom3 folder gets around this but then i get the problem that i described above.
You shouldn't have any .pk4's in ~/.doom3 it's meant for individual user settings. That file should be in /path/to/doom3/d3xp/

Check that the md5sums match those published in /path/to/doom3/README & if you've not installed as user, within your home dir, do so.

;)

---

### Post by steelklvr on 2007-12-20
Excellent, that got everything working properly!

Thanks for your help.

---

