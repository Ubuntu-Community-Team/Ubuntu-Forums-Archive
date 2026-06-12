---
title: "amaroK Crashes on Play"
date: 2007-03-09
forum: Desktop Environments
---

### Post by RAdams on 2007-03-09
When I play ANY media file in amaroK, it crashes.

I'd give debugging info if someone could tell me how to give info for this. Running amarok in terminal returns this much at start:
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

```

But nothing when I try to play a file. It shows the little popup box with the name of the file, then that goes away and amaroK freezes without me hearing a sound.

---

### Post by jazzdonkey on 2007-06-25
I am new to the forums so please forgive me if this post appears a little ugly or non-standard.

I too am receiving this same error:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
*** PULSEAUDIO: Unable to connect: Connection refused
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

I am fairly new to Ubuntu so I can't exactly figure this out.  Any help would be great.  Thank You in advance!  You people are awesome!

---

### Post by mr_arrow on 2007-07-05
I have the same probelm! Amarok just stoped working :(

here's my output:

```
amarok %U
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

Please help me!

Regards
Erik

---

### Post by ktneely on 2007-07-07
Has anyone discovered a way to fix this problem.  I reun Gnome as my primary desktop but recently installed Amarok on my Feisty Fawn installation.

---

### Post by mytwobears on 2007-07-07
If you are running Amarok under Gnome, check to make sure you have all the kde dependencies and the qt dependencies as well.  This happened to me and I realized that I was missing the kdelib and qt library dependencies.  Once these are installed, Amarok runs smoothly under Gnome.

---

### Post by deathspell on 2007-07-08
What all do i need to install? My Amarok was working fine but now it crashes, or doesn't run at all at times.

---

### Post by koshari on 2007-07-08
what version of amarok are we all running?

what package did you use?

---

### Post by ktneely on 2007-07-08
Output from the shell:

ktneely@bacall:~$ amarok -v
Qt: 3.3.7
KDE: 3.5.6
Amarok: 1.4.5
ktneely@bacall:~$ uname -a
Linux bacall 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

I installed via apt, and added a number of the "recommended" packages to go with it.  I have about 5 albums worth of mp3s on my laptop, which it found relatively easily.

Via apt, I installed amarok and pretty much all of the packages recommended by apt.

However, the program crashes when I drag an album over to the playlist.  I have seen that others have experienced a similar problem

---

### Post by mytwobears on 2007-07-09
Well if it used to play these files before and suddenly started to malfunction, I would uninstall it completely and then do a fresh install of the package.

I generally find this solution to be easier than to begin messing around with configurations and fixes etc.

---

### Post by ktneely on 2007-07-09
I can try a fresh install, however, this is a new install of Amarok and I have never had it working.  This is my first attempt at using the program.

---

### Post by Rebeca on 2007-07-15
Just make sure you:

1. Meet all amarok requirements: [http://amarok.kde.org/wiki/Requirements](http://amarok.kde.org/wiki/Requirements) 
2. Enable all multimedia: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)
3. And, also get the xine codecs since amarok uses xine:

```
sudo apt-get install libxine-extracodecs
```

---

### Post by ktneely on 2007-07-15
This was pretty much the solution, thank you!  First I updated to amarok 1.4.6 using the backports option in Synaptic, then I got the message right before amarok crashed that I did not have an mp3 decoder installed.  From there, I added xine and all its components, and voila!  Solved.

thank you

---

