---
title: "How to install PSX in 10.10?"
date: 2010-10-12
forum: Gaming &amp; Leisure
---

### Post by ThePhysician on 2010-10-12
I've been looking all over for a guide on how to install PSX emulator on Ubuntu 10.10 but can't find anything.

I got it extracted to /home/xan/Games/pSX and have the correct BIOS installed but clicking "PSX" just does nothing at all.

I think I'm missing the required dependencies, which I can't find a proper download for any longer. All the guides either use the terminal to download them on older versions of Ubuntu, or link to a deb of the dependency which is no longer available to download.

Thanks.

---

### Post by DoktorSeven on 2010-10-12
If you open a terminal and type
```

cd ~/Games/pSX/
./pSX

```
what happens?

---

### Post by ThePhysician on 2010-10-12
After trying to run it in the terminal, I found out what dependency was missing and I installed it through the package manager. 

Now when I try to run it in the terminal, this is the error I receive:

```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

Any suggestions?

Edit: Also, this is after the menu pops up asking me to select the language and I hit okay. Then it returns that error.

---

### Post by DoktorSeven on 2010-10-12
A search for that error shows suggestions to remove or turn off PulseAudio, e.g. this thread: 
[http://ubuntuforums.org/showthread.php?t=973021](http://ubuntuforums.org/showthread.php?t=973021)

pSX works fine here, but I don't have PulseAudio installed at all.

---

### Post by ThePhysician on 2010-10-12
Upon doing that it will launch now with very laggy sound with the terminal infinitely repeating "sound: underrun" until I close pSX. 

Gahhh.

---

### Post by DoktorSeven on 2010-10-12
It will do the sound underrun quite a few times in the terminal for me as well but sound isn't laggy. 

Try playing with the sound latency options under pSX configuration.

Also, have you tried ePSXe?  I generally use both since if I can't get a PS1 game working well under one, I use the other.  It's a bit more of an effort to get running particularly under GNU/Linux since it has all the plugin stuff but if you can get it going, it's a great emulator.

---

