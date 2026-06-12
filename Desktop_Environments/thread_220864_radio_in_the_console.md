---
title: "radio in the console?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by halvdansk on 2006-07-22
hi! how do i play internet radio in the console? i have tried mpg321 radiostation.wav etc

Thx

---

### Post by philippe_carlo on 2006-07-22
Use mplayer.

---

### Post by halvdansk on 2006-07-22
[johan@FreeBSD ~]$ mplayer jazzradio.wax
MPlayer 1.0pre8-3.4.4 (C) 2000-2006 MPlayer Team
CPU:    Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz (Family: 15, Model: 
2, Step
ping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Playing jazzradio.wax.


Exiting... (End of file

---

### Post by SimonJW on 2006-07-22
jazzradio.wax is a playlist file. So you need to either run:
```

mplayer -playlist jazzradio.wax
```

or open it in gedit and find out where it links to, then run:
```

mplayer mms://stream.green.ch/jazzradio
```

Both these streams work for me (I guessed that [http://www.jazzradio.net/](http://www.jazzradio.net/) was the intended stream. Note they also have a WINE-compatible p2p streaming client, if you're interested)

---

