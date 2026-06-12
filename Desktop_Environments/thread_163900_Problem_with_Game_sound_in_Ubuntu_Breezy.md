---
title: "Problem with Game sound in Ubuntu Breezy"
date: 2006-04-21
forum: Desktop Environments
---

### Post by proton_ghost on 2006-04-21
Hey Everyone,

Whenever I try to start a game from an icon (either from the Applications menu or if I create my own launcher) I get no sound for the game.  But, if I run the game from the terminal, the sound works no problem.  This happens every time, so obviously there is some sort of sound process that isn't starting when I use an icon.  Anyone have any ideas?

Thanks in advance.

---

### Post by joft on 2006-04-22
Hi,

I'm not 100% sure, but your problem might be, that GNOME is playing a sound as soon as you (double)click the icon for your launcher. "Playing" means that GNOME contacts it's sound server ESD and ESD in turn opens the sound device (and plays the sound).

Assumption: Your sound card doesn't support hardware mixing, right?

So, right after that happens, your game starts up - and another assumption - your game uses OSS (Open Sound System, old, deprecated). ALSA (Linux's current sound subsystem) emulates the old OSS. At at that point of time your game can't open the OSS sound device, because ESD has already opened the ALSA sound device and though "blocks" the whole sound subsystem.

AFAIK ESD releases the sound device after some seconds/minutes again - but then it's to late for your game.

If you start your game from a console, there is no playing of any sound, as soon as you hit the enter key, so no ESD is being contacted and no sound is played and thus the sound subsystem isn't block from the view of your game.

You could stop ESD before starting your game:
```
killall esd
```

or even disable it completely in System->Pref->Sound (result would be: no GNOME sounds)

Or you could use esddsp to reroute your games sound to ESD:
```
esddsp <game>
```

Or you could use another solution like described in my HOWTO (to get software mixing right especially OSS applications):
[http://ubuntuforums.org/showpost.php?p=695990&postcount=6]("http://ubuntuforums.org/showpost.php?p=695990&postcount=6")

---

