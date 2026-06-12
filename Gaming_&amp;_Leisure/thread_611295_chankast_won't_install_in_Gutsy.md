---
title: "chankast won't install in Gutsy"
date: 2007-11-12
forum: Gaming &amp; Leisure
---

### Post by xjgnsdof on 2007-11-12
I have Chankast Alpha 0.25 and can't run it through WINE. When I try to, I get an error message: "Can't find any input plugin." Afterwards, the emulator closes.

---

### Post by xjgnsdof on 2007-11-17
up

---

### Post by hikaricore on 2007-11-17
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8949](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8949)
[http://forums.ngemu.com/chankast-discussion/53700-got-chankast-run-linux.html](http://forums.ngemu.com/chankast-discussion/53700-got-chankast-run-linux.html)
[http://forums.ngemu.com/chankast-discussion/75613-linux-chankast-running-under-wine.html](http://forums.ngemu.com/chankast-discussion/75613-linux-chankast-running-under-wine.html)

This forum says it works... however AppDB says it doesn't.
You'll also need fantastic hardware, but I can see you already have that.

Have you looked into this emulator? [http://ubuntuforums.org/showthread.php?t=601203&highlight=dreamcast](http://ubuntuforums.org/showthread.php?t=601203&highlight=dreamcast)

It has a native linux port.  ^_^

---

### Post by xjgnsdof on 2007-11-17
Thanks. I'll give it a shot and see if it works with Shenmue.

---

### Post by xjgnsdof on 2007-11-17
I just installed lxdream. I had to get the dreamcast bios and flash bios and point lxdream to them in the program itself. However, I get the following line:

```
01:01:11 A0000000 ERROR Unable to open audio output (ESD)
```

Not only is there no sound when I play Shenmue, but the "Audio" option is ghosted in the main menu, as is the "Video" option. While the game plays, I get missing polygons in many places. 

Any idea on what to do about either of these issues?

---

### Post by hikaricore on 2007-11-17
Entirely unfamiliar with lxdream, but i have a few ideas about the audio.

I'm assuming that Gutsy uses pulse audio by default, but I could be wrong.
(I've always installed pulse since it's been in the repos, but since I upgraded I don't know the default setup of Gutsy)

To resolve issues you could try running:

> padsp _program_

Where program is the name of the program.

Failing this, try installing the "esound" package:

> sudo apt-get install esound

---

### Post by xjgnsdof on 2007-11-17
Installing padsp and running lxdream with it didn't change anything; I still get no sound. Also, I already installed esound and recompiled the package. Any other ideas...anyone?

---

### Post by hikaricore on 2007-11-17
There was no point in installing pulseaudio components if you aren't actually using pulse audio.. just fyi.  ^_^

---

### Post by xjgnsdof on 2007-11-17
After I installed esound and recompiled the package, I got sound at the Dreamcast boot screen, but not in the game itself.

Also, the options for Video and Audio are still ghosted, and I think that my being able to access them may rectify my problems as to the missing polygons and the muted sound.

Anybody know how to use this thing?

---

