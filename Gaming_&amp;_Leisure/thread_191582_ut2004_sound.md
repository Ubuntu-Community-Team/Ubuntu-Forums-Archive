---
title: "ut2004 sound"
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by kariopto on 2006-06-07
Hi!, I just installed ut2004 on my Ubuntu Daper amd64, and I'd like to be able to play while listening to xmms, I can do that with quake3, but not with ut2004.. I read somewhere that i have to run ut2004 with alsa and not oss.. but I have no idea how.. does anybody know how to fix this?
Thanks in advance

---

### Post by Gannin on 2006-06-07
You could always try to install a version of SDL that uses alsa, or compile one yourself, and then copy the appropriate libraries into UT2004's library directory.

Also, what output plugin are you using with XMMS?

---

### Post by kariopto on 2006-06-07
I have the pakcage libsdl1.2debian-alsa installed, what libraries do I have to copy to ut2004's library directory??.. 
I am using the alsa 1.2.10 output plugin on xmms..
thanks!

---

### Post by juicemansam on 2006-06-08
[QUOTE=kariopto]I have the pakcage libsdl1.2debian-alsa installed, what libraries do I have to copy to ut2004's library directory??.. 
I am using the alsa 1.2.10 output plugin on xmms..
thanks![/QUOTE]
I'd gzip/bzip2 the original libSDL-1.2.so.0 in UT's System directory. Then copy /usr/lib/libSDL-1.2.so.0.x.y.z into libSDL-1.2.so.0 in the System directory. Hope that helps.

---

### Post by kariopto on 2006-06-08
nope... I still have sound when i run it alone, but if i'm playing music with xmms, then I can't hear anything in the game..

---

### Post by Gannin on 2006-06-08
Now that I think about it, I think UT2004 uses OpenAL for sound.  See if there are any OpenAL libraries in UT2004's System directory, and if there are, do the same thing with them that you did with SDL.

---

### Post by kariopto on 2006-06-08
all right!!!.... It works!!.. thanks a lot!!..

---

### Post by Gannin on 2006-06-09
You're quite welcome.

---

