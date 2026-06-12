---
title: "UT2004 no sound:S comfused.help!"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by keef247 on 2007-04-01
root@pc:~# ut2004demo
open /dev/[sound/]dsp: Device or resource busy
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
thats the error i get..
how do i make it work with oss? its the demo. i REALLY want sound:(
simple steps.im new.cheers

---

### Post by keef247 on 2007-04-01
bump:P

---

### Post by ikonia on 2007-04-01
you're running as root - you're not meant to run as root, so your display variable is not set so the X windows sessoin is complaining about something.

/dev/dsp is your sound device and its either not accessable or locked

---

### Post by keef247 on 2007-04-02
so what would you idvise? why does root have a problem with it?i didn't think playing it as root would matter.
i red somewhere when looking for the demo about someone entering a command in the terminal in the game to enable oss?any idea what i should enter?
cheers

---

### Post by keef247 on 2007-04-02
fixed no worries:D

---

### Post by ikonia on 2007-04-04
how about posting the fix so others an benifit from your mistakes.

---

### Post by Tipou on 2007-04-07
I got the problem and I successfully fixed it. I hope this post will help people with the same problem.

First, I need to say I am using ubuntu 6.10 and I have the complete UT2004 (patched to  3355).

Install *libopenal0a*
```
sudo apt-get install libopenal0a
```

Make a backup of the original openal from UT2004
This line assume your game is installed in /usr/local/games/ut2004. Replace for your own path if you didn't install the game at this location.

```
sudo cp /usr/local/games/ut2004/System/openal.so ~/
```

Make a symbolic link to your own openal. Again, change your game's location if it's not in /usr/local/games/ut2004.

```
sudo ln -s /usr/lib/libopenal.so /usr/local/games/ut2004/System/openal.so
```

Run the game...

I am using gnome and ESD still open.

See you in the battle field! :)

---

### Post by keef247 on 2007-04-08
well turns out there was no problem the sound just wasn't working randomly.after a restart it randomly worked.even when speaking on skype at the same time in oss mode.alsa did the ut2004demo sound (or so i presume)

---

