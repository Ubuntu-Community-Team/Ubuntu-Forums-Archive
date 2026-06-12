---
title: "Playstation (One) Emulator problems"
date: 2008-11-12
forum: Gaming &amp; Leisure
---

### Post by DanielJackins on 2008-11-12
Hi,
I've been trying to get (two) playstation emulators to work, with little to no success. I downloaded pSX, and got the BIOS and everything, but after choosing the language upon start up it just shuts down. If I try it in the console it gives me this:

daniel@daniel-desktop:~/Desktop/pSX$ ./pSX 
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

The other emulator I've tried, ePSXe, will run the game (Final Fantasy VII, if it matters), but with several problems (can't seem to get it out of turbo, battle screens are black, sound problems, etc...)

Any help would be great, thanks a lot.

P.S - This is all on Intrepid Ibex

---

### Post by dfreer on 2008-11-12
Before running pSX:
```

sudo /etc/init.d/pulseaudio stop
sudo killall pulseaudio  ## if the first command didn't stop it

```
After running pSX:
```

sudo /etc/init.d/pulseaudio start

```

---

### Post by DanielJackins on 2008-11-12
Wow, it works perfectly :P
Thank you so much

---

### Post by Grishka on 2008-11-13
> **dfreer said:**
> Before running pSX:
```

sudo /etc/init.d/pulseaudio stop
sudo killall pulseaudio  ## if the first command didn't stop it

```
After running pSX:
```

sudo /etc/init.d/pulseaudio start

```

man, this looks like an overkill to me. simple "killall pulseaudio" does just that, it needs no root permissions, and it only has to be done once, not before every pSX session. also, I've found no upsides to restarting pulseaudio afterwards.

---

### Post by binbash on 2008-11-13
> **dfreer said:**
> Before running pSX:
```

sudo /etc/init.d/pulseaudio stop
sudo killall pulseaudio  ## if the first command didn't stop it

```
After running pSX:
```

sudo /etc/init.d/pulseaudio start

```

Thanks this fixed my problem also.I wrote a simple bash script for this.

---

### Post by dfreer on 2008-11-13
> **Grishka said:**
> man, this looks like an overkill to me. simple "killall pulseaudio" does just that, it needs no root permissions, and it only has to be done once, not before every pSX session. also, I've found no upsides to restarting pulseaudio afterwards.

Hmmm, so pulseaudio is run with the current user's permissions? That seems a little odd, why wouldn't it be run with root permissions? Well whatever, it most certainly gets the job done.

You **do** need to run it before every pSX session if you restart it afterwards, and if you are not planning on restarting pulseaudio afterwards, **why do you have it installed at all?**

---

### Post by Grishka on 2008-11-13
> **dfreer said:**
> Hmmm, so pulseaudio is run with the current user's permissions? That seems a little odd, why wouldn't it be run with root permissions? Well whatever, it most certainly gets the job done.

You **do** need to run it before every pSX session if you restart it afterwards, and if you are not planning on restarting pulseaudio afterwards, **why do you have it installed at all?**

the thing is, pSX works well on my system even with pulseaudio on after reboot. it's true that some applications will have garbled sound, or refuse to run at all with Intrepid pulseaudio setup. even so, 'killall pulseaudio', without root persmission, is all it takes for them to work. as you say, this won't stick after reboot in most cases, but in case of pSX, all I had to to is 'killall pulseaudio' once, start pSX, and set the audio card in the preferences from the 'default' setting to my card.

---

