---
title: "Unable to run homeworld-sdl in ubuntu 32 bit"
date: 2015-01-16
forum: Gaming &amp; Leisure
---

### Post by light2ultima on 2015-01-16
Hello everyone!

I have a Homeworld GOTY cd. I want to run game in my linux pc. It is Ubuntu 14.04 LTS 32 bit dual boot with Windows 7 Ultimate 32 bit.

I have installed the game in windows and it runs fine. As it can be played in linux so I decided to install it in linux.

So I have downloaded homeworld for linux from this [site](http://www.homesource.nekomimicon.net/downloads/stuff_for_testing/index.php?dir=&file=homeworldsdl-Linux-0.5alpha.tar.gz).

After doing neccecary settings [extracting archive to a directory, copying data files from cd and win directory to game directory]
when I typed:

```

./homeworld

```

in my  terminal I got following message displayed and game didn't run.

```

Scanning for newer files in .
Compared 36 filesystem files to main & update bigfiles.
0 files found newer than main bigfile in filesystem.
0 files found newer than update bigfile in filesystem.
Homeworld CRCs = 0x0 (not used) 0x52f110b0 (Homeworld.big's TOC) 0x291050b6 (Update.big's TOC) 0x0 (not used)
Assertion 'p' failed at pulsecore/memblock.c:836, function pa_mempool_block_size_max(). Aborting.
Aborted (core dumped)

```

I have allowed the executable execution permission by using 
```

chmod +x homeworld

```

I have searched for this issue in the web but found no solution. :(
I will be very grateful if anyone can help me to find the the cause of this error and possibly a solution.

Thank you.

I have downloaded the 0.4 binary archive also. Surprisingly this binary is running, although I am not getting the sound. This release has a *libs* folder where are some libraries. If I delete this folder then I also get a sound which is annoying, I hear a noise from the speaker and voice speed is very fast.

---

### Post by howefield on 2015-01-16
Thread moved to the "Gaming & Leisure" forum.

---

