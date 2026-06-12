---
title: "Volume dieing to nothing at less than 50% down."
date: 2009-06-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheNad on 2009-06-17
I'm using a Dell Studio 17" w/ Ubuntu 9.04. When I am listening to anything (either through the speakers built into the laptop or through my headphones) and I attempt to lower the volume, the volume will get to zero output by the time the volume meter is a little less than 50%. Has anyone else experienced this? Any documented fixes? Feel free to ask for clarification; it's almost 2 AM here and I'm sure I'm not quite as coherent as I should be...

---

### Post by mynameinc on 2009-06-17
Click on the volume icon at the top, beside the calendar, and then click "Volume Control".  Turn "PCM" to the maximum.

---

### Post by Togezo on 2009-06-18
Hey, I'm getting a similar problem with my Dell 1545, running 32 bit Jaunty.

I have checked the PCM- it's at 100%, so it's not that...

---

### Post by mynameinc on 2009-06-18
What organization manufactured your sound card?

---

### Post by Togezo on 2009-06-19
The insprion booklet informs me that I have 2 channel Intel High definition audio, controlled by an IDT 92HD71.

---

### Post by TheNad on 2009-06-20
Sorry for the late reply. PCM is all the way up for me too.
I'm running an Intel HD Audio card.

---

### Post by AndThenWhat on 2009-06-23
It is a kernel problem with how the kernel communicates with Intel sound cards.  I have the same issue on the 2.6.28-13-generic kernel with the following sound card:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

However, on a later development kernel that problem is fixed for me.  Give it a few kernel releases and it will probably be resolved.

---

### Post by nwadams on 2009-06-23
ok. so here's the solution.

Set your volume control to the pulse audio mixer. 

Then max the PCM, etc. The alsa mixer master volume control isn't scaled correctly with the pulse audio one. (the pulse audio one is better). 40% on alsa == 0% on pulse audio (anything below 40% is still 0)

so just set your volume control and tray icon to use the pulse audo mixer (playback one) and then just ignore the alsamixer one. 

more detailed instructions:
go to system/prefereces, sound
near the bottom where it says default mixer tracks change it to the playback HDA intel...etc (the pulseaudio one)

and make sure the mixer is master (only one probably)

then where your volume icon is on your desktop tray. Right click on it and go preferences. and do the exact same thing we did above for the default mixer track

---

### Post by TheNad on 2009-06-25
Thanks ATW. I'll hope they fix it eventually. Not too big a deal since I have the whole range, just condensed into 60% of the space :)

@nwadams: Tried what you suggested (in both the locations it needed to be done) but to no avail. Even tried restarting after the changes but the problem remained. You said to use Playback: HDA Intel, right?_[U]_[/U]

---

### Post by nwadams on 2009-06-25
ya, the pulse audio one. i think you got it. It doesn't really fix the alsa mixer ranges. All it does it use the pulse audio modifier for volume which is the whole range in the whole space and then u can just ignore the alsamixer one. 

But if you did it as I said and it didn't work for you then i'm sorry i've got nothing at the moment. But if I do figure something out I will let you know.

---

