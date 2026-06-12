---
title: "Mupen64Plus-GTK Update (14.1.24)"
date: 2014-01-24
forum: Emulators
---

### Post by gerowen on 2014-01-24
Just posted an update to my graphical Mupen64Plus launcher for Linux/Unix. You can download it at: [https://sourceforge.net/projects/mupen64plusgtk/](https://sourceforge.net/projects/mupen64plusgtk/) 

Changes made in this version are:
- Added a "custom" option to the configuration process to allow users
to point to a specific .so file to use as their graphics plugin.
- Re-worded the program's description as a "launcher" instead of a "front-end" since it doesn't actually perform any of the emulation work, it just takes in information and passes that information to mupen64plus.
- Replaced all the "is" occurrences in the program's if statements with
== , just to make sure everything is to standard.
- Added an example resolution to the configuration dialog so users will
know how to enter their resolution.

Maybe if I get bored I'll work on the code a little to have it functioning on Windows, since it is Python, but when I tried it before I ran into some headaches with how Windows interpreted certain things and the fact that you had to locate and specify "all" of the plugins and the controller configuration by default in the Windows version of Mupen64Plus, so I just quit on it since it was originally just a project for myself to replace the GUI that used to come with the Ubuntu and Debian versions of Mupen64Plus.

I also uploaded some updated screenshots and such to the sourceforge page.  It's nothing too fancy, just something I wrote for myself because I was having some issues with some of the other offerings, and figured I'd share it.

---

### Post by BigSilly on 2014-01-25
Looks fantastic! I've just tried using it with Mint 16 Cinnamon but I get the following error:

```
bigsilly@bigsilly ~/Downloads/Mupen64Plus-GTK $ ./mupen64.py sh: 1: ./killscreensaver.sh: not found
sh: 1: ./startscreensaver.sh: not found
```

Is there a file missing? Thanks. :)

---

### Post by howefield on 2014-01-25
Thread moved to the "*Emulators*" forum.

---

### Post by gerowen on 2014-01-25
> **BigSilly said:**
> Looks fantastic! I've just tried using it with Mint 16 Cinnamon but I get the following error:

```
bigsilly@bigsilly ~/Downloads/Mupen64Plus-GTK $ ./mupen64.py sh: 1: ./killscreensaver.sh: not found
sh: 1: ./startscreensaver.sh: not found
```

Is there a file missing? Thanks. :)

Apparently I forgot to include the screensaver kill script, if you want you can just remove lines 126 and 128 from the mupen64.py file and that should get rid of the error.  Don't bother line 127, it's the one that actually launches the emulator.  Sorry about that.

---

### Post by gerowen on 2014-01-25
On mine I get that same error because the screensaver kill/start scripts aren't present, but the game still runs.  Did the emulator still work fine for you regardless of the error?

---

### Post by BigSilly on 2014-01-25
> **gerowen said:**
> On mine I get that same error because the screensaver kill/start scripts aren't present, but the game still runs.  Did the emulator still work fine for you regardless of the error?

Hi, sorry for late reply. I commented out those lines as you say but the emulator still fails to launch a game (it failed before but with the errors I mentioned). Since commenting them out there's no error feedback but the like I say nothing happens when trying to launch a game. Maybe Mint is just too different to Ubuntu one way or another...?

EDIT: Actually I may have pointed it to the wrong folder for the executable...I'll try it again...

---

### Post by BigSilly on 2014-01-26
Managed to find my fault. It looks like it was trying to locate the Glide plugin for graphics but it was looking in the wrong place. Your log file said as much. ;)  :oops:

Once I pointed it at the right location (/usr/lib/x86_64-linux-gnu/mupen64plus) it was fine. And how! It runs in full screen! None of the other front ends can do this at the moment.

I think for a straightforward frontend you've done a fine job here, and thanks so much for sharing it with us. :)

---

### Post by gerowen on 2014-01-27
Glad it worked out for you, :-)

I had similar issues with other front-ends as well, which is weird because my little launcher/front-end here doesn't actually do a whole lot, it just collects information from you, and then passes all of that information as arguments to mupen64plus, so anything that would work if you manually typed the whole string into your terminal should work when using this, which is what puzzled me about why it didn't work when using other options.  Oh well, that's why I shared it.  I'm thinking about working in an update with some error handling so that if somebody points it to the wrong folder and it fails to launch the mupen64plus executable, they will get an error message telling them such, ya know, maybe give them a clue as to what exactly didn't work in the event that there's a problem.

Just an FYI, I was using a downloaded copy of Mupen64Plus, and when I was playing Ocarina of Time, there was an issue when using the Glide64 plugin where the game just outright crashes without any kind of output when you go into the market/castle square where the Happy Mask shop is.  It didn't happen if using the Rice plugin, but a guy pointed me to a PPA with an updated version of Mupen64Plus that doesn't have the issue when using Glide64.  Since your graphics plugin was in /usr/lib/x86_64-linux-gnu/mupen64plus, I'm guessing you're already using the good version, but just in case you run into this issue, here's two links that you may find useful.

Issue Page on Google Code: [https://code.google.com/p/mupen64plus/issues/detail?id=579](https://code.google.com/p/mupen64plus/issues/detail?id=579)
PPA for Updated Mupen64Plus: [https://launchpad.net/~sven-eckelmann/+archive/ppa-mupen64plus](https://launchpad.net/~sven-eckelmann/+archive/ppa-mupen64plus)

---

