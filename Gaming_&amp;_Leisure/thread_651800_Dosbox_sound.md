---
title: "Dosbox sound"
date: 2007-12-27
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2007-12-27
Hey, I've searched the forums, but so far nothing I have done with DOSbox has given me any MIDI support. here's my situation.

I've downloaded DOSbox (latest as of december 27/07) through the repos. I've gotten timidity as well as the extras, and I've installed the game I want to have work (DOOM).

how do I link timidity to DOSbox and where are these elusive ~/.bashrc and ~/.dosboxrc that don't seem to be in my home directory?

---

### Post by FranMichaels on 2007-12-28
To create a .dosboxrc, Launch dosbox.

From the Z:\ prompt (or whatever)
```
config -writeconf .dosboxrc
```

Exit dosbox.

Now fire up a terminal

```
gedit ~/.dosboxrc
```

search for [midi]

make sure that the line with config looks like this 

config=128:0

Save.

Ok, if you are running Gutsy, timidity is running in server mode.
You are all set! :)

If you want the latest dosbox (0.72), I like it because you can right click on whatever exe, and it handles mounting the folder automatically. You can grab the deb [here]("http://www.getdeb.net/release.php?id=1722").

Oh yes, I forgot to mention, for DOOM specifically, if you'd like to run it with less overhead and some extra features, look at [PrBoom]("http://prboom.sourceforge.net/") It is in the Ubuntu repositories.

---

### Post by Tyke91 on 2007-12-28
hmm... followed your instructions and also upgraded to 0.72, however i still have no sound. I think it's because timidity is NOT running in the background. How can I configure it to?

---

### Post by Tyke91 on 2007-12-28
[LEFT]Hmm... still no luck, I tried the instructions listed here, but i still don't have sound (prBoom is really good, but it just isn't the same as DOOM) [http://ubuntuforums.org/showthread.php?t=618914&highlight=dosbox+sudo+modprobe](http://ubuntuforums.org/showthread.php?t=618914&highlight=dosbox+sudo+modprobe)
[/LEFT]

---

### Post by FranMichaels on 2007-12-28
> **Tyke91 said:**
> [LEFT]Hmm... still no luck, I tried the instructions listed here, but i still don't have sound (prBoom is really good, but it just isn't the same as DOOM) [http://ubuntuforums.org/showthread.php?t=618914&highlight=dosbox+sudo+modprobe](http://ubuntuforums.org/showthread.php?t=618914&highlight=dosbox+sudo+modprobe)
[/LEFT]

Hmm. You are using your doom.wad right? Not freedoom?

As for DOSBox, if another app isn't tying up sound, it should be working. Can you run the doom setup program. Did it use midi, or adlib? Make sure the in game settings, irq and dma etc, match the options available in .dosboxrc. 

Do you have another dos application to test in dosbox?

[http://liberatedgames.org/]("http://liberatedgames.org/")

Carries games where the copyright owner has given it permission to be freeware or in some cases open sourced.

I recommend Tyrian 2000 :)

---

