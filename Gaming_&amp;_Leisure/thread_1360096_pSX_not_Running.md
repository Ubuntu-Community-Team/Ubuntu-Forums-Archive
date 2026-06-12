---
title: "pSX not Running"
date: 2009-12-20
forum: Gaming &amp; Leisure
---

### Post by dragonboss on 2009-12-20
Ok, so I downloaded pSX just now, extracted it to home folder when i run it it gives this  output:
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
How do I make it work?

---

### Post by dfreer on 2009-12-20
Used to work fine on older Ubuntu versions, I believe killing pulseaudio may allow it to still work on the latest Ubuntu.

---

### Post by dragonboss on 2009-12-20
Thanks. How do you kill pulseaudio again?

---

### Post by wheredidrealitygo on 2009-12-20
In case you can't figure out the pSX issue then you may also want to try out [PCSX-Reloaded]("http://www.codeplex.com/pcsxr"), works much better than the existing version of PCSX in the repos.

---

### Post by dragonboss on 2009-12-20
Thanks for the tip

---

### Post by thomaszmark on 2009-12-20
Thanks for your tips, I have the same situation, I will overcome this

---

### Post by hikaricore on 2009-12-20
I'd really like to see a new version of psx released so I can finally try it.
Out of the million possible workarounds none of them have ever worked for me.
I've been using epsxe for about 3 years now as no matter what pcsx and all it's forks produce white ground textures in all my games.
No matter what video plugin/configuration I try it's always the same, shame really too because pcsx works better.
Lets keep our fingers crossed the the psx developer has better audio support in the next release, hell even an option to disable it completely would be fine for a start.
Even nicer would be if he released the sourcecode, but I suspect there's a reason why this has not been done.

---

