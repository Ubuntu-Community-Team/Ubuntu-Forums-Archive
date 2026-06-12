---
title: "GUI for Mupen? Also, is there a way to get Mupen64plus to go fullscreen?"
date: 2012-09-25
forum: Emulators
---

### Post by 777funk on 2012-09-25
I have been running Mupen64Plus through Terminal. Is there an actual GUI Interface (not terminal) for this? 

Also, can't get it to go fullscreen any tips there?

---

### Post by WienerWuerstel on 2012-10-03
There is a great GUI for Mupen64Plus out there and it's called [M64Py]("http://m64py.sourceforge.net/").

---

### Post by ikem.krueger on 2012-12-08
There's also CuteMupen:

[http://sourceforge.net/projects/cutemupen/](http://sourceforge.net/projects/cutemupen/)

---

### Post by LillyDragon on 2012-12-09
If you want Mupen to go fullscreen, there is a terminal command for it and you can even choose the resolution. I prefer using a launcher to handle that, however, since it's much faster. This is what mine looks like encase you want to create custom launchers for each of your games.

```
mupen64plus --fullscreen --resolution(640x480) '/host/Users/Jonathan/My Games/Nintendo 64/Legend of Zelda - Ocarina of Time.z64'
```

Don't forget that there are tons of other commands for Mupen64Plus as well : [http://code.google.com/p/mupen64plus/wiki/UIConsoleUsage](http://code.google.com/p/mupen64plus/wiki/UIConsoleUsage)

[quote="ikem.krueger"]There's also CuteMupen:

[http://sourceforge.net/projects/cutemupen/](http://sourceforge.net/projects/cutemupen/)[/quote]

Last I tried that on Precise Pangolin, it nearly broke my package management system. If it weren't for the automatic repair option, I would have been completely screwed out of installing additional programs from the Software Center, and forced to reinstall my OS. (Since that's always faster than figuring out what went wrong over something this complicated.) I had to reinstall Xscreensaver for whatever reason, but it's fine now. XD

**EDIT** : Forgot to mention the package I got was from PlayDEB, or GetDEB, can't remember which. Either way, if CuteMupen is still in the Software Center, it's a much safer bet than a dated third-party package for Lucid Lynx.

[quote="WienerWuerstel"]There is a great GUI for Mupen64Plus out there and it's called M64Py.[/quote]

This installed and worked fine on my system, but it doesn't launch Mupen when loading a disk image for me. Maybe M64Py doesn't like x64 CPUs or can't find my binary of Mupen64Plus, I don't know for sure why it's not working for me. I hope the topic creator over here doesn't bump into the same problem, having a GUI for this emulator is quite handy for quickly configuring things without a text editor.

---

