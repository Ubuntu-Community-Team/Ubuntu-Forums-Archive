---
title: "Glest [cannot play]"
date: 2009-09-25
forum: Gaming &amp; Leisure
---

### Post by 1linuxuzr on 2009-09-25
Hello first of all I am running 8.10 with Nvidia graphics...
00:08.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200]
I have half a gig of ram currently installed and do not have any other games that will not play on this box.

I have installed Glest version 3.1.2  with Synaptic. When I start Glest everything seems normal opens in full screen and displays a menu graphics look good and sound plays. I can click "options" and poke around seems good. After clicking on "new game" "join game" or "scenerio"  It starts to load the game I get various normal looking verbage scroll across the screen then the game opens then the music stops (sometimes is choppy) and everything freezes I cannot move curser with mouse cant esc I can't even ctrl alt * The only way out is that bad button on the front of my box :(

This happens even if I don't take any action ie no inputs from keyboard or mouse and everytime. This happens very quickly like as in right after the game music starts. clicking on "options" "about" and "exit" function as they should. 

I didn't see anything in var/log/  but did see a log file in my home folder but it looks very normal. If you insist I will post the glest.log but like I said very normal looking log. 

Has anyone else has any problems like so with glest? If yes is there a fix? I have tried uninstalling and reinstalling no change. I even uninstalled and tried to DL and install manually but that didn't work at all. :(

Any help would be appreciated Thanks in advance.

---

### Post by Perfect Storm on 2009-09-25
Try run it via the terminal and see what is happening.

---

### Post by 1linuxuzr on 2009-09-26
It took several attempts but I finally switched it to windowed then I could get back to the terminal and here is what it was outputing....


```
Restarting audio source because of buffer underrun.
Restarting audio source because of buffer underrun.
Restarting audio source because of buffer underrun.
```So any ideas how I  can prevent this?

---

### Post by Perfect Storm on 2009-09-26
Try disable the sound/music in glest and see what it says.

<snip>
Audio card?

---

### Post by BunTai on 2009-09-26
why didnt you try install Glest on Playdeb?
its more suitable maybe..

---

### Post by 1linuxuzr on 2009-09-26
> Audio card? 	

```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

I'm looking for a way to disable sound, I'm not seeing it right off.

---

### Post by Perfect Storm on 2009-09-26
Have you checked glest config file?

---

### Post by 1linuxuzr on 2009-09-26
I don't see a way to disable it maybe I'm overlooking it. I attached a copy of the .ini

I'm starting to think my crappy integrated sound card might just not work with this game.

---

### Post by Perfect Storm on 2009-09-26
> SoundStaticBuffers=16
SoundStreamingBuffers=4
SoundVolumeAmbient=15
SoundVolumeFx=15
SoundVolumeMusic=15


You can try play with these settings.

> Restarting audio source because of buffer underrun.

SoundStaticBuffers=16

Try changing it to 8
or lowering SoundStreamingBuffers

---

