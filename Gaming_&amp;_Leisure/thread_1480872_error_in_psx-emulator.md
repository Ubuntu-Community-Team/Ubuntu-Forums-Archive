---
title: "error in psx-emulator"
date: 2010-05-12
forum: Gaming &amp; Leisure
---

### Post by shini-kire on 2010-05-12
I have a problem with the emulator just closes when I select the language and the terminal receive this error:
```
$ psx-emulator
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Argumento inválido'
pad=0
AVISO: El proceso hijo terminado por la señal 11
``` 

please help with this problem I want to end the final fantasy 7 :P

used: ubuntu lucid (10.04)

---

### Post by WarrenSH on 2010-05-17
What emulator are you using for play the psx games?

---

### Post by shini-kire on 2010-05-17
> **WarrenSH said:**
> What emulator are you using for play the psx games?

ammm.. [http://www.ubuntugames.org/es/emulator/psx-emulator](http://www.ubuntugames.org/es/emulator/psx-emulator)

---

### Post by dfreer on 2010-05-17
Did you try all of the instructions on that page? Namely, killing pulseaudio and editing the .ini file?

---

### Post by shini-kire on 2010-05-17
> **dfreer said:**
> Did you try all of the instructions on that page? Namely, killing pulseaudio and editing the .ini file?

I did the setup and I get the following error:
```
$ sudo psx-emulator
Home directory /home/hikaru not ours.
Error en la conexión: Conexión rechazada
Home directory /home/hikaru not ours.
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Dispositivo ó recurso ocupado'
pSX: pcm_params.c:2274: snd_pcm_hw_refine: Afirmación `pcm && params' fallida.
AVISO: El proceso hijo terminado por la señal 6

```

how rare that I get in home folder .pSX   only appears in the folder ROOT :s

---

### Post by dfreer on 2010-05-18
> **shini-kire said:**
> I did the setup and I get the following error:
```
$ sudo psx-emulator
Home directory /home/hikaru not ours.
Error en la conexión: Conexión rechazada
Home directory /home/hikaru not ours.
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Dispositivo ó recurso ocupado'
pSX: pcm_params.c:2274: snd_pcm_hw_refine: Afirmación `pcm && params' fallida.
AVISO: El proceso hijo terminado por la señal 6

```

how rare that I get in home folder .pSX   only appears in the folder ROOT :s

When you run it with sudo, it's going to place it's configuration files in root. When you run it as a normal user it will place them in your home directory.

The pcm error may be fixed by following step 6 in the instructions you provided. However, knowing what device number to insert there can be a problem.

---

