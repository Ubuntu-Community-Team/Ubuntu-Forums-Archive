---
title: "New turn based strategy game : Conquest"
date: 2010-10-05
forum: Gaming &amp; Leisure
---

### Post by Naiki Muliaina on 2010-10-05
[http://www.conquest-game.com/](http://www.conquest-game.com/)

Wewt! Looks good, demo plays nice with Ubuntu 10.04. Heres hoping this is a good RTS, Linux needs a new and pretty one :)

---

### Post by Shazzner on 2010-10-06
Doesn't play nice on my system (10.04), sound doesn't work and it seems like it's using software rendering as the game is very slow. :(

---

### Post by Naiki Muliaina on 2010-10-06
Ack, I am using Ubuntu Studio 64 bit with everything installed on a beast of a PC (8gb ram, Nvidia 250gs 1gb, 3.4ghz quad core AMD). Ill have a poke when I get home and see how much ram / cpu it is using.

---

### Post by rettichschnidi on 2010-10-06
> **Naiki Muliaina said:**
> Heres hoping this is a good RTS, Linux needs a new and pretty one :)

It's a turn-based strategy game.

---

### Post by Shazzner on 2010-10-06
> **Naiki Muliaina said:**
> Ack, I am using Ubuntu Studio 64 bit with everything installed on a beast of a PC (8gb ram, Nvidia 250gs 1gb, 3.4ghz quad core AMD). Ill have a poke when I get home and see how much ram / cpu it is using.

I have an Nvid GTX 295 so that shouldn't be the reason why it's slow. I emailed support and they're thinking possibly one of the libraries included is old/broken so I should try to disable some.

Is there a way to see if you have newer versions of the libraries?

Edit: Yep, that's what did it. I created a temp folder and dragged these over (removing them from the Conquest Binaries folder):
libalut.so.0    libogg.so.0      libSDL_image-1.2.so.0
libGLEW.so.1.5  libopenal.so.1   libvorbisfile.so.3
libGUI.so       libSDL-1.2.so.0  libvorbis.so.0

So if anyone else has problems should try this.

---

### Post by gbear14275 on 2010-10-11
That didn't work for me... just threw a "/Binaries/Conquest.bin: error while loading shared libraries: libalut.so.0: cannot open shared object file: No such file or directory" error...

Did I miss a step?

---

### Post by _outlawed_ on 2010-10-11
Looks like a cool game, it's a shame that it is a intense GFX game. :(

Had to reboot as I started the demo and couldn't even do anything the GFX lag was so bad.

Stupid intel card. :(

---

### Post by Shazzner on 2010-10-11
> **gbear14275 said:**
> That didn't work for me... just threw a "/Binaries/Conquest.bin: error while loading shared libraries: libalut.so.0: cannot open shared object file: No such file or directory" error...

Did I miss a step?

Download libalut0 (I also grabed -dev version too) via synaptic package manager. Ditto for any other libraries it's missing.

---

### Post by gbear14275 on 2010-10-11
Did you have to put them anywhere in particular?  I got them with synaptic but it still says they are missing when I try to launch.

I'm guessing I may just have to restart...

---

### Post by Shazzner on 2010-10-11
> **gbear14275 said:**
> Did you have to put them anywhere in particular?  I got them with synaptic but it still says they are missing when I try to launch.

I'm guessing I may just have to restart...

No, basically when an application can't find a local library file it defaults to the system's library files, which are usually more compatible. So I'm guessing you may have grabbed the wrong file.

---

