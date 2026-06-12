---
title: "pSX Soundproblem"
date: 2010-02-25
forum: Gaming &amp; Leisure
---

### Post by athelas on 2010-02-25
Hello everybody.

I tried to install pSX on Ubuntu 9.10 64bit. After installing I got this message:

```

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams, SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```But I could fix this with changing everything under Sound in the psx.ini file to "0" and frequency to "8000". Afterwards pSX started, but without Sound and I get this message in the console:

```

Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64

```I have  installed all 32bit libs with getlibs, but it looks like pSX tries
to find these libs under /usr/lib/... instead of /usr/lib32/...
I've found in other threads that it helps to end pulseaudio, but then pSX 
doesn't start at all anymore.

Many thanks

---

