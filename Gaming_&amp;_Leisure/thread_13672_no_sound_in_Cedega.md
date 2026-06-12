---
title: "no sound in Cedega"
date: 2005-02-02
forum: Gaming &amp; Leisure
---

### Post by urielka on 2005-02-02
i installed Ubuntu Hoary and update everything.
when i play games in Cedega(4.2.1) i go t no sound and checking the console output give me this:

ALSA lib pcm_hw.c:1172:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device o r resource busy
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory

and then continue.

i have a O/B sound card in the southbrige VT8233A(via chipset) a P4 2.4GHZ and 512MB DDR RAM.

i got sound in all the apps(expect cedega).

plz help me

(sorry about my bad english)

---

### Post by mike998 on 2005-02-02
I had this problem.
Try disabling the sound server on startup (found under Computer > Desktop Settings, I belive) and restarting your X session.

---

### Post by piedamaro on 2005-02-02
[QUOTE=mike998]I had this problem.
Try disabling the sound server on startup (found under Computer > Desktop Settings, I belive) and restarting your X session.[/QUOTE]
 Or enable software mixing to hear multiple sounds at once. There is an howto in the howto section.

---

### Post by urielka on 2005-02-02
thx i hope it will work ;)
UPDATE: i can`t find it on the howto section can you give me a link to the howto?
ok i found it :p

---

### Post by urielka on 2005-02-04
it doesn`t work i got the same error!
but when i uncheck the "Enable sound server startup" it work

---

### Post by mike998 on 2005-02-04
Actually I am getting the same problem, hence the reason why I suggested disabling the sound server.  That's what works for me.  I also have some strange problems playing Star Trek : Elite Force where the cinematics and voiceovers will cut out and "stutter".

I have tried the multiple sound source how-to, but it hasn't worked.  It's a low priority problem for me right now, but it would be nice to play some games while I have XMMS playing.

---

### Post by urielka on 2005-02-04
just disable the sound startup and it will work and when you finish playing enbale it
that work for me

---

### Post by piedamaro on 2005-02-04
I have it working WITH desktop sounds together. After configuring software mixing, I've configured cedega to use alsadrv and I've disabled nmap (always in ~/.transgaming/config). If you disable esd, firefox can't produce sound. Hope this helps.

---

