---
title: "[SOLVED] Crackling Sound in games, rhythmbox / totem / flash are fine"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by keyboardashtray on 2007-08-07
I am having crackling, popping sound in games like Lincity NG and Battle for Wesnoth. There are no sound problems in Rhythmbox, Totem, Flash, etc., any form of media like that, those are all fine. It is just in games.

When I bring up Sound from Preferences, it has HDA Intel chosen as the device. There is a drag down option of Realtek ALC 880.

Any ideas?

---

### Post by barbaricrunner on 2007-08-07
Perhaps it was a bad download.  I would try uninstalling the game(s), then re-install them.

---

### Post by johnb820 on 2007-08-07
I've had problems with popping/crackling sounds before and it was because the program I had running (vlc, rhythmbox) had their sound turned up too high while the main volume was too low.  Really I believe bass was what caused the crackling because through an equalizer such as in vlc, lowering the low dbs sounds removed the weird click like crackling.

---

### Post by keyboardashtray on 2007-08-07
> **johnb820 said:**
> I've had problems with popping/crackling sounds before and it was because the program I had running (vlc, rhythmbox) had their sound turned up too high while the main volume was too low.  Really I believe bass was what caused the crackling because through an equalizer such as in vlc, lowering the low dbs sounds removed the weird click like crackling.

Yeah, you know, I can definitely make it tolerable by just turning the volume low, but I still think there is an underlying issue - because I can (and do) crank my regular music and whether its Stevie Wonder or Slayer they both sound great, whether it is bassy or trebley. And I've tried different combinations of system volume and speaker volume. Same goes with online videos, etc., it is just that sort of synthesized video-game style music that crackles, currently from the two games I've mentioned but I think I encountered it in a couple other games that I tried right when I got Ubuntu but didn't keep.

---

### Post by keyboardashtray on 2007-08-07
> **barbaricrunner said:**
> Perhaps it was a bad download.  I would try uninstalling the game(s), then re-install them.

Thanks for the idea :) I tried this with Lincity NG and I still have the crackles. though...I'm really stumped.

---

### Post by graigsmith on 2007-08-08
open the console and try running alsamixer. and fidddling with all the settings. i think if you hit f5 in alsamixer, you can see all the bars. just play around in it, you'll figure it out.

the up and down keys adjust the volume m is mute. and 1-0 is volume adjustment

---

### Post by K.Mandla on 2007-08-08
I had this issue in Warzone 2100 and in Regnum Online, where the sound output in the game was crackled and distorted, but other programs were fine. It did seem to help when I turned down the sound output level within the game, although the crackling hasn't ever gone away for me. It happens in those same games, across installations and regardless of my tweaking it.

To be honest, I always wrote this off as a flaw in the game, rather than a fault with the system. Maybe I was too quick to dismiss it out of hand, though. ...

In the hopes that it helps, I'll move your thread to the gaming area. ;)

---

### Post by hikaricore on 2007-08-08
Actually this fixes games that use OpenAL.

Regnum for sure.

Create a file in your home dir called:  **.openalrc**

And place the following inside it.

```

(define alsa-device "default")
(define devices '(alsa native))

```

Save the file, start Regnum.  Sound should be fixed.

--

If that doesn't work, remove the pevious settings from the file and just put this in it:

```
(define devices '(native))
```

The latter of the two was the original fix, but after having to fix for another game with the first config options, Regnum was still working fine.

---

### Post by keyboardashtray on 2007-09-14
I stumbled on this, seemed to do the trick: [http://ubuntuforums.org/showpost.php?p=2378018&postcount=3](http://ubuntuforums.org/showpost.php?p=2378018&postcount=3)

---

### Post by bubbalouie on 2007-09-14
I found changing the sample rate from 44100 to 48000 in the game settings (it's the first thing I do with ZSNES :) ) fixes things for my lappy.

---

### Post by JurB on 2007-10-21
> **hikaricore said:**
> 
Create a file in your home dir called:  **.openalrc**

 put this in it:

```
(define devices '(native))
```.

This works for me. TNX!

---

### Post by FuturePilot on 2007-12-12
> **hikaricore said:**
> 

If that doesn't work, remove the pevious settings from the file and just put this in it:

```
(define devices '(native))
```

The latter of the two was the original fix, but after having to fix for another game with the first config options, Regnum was still working fine.
Thank you, thank you, Thank You!!
That cracking/popping noise in games was starting to drive me nuts. :grin:
:guitar:

---

### Post by FSHero on 2007-12-22
Hi guys, I'm running Kubuntu 7.04 Feisty i386, and I've got a similar problem with Nexuiz and Neverball. Whenever a sound plays in either of these there is crackling. It is much worse in Neverball, however.

Anyway, I tried both the options below (one at a time) like hikaricore said, but to no avail:
```

(define alsa-device "default")
(define devices '(alsa native))

```

```

(define devices '(native))

```

There is still crackling noise from Nexuiz (I haven't checked Neverball yet -- but I only play Nexuiz now so would like to fix it!). I also tried changing the sample rate in Nexuiz from 48 kHz to lower values (e.g. 20-something kHz, 44.1 kHz), but this doesn't help; in fact, it just reverts to 48 kHz (and I can tell that it isn't at 20 kHz: because it would sound 'poor' in quality).

Can someone help please? Also... why might this be happening? (Note, playing music through Amarok is 100% fine.) I used to run Windows 98 on an old computer and whenever it had a high processor load, sound went crackly. Could it be a similar effect?

---

### Post by jhansonxi on 2008-05-12
I filed [bug #214448](https://bugs.launchpad.net/ubuntu/+source/openal/+bug/214448) about this configuratoin problem but it may be invalidated by [bug #194919](https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919) in Intrepid Ibex which calls for replacing the old OpenAl implementation.

---

### Post by Evillz on 2010-01-02
> **keyboardashtray said:**
> I stumbled on this, seemed to do the trick: [http://ubuntuforums.org/showpost.php?p=2378018&postcount=3](http://ubuntuforums.org/showpost.php?p=2378018&postcount=3)

I did this and it fixed the crackly sound problem for me.

First I did this.  I don't remember how I did it though.  I opened a file using a terminal script that someone posted.
(define devices '(native))
 
This didn't fix the crackly sound, so I followed the instructions at thread listed above and installed the recommended package and that fixed the problem.

Just a helpful reminder for those that aren't familiar with Ubuntu, the Synaptic Package Manager is really easy to use and works great.  Just search for a package that someone references and use the graphical user interface to place a checkmark, or remove checkmarks, and install or uninstall as suggested.

---

