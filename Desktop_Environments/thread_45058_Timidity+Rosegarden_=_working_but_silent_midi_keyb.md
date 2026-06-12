---
title: "Timidity+Rosegarden = working but silent midi keyboard"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Flawed on 2005-06-28
I finally got timidity working using this howto (I have a SB Live and as far I know its Linux drivers can't do hardware midi synthesis.) 

[http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo](http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo)

Rosegarden obviously sees my midi keyboard and is giving me graphical feedback when I hit the keys, but there's no sound. What do you think I could have done wrong? Is there a midi volume control somewhere? Jack is up and running, by the way.

 I have a sound fonts file, it's the same freeware one I use in Windows with decent results. Here's another thing: Rosegarden seems to expect me to point it to the sfxload executable, but where can I find it? I don't seem to have one on my system and I can't find a package called sfxload in kynaptic, either.

Any advice? Lots of thanks in advance.

---

### Post by alainhenry on 2005-07-04
Maybe a stupid question, but have you checked that midi synthesis works with other programe, for example:

pmidi -p 128:0 yourmusic.mid 

Nothing to do with sfxload, but have you tried fiddling with alsamixer ?  I noticed that to record sound, I had to unmute some weird channel in alsamiwer.  Maybe there are some other channels you must increase ?

Alain

---

