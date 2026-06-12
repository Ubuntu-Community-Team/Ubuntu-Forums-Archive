---
title: "pSX wont start"
date: 2010-10-17
forum: Gaming &amp; Leisure
---

### Post by segamaster222 on 2010-10-17
Heres what the terminal gives me after .**./pSX**

> [src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

It opens for a split second then closes.

I tried 

> sudo apt-get install libgtkglext1

But no luck, but if I don't have that installed then PSX wont even come up for a split second

Anyone have any ideas as to what i could do? Thanks.

I don't have a TV at the moment and want to play some games :(

---

### Post by kotaro535 on 2010-10-17
Hmm...


Why don't you try PCSX Reloaded?.
It is much easier to use because it already comes up with plugins except for BIOS..

And I don't have any trouble using it.

---

### Post by segamaster222 on 2010-10-17
> **kotaro535 said:**
> Hmm...


Why don't you try PCSX Reloaded?.
It is much easier to use because it already comes up with plugins except for BIOS..

And I don't have any trouble using it.

Good idea i'll give it a try, I'm sure it will work with the 2 games I want to play

---

### Post by spai on 2010-10-17
> **segamaster222 said:**
> Heres what the terminal gives me after .**./pSX**



It opens for a split second then closes.

I tried 



But no luck, but if I don't have that installed then PSX wont even come up for a split second

Anyone have any ideas as to what i could do? Thanks.

I don't have a TV at the moment and want to play some games :(

I had the same problem. I could not fix it. So I am using epsxe for windows and running it on wine. It works fine :D

---

### Post by DoktorSeven on 2010-10-18
You need to disable PulseAudio.  Kill the pulseaudio process and it should work.

---

