---
title: "VICE Commodore emulator - No Sound?"
date: 2006-08-28
forum: Desktop Environments
---

### Post by celticmonkey on 2006-08-28
Anyone having trouble getting sound to work in the VICE emulator in Dapper?

I keep getting this error:

Cannot open '/dev/dsp' for writing

I tried this command line argument but it didn't help:
x64 -sounddev uss -soundarg /dev/dsp1

I tried a few other soundarg options as well. Nothing.

(ps. Yes, I have the ROMS installed.)

---

### Post by simonn on 2006-08-28
what does the following return:

> 
$ ls -l /dev/dsp


---

### Post by celticmonkey on 2006-08-28
I got:

crw-rw---- 1 root audio 14, 3 2006-08-27 21:10 /dev/dsp

---

### Post by celticmonkey on 2006-08-28
Hmmm... I also got the same type of error trying to run lxdoom, the doom emulator. (I have WADs and the lxdoom soundserver installed.)

```
I_InitSound: Passing sound data to /usr/games/sndserv via pipe: I_InitSoundGen: Could not open /dev/dsp
```

Sound does work for other applications.

---

### Post by celticmonkey on 2006-08-28
After some research I was able to get sound working in VICE

There is an OSS wrapper for non-ALSA applications:

```
aoss x64
```

This also solve a problem I had getting sound on YouTube.

```
aoss firefox
```

Still no luck with lxdoom, however.

---

