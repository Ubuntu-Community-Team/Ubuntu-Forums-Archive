---
title: "Heroes 3 Linux Native- Choppy Sound"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by indeago on 2008-02-03
Hello, I just installed Heroes of Might and Magic 3 linux version by Loki...

I had two problems- choppy sound and game no going into full screen resolution.

The resolution problem was fixed when i applied the loki heroes 3 patch,

however, although the game plays smoothly

the sound is choppy and skips...

I read many forums and many people report this same issue, but i still haven't found a solution. 

I tried all the ALSA updates, etc. to no avail 

Did anyone have success fixing the sound bug? 

Thanks

---

### Post by Red Khan on 2008-04-22
I would like to up this thread, same problem here...

---

### Post by Doombringer on 2008-04-23
Not sure if it will help but I had a similar problem with another game and I had to change the sample rate from 44.1 kHz to 48K kHz. Not sure how to do it for Heroes 3 (great great great game !!!).

---

### Post by ryu kun on 2008-05-02
I have same problem with music in the game. I have hda-intel sound card and use Alsa 1.0.16 driver. Any help will be appreciated.

---

### Post by Yuri_Kenobi on 2008-05-03
Same thing here.
Does anyone not have this problem?

Though how did you apply the patch? Can't seem to make it work..

---

### Post by ryu kun on 2008-05-03
Hoping that installing latest patch might fix this problem, I tried to download it from official site [here]("http://www.lokigames.com/products/heroes3/updates.php3"), however all mirror ftp's were inactive. Then I found latest patch, 1.3.1, [here]("http://lokifiles.tuxgames.com/patches/heroes3/"), but it gives me this error when I run it:

> Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 3502225806 1601210390

Anybody succeed in patching Heroes 3 linux version? Did it solve this problem?

---

### Post by Yuri_Kenobi on 2008-05-03
Excatly the same problem here..](*,)

---

### Post by georginus on 2008-05-20
I haven't any trouble with the sound and fullscreen mode in HOMM3

But I'm a Gentoo user

If U want, I can say to U, how I won this bugs

P.S.: big sorry for my English

---

### Post by SlackerTD on 2008-05-20
ryu kun:

For that tail error, try running this before the running the patch:

export _POSIX2_VERSION=199209

I don't have this game, but I've seen a similar error with the Loki installer used for Lore. It might work for this game as well.

---

### Post by Ioky on 2008-06-13
I have this problem before, and I somehow magically fixed it. And now I reinstall the game, and I forget how I once fixed it. What can I say..... to myself. 

But I will let you know how I fix it, when I once again fix it some how magically.

---

### Post by sblatt on 2008-06-13
I just successfully installed the game!!! (on hardy)
It took me the following steps:
installation was easy, just use bash setup.sh (not ./setup.sh or sh setup.sh)

to update, i followed these steps (found [here]("http://wtanaka.com/node/7641"):

wget [ftp://mirrors.dotsrc.org/lokigames/updates/heroes3/heroes3-1.3.1a-unified-x86.run](ftp://mirrors.dotsrc.org/lokigames/updates/heroes3/heroes3-1.3.1a-unified-x86.run)

_POSIX2_VERSION=199209 ./heroes3-1.3.1a-unified-x86.run --keep

Download [http://downloads.sourceforge.net/goldenfiles/loki_patch-fix-0.1.tar.gz](http://downloads.sourceforge.net/goldenfiles/loki_patch-fix-0.1.tar.gz)

tar xvfz loki_patch-fix-0.1.tar.gz

cp Loki_patch-fix/fixedpatch heroes3-1.3.1a-unified-x86/bin/Linux/x86/loki_patch

./heroes3-1.3.1a-unified-x86/update.sh

now the game runs in fullscreen (or heroes3 -w for window)

but the sound was buggy (as described above).

so i found [this]("http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games") page, that told me a lot. if you are too lazy to read it all:

download [this]("http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.3.tar.bz2") file, extract it to /usr/local/lib/Loki_Compat/
and start the game by typing 

 LD_PRELOAD=/usr/local/lib/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/local/lib/Loki_Compat/libsmpeg-0.4.so.0.1.3:/usr/local/lib/Loki_Compat/libsmjpeg-0.2.so.0 /usr/local/games/Heroes3/heroes3.dynamic

actually i din't test it very well, i was so happy the sound worked, i just had to tell you ;)

oh, and on the above page it says that to start the game with 

LD_PRELOAD=/usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/local/games/Heroes3/heroes3.dynamic might be enough (didn't work for me)

the only problem i have now is that the resolution doesn't adjust to widescreen. any hints?

have fun

---

### Post by GepettoBR on 2008-08-20
> **sblatt said:**
> I just successfully installed the game!!! (on hardy)
It took me the following steps:
installation was easy, just use bash setup.sh (not ./setup.sh or sh setup.sh)

to update, i followed these steps (found [here]("http://wtanaka.com/node/7641"):

wget [ftp://mirrors.dotsrc.org/lokigames/updates/heroes3/heroes3-1.3.1a-unified-x86.run](ftp://mirrors.dotsrc.org/lokigames/updates/heroes3/heroes3-1.3.1a-unified-x86.run)

_POSIX2_VERSION=199209 ./heroes3-1.3.1a-unified-x86.run --keep

Download [http://downloads.sourceforge.net/goldenfiles/loki_patch-fix-0.1.tar.gz](http://downloads.sourceforge.net/goldenfiles/loki_patch-fix-0.1.tar.gz)

tar xvfz loki_patch-fix-0.1.tar.gz

cp Loki_patch-fix/fixedpatch heroes3-1.3.1a-unified-x86/bin/Linux/x86/loki_patch

./heroes3-1.3.1a-unified-x86/update.sh

now the game runs in fullscreen (or heroes3 -w for window)

but the sound was buggy (as described above).

so i found [this]("http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games") page, that told me a lot. if you are too lazy to read it all:

download [this]("http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.3.tar.bz2") file, extract it to /usr/local/lib/Loki_Compat/
and start the game by typing 

 LD_PRELOAD=/usr/local/lib/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/local/lib/Loki_Compat/libsmpeg-0.4.so.0.1.3:/usr/local/lib/Loki_Compat/libsmjpeg-0.2.so.0 /usr/local/games/Heroes3/heroes3.dynamic

actually i din't test it very well, i was so happy the sound worked, i just had to tell you ;)

oh, and on the above page it says that to start the game with 

LD_PRELOAD=/usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/local/games/Heroes3/heroes3.dynamic might be enough (didn't work for me)

the only problem i have now is that the resolution doesn't adjust to widescreen. any hints?

have fun

If I create a launcher with all those preloads, I get an error message from GNOME saying that the first file on the chain wasn't found (even though it's there) but it works if I paste it to the Terminal. Any idea what's going on?

---

