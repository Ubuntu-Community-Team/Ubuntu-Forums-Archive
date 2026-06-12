---
title: "Anyone have Knights chess working? It just hangs"
date: 2006-06-26
forum: Desktop Environments
---

### Post by xoros on 2006-06-26
I installed knights, gnuchess v5, gnuchess-book. 

I setup gnuchess v5 in it (to play against computer)  It does 4 moves then just hangs. 

Here is what I get in shell when I start it: 
```
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QMetaObject::findSignal:io_engine: Conflict with io_base::sendCMD(const Command&)
```

Here is what I get in Knights log file: 
```
<- xboard
protover 3
-> gnuchessx is obsolete, please read the manpage for details.
-> Chess
-> Adjusting HashSize to 1024 slots
-> feature setboard=1 analyze=1 ping=1 draw=0 sigint=0 variants="normal" myname="GNU Chess 5.07" done=1
<- accepted setboard
<- accepted analyze
accepted ping
accepted draw
accepted sigint
accepted variants
accepted myname
hard
easy
new
random
white
sd 262144
st 131072
-> Illegal move: sd 262144
<- time 30000
<- otim 30000
e2e4
-> 1. e2e4
-> 1. ... c7c5
-> My move is: c7c5
<- time 29970
<- otim 29640
c2c4
-> 2. c2c4
-> 2. ... b8c6
-> My move is: b8c6
<- time 29970
<- otim 29470
d2d4
-> 3. d2d4
<- ?
<- ?
<- ?
<- ?
<- quit
```

The question marks is when I was trying to force it to move. Plus, why is it saying gnuchessx obsolete??, I have latest version.

Any ideas?  Should I send this to the knights people?
Thanks.

---

### Post by xoros on 2006-06-26
Instead of using the file gnuchessx in the setup,  I used the plain gnuchess,  but made no difference.

---

### Post by xoros on 2006-06-26
Here is what happens if I try to run it as root with -d option:

```
sudo knights -d /usr/share/apps/knights
Password:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
knights: WARNING: audio::audio: Can not create Arts::SoundServerV2
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kio_uiserver: cannot connect to X server :0.0
DCOP aborting call from 'knights-9940' to 'kio_uiserver'
DCOP aborting call from 'anonymous-9950' to 'kio_uiserver'
ERROR: Communication problem with kio_uiserver, it probably crashed.

```

---

### Post by 146lily on 2006-07-21
Different chess engines help, phalanx works 100% well. Fruit works well with you playing white!?](*,)

---

### Post by gamma-alpha on 2006-08-27
It seems that synaptic does not know what the dependencies for Knights are, because although it was written for KDE, synaptic does not ask whether it should install KDE (I'm running gnome) when installing Knights.  The program actually has many more dependencies which aren't dealt with by Synaptic either, so this probably explains why it hangs for some users but not others (probably KDE folks).

---

### Post by janhenderson on 2006-08-28
> **gamma-alpha said:**
> It seems that synaptic does not know what the dependencies for Knights are, because although it was written for KDE, synaptic does not ask whether it should install KDE (I'm running gnome) when installing Knights.  The program actually has many more dependencies which aren't dealt with by Synaptic either, so this probably explains why it hangs for some users but not others (probably KDE folks).

I had the same problem with knight hanging on the third move for the computer, which is regrettable, as it seems a nice program otherwise. I tried to fix it, even compiling from source, but couldn't, so gave up. Anyhow, you really don't need a complex thing to play chess. Part of the joy of the game to me is its simplicity. As such, I've come to appreciate the no-nonsense quality and reliability of xboard. This thing is rock solid. I'd suggest you use that. Have a look at the command line options for xboard. Here are the few that I use the most 

xboard -tc 40 -mps 40

-tc stands for time control in minutes
-mps stands for moves per session 

You can also specify size if you don't like the default one.. the parameter for size is 

xboard -size medium 

and if you don't like the medium size the man page lists other options , just type

man xboard 

and do what look for the options there 

to quit the manpage just type q

---

