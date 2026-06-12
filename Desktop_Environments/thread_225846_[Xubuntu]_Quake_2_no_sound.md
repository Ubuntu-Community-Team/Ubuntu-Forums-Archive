---
title: "[Xubuntu] Quake 2 no sound"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Krank on 2006-07-30
System specs:

Pentium II 350mhz
256 mb RAM
Graphics: RIVA 128
Soundcard: OPTi 82C924

Trying to get sound in Quake 2 (installed from repositories) and JoeQuake (downloaded binary). I got sound in Beep Media Player and more or less every other program I've tried so far.

...and yet, when I run either joequake.svga or quake2 I just get the following error:

Quake II:
```

loading oss sound output driver, ok
/dev/dsp: No such file or directory
SNDDMA_Init: Could not open /dev/dsp.

```

Quake I:
```

/dev/dsp: No such file or directory
could not open /dev/dsp
Startup: SNDDMA_Init failed.

```


I've heard that modern Linux systems don't use the /dev/dsp anymore - but is there any way to get this working? Quake II is even in the repositories, for gosh's sake...

Can anyone perhaps point me in the right direction?

---

### Post by jISh on 2006-07-30
Try putting this into the terminal before launching either game:
```
killall esd
```

After your game, type 
```
esd
```

Can write a shell script to kill the esd, open your game, and enable the esd again afterwards.

---

### Post by Krank on 2006-07-30
Nope, didn't work.

There's simply no such thing as /dev/dsp at all...


Tried aoss too - that got me a bunch of garbled noise and not much else.

Thanks for trying =)

---

### Post by sorcererx84 on 2006-07-30
Try ```
echo "quake2 0 0 direct" > /proc/asound/card0/pcm0p/oss
``` as root in a terminal. Then do 'killall esd' and run quake2 again.

---

### Post by Krank on 2006-07-30
No such animal. There's no "oss" file in that dir, and therefore the command fails miserably... =)

The /proc/asound/card0/pcm0p/ dir contains only a "info" file and a "sub0" dir...

---

### Post by Dan Ballantine on 2006-09-21
Use the Loki install it fixed my sound problems

---

### Post by TrueJk7 on 2006-09-28
... "Loki"? I looked for it in the Synaptic Package Manager and pulled this 

> [Biology] MCMC linkage analysis on general pedigrees
Performs Markov chain Monte Carlo multipoint linkage analysis on large,
complex pedigrees.  The current package supports analyses on quantitative
traits only, although this restriction will be lifted in later versions.
Joint estimation of QTL number, position and effects uses Reversible Jump
MCMC. It is also possible to perform affected only IBD sharing analyses.

Homepage: [http://loki.homeunix.net](http://loki.homeunix.net).

Somehow, since it seems to have no link to Quake or Sound card issues (mainly not being detected) I dont think were looking at the same "Loki"s. What exactly did you do to fix your sound problem?

---

