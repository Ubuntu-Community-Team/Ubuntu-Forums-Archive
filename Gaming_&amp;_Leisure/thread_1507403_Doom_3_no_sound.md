---
title: "Doom 3 no sound"
date: 2010-06-11
forum: Gaming &amp; Leisure
---

### Post by pweaks on 2010-06-11
So my problem is that I can't hear any sounds on in game. My sound card is:  AD198x Analog (DUPLEX)

---

### Post by pweaks on 2010-06-12
No one can't help me?

---

### Post by Spummy on 2010-06-12
Hey, I'm no expert, but in my experience a whole lot of sound issues can appear from running older stuff with the newer Ubuntu due to PulseAudio. I don't know if that's what's causing it, but it's worth a try.

You need to launch doom3 from the terminal following the command "pasuspender" which'll disable PulseAudio for it.

So, say the file was doom3.x86, you'd find the directory with it, and run ```
pasuspender ./doom3.x86
```

If you're not too savy with the terminal, just ask and I'll try to get a step-by-step of what exactly you have to do. But yeah, hopefully it's just PulseAudio being silly.

---

### Post by rlarrowe on 2010-06-14
I don't believe pasuspender by itself will help.  Try this:

pasuspender -s=alsa -- <the program you want to run>

---

### Post by Cresho on 2010-06-14
pulseaudio is the major problem.  I went to kubuntu and just totally suspended the thing.  I just didnt want to deal with no desktop sound after totally uninstalling the garbage.

---

### Post by Virus666 on 2011-03-12
I managed to solve with that way:

[http://ubuntuforums.org/showthread.php?t=1705760](http://ubuntuforums.org/showthread.php?t=1705760)

---

