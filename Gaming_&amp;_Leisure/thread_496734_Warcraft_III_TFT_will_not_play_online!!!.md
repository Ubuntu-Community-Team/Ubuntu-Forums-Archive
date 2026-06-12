---
title: "Warcraft III: TFT will not play online!!!"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by FRuMMaGe on 2007-07-09
I've managed to get Warcraft III TFT to install and play perfectly.  However, I cannot play online.

When I logon to my Battlenet account (I have the original game) I am able to browse games and even create my own.  However, as soon as the match starts, my entire laptop freezes, with nothing to do but hold the power button till it turns off.

Basically, I can see all my starting characters, but then the games freezes.  The sound is still playing but nothing else works.

I read on the Wine site that you have to make sure port 6112 is open, how do I do this?

---

### Post by FRuMMaGe on 2007-07-11
bump

---

### Post by frodon on 2007-07-11
Make sure to have read this before asking anything else :
[http://appdb.winehq.org/appview.php?iVersionId=3126](http://appdb.winehq.org/appview.php?iVersionId=3126)

The appDB is the first place to search when you have problems.

If you didn't install any firewall then you shouldn't have problems with your ports.

Then if you can't find the answer to your problem in the appDB, come back here with the needed infos (wine version, wine config, instruction followed to install W3, graphic card name and so on).

---

### Post by FRuMMaGe on 2007-07-11
Yes i've been on there but could not find the answer.

I thought it may be an Ubuntu specific problem so I posted here.

---

### Post by FRuMMaGe on 2007-07-11
bump

---

### Post by Mike'sHardLinux on 2007-07-12
What kind of graphics on your laptop? Is it by chance ATI?

---

### Post by FRuMMaGe on 2007-07-12
Nope, but I know why you are asking.  As I have already said I have read all the bug reports bug they assume you are using an ATI graphics card.  I am using an Intel 945G integrated card with the i810 driver.

It should not be a graphics problem as I can play single player games perfectly.

---

### Post by frodon on 2007-07-12
please tell us at least what version of wine you ar using, some versions are known to create problems with some games.
Explain what is your wine config as well, do you use alsa or oss for sound, did you try the Emulate Virtual Desktop option, ....

you will find many useful infos here :
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

---

### Post by FRuMMaGe on 2007-07-12
> **frodon said:**
> please tell us at least what version of wine you ar using, some versions are known to create problems with some games.
Explain what is your wine config as well, do you use alsa or oss for sound, did you try the Emulate Virtual Desktop option, ....

you will find many useful infos here :
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

Ok, I am using Wine v0.9.39.  I don't use the emulate desktop, and primarily I use OSS due to its best compatibility.  However, I have tried every configuration imaginable to try and fix this problem but to no avail.

---

### Post by Afoot on 2007-07-12
Have you set up your drive mappings correct? Start winecfg, go to the Drives tab, press "Autodetect..." and apply the changes. Now, it should work...

---

### Post by FRuMMaGe on 2007-07-12
Yes i've done all this.

---

### Post by angryfirelord on 2007-07-12
Weird, TFT works fine for me online.

When you type your wine command, remember to add --enable-opengl at the end of it.

I'm really not sure why it's doing this, but did you try joining a regular game rather than a custom one? Other than that, it seems the blame could on the intel card. Try changing the audio driver as well. I set it to alsa with 44100 Hz and 16-bit depth under full hardware acceleration.

---

### Post by FRuMMaGe on 2007-07-13
> **angryfirelord said:**
> Weird, TFT works fine for me online.

When you type your wine command, remember to add --enable-opengl at the end of it.

I'm really not sure why it's doing this, but did you try joining a regular game rather than a custom one? Other than that, it seems the blame could on the intel card. Try changing the audio driver as well. I set it to alsa with 44100 Hz and 16-bit depth under full hardware acceleration.

I play with opengl using the registry entry listed on the wine site so there is no need for the --enable-opengl suffix.  And yes I am joining regular ladder games.

I really don't see how this is a video problem though :(

---

