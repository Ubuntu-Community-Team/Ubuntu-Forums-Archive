---
title: "Quake 3 Arena freezes"
date: 2007-01-25
forum: Gaming &amp; Leisure
---

### Post by Hanj on 2007-01-25
I installed Quake 3 Arena using [this guide.]("https://help.ubuntu.com/community/Games/Native/QuakeIIIArena") After the installation it worked fine except that I had no sound. So I tried the fix suggested at the page, namely doing:
```

echo 'quake3.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss

```

After this the sound started working, but now the game freezes every time I complete an arena. No error messages or anything. Is there any way I can undo the sound fix so I can try some other workaround? I can't edit /proc/asound/card0/pcm0p/oss directly.

---

### Post by Hanj on 2007-01-25
Well, I found out the problem is with my sound card and is pretty well known (sorry, should have done a little more searching before posting). I read that using a program called joss might solve the problem, but I'm getting weird errors trying to compile it:
```

$: joss-0.4 > make
gcc -O2 -fPIC -c -Wall -DHAVE_IOCTL_INT_ULONG_DOTS  -o joss.o joss.c
ld -o joss.so joss.o -shared -ljack -lsamplerate
$: joss-0.4 > sudo make install
cp joss.so /usr/local/lib
sed 's%jossdir=/usr/local%jossdir=/usr/local%'< joss > /usr/local/bin/joss
/bin/sh: cannot open joss: No such file
make: *** [install] Error 2
$: joss-0.4 > 

```
Anyone know what's causing this?

---

### Post by Lord Illidan on 2007-01-25
How are you sure that the problem is being caused by your soundcard and nothing else? Can you give us more info about your system please?

---

### Post by Hanj on 2007-01-25
> How are you sure that the problem is being caused by your soundcard and nothing else? Can you give us more info about your system please?Well, I searched through these forums more carefully and found out that a lot of people have exactly the same problem, and apparently it's sound card related. After installation, there's no sound. After using the fix suggested in the guide, sound works but the game crashes. My sound card is an onboard NVidia CK804 by the way.

[Edit]I finally got joss to compile, but now I get this error when trying to run it:
```

/bin/sh: symbol lookup error: /usr/local/lib/joss.so: undefined symbol: __stack_chk_fail_local

``` Anyone?
[/Edit]

---

### Post by Hanj on 2007-01-26
Finally solved it! :D 
If anyone's interested, the solution was to add -fno-stack-protector to the CFLAGS variable in the Joss makefile and recompile it.

---

### Post by winzo on 2007-03-15
I have exactly the same problem Hanj, nv CK804 on Edgy AMD64, and I've done everything you have.

1) map quake3.x86 sound to pcm0p on /dev/dsp (im sure this is correct, the only other dsp in /dev is 'adsp', and that has a set of errors of its own ...)

2) compile and install joss with your CFLAGS addition

However, when I run  " $ jackd -d oss & joss quake ", i get this error from quake3:
> ------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

The game will then play without sound like it did before remapping to pcm0p or installing joss.
I've tried doing this with and without esd, and I still get that error.

I feel like I'm close and maybe missing something stupid, I just can't figure it out.  Any ideas?

---

### Post by sorcererx84 on 2007-03-15
Try using ioquake3 ([http://www.icculus.org/quake3)](http://www.icculus.org/quake3)). It has openal support and runs better sor me.

---

### Post by winzo on 2007-03-15
I guess I should've mentioned ... ioquake3 doesn't support punkbuster because its closed source, and pb is required to play on many popular servers online.

For the record though, yes, ioqauke3 does work on my machine. But getting the binary's sound to work is what I'm aiming for.

---

