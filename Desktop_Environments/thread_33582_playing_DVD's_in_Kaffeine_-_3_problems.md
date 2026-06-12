---
title: "playing DVD's in Kaffeine - 3 problems"
date: 2005-05-11
forum: Desktop Environments
---

### Post by joni on 2005-05-11
Hello, all.

First problem: I've installed libdvdcss2, but I'm still having some problems playing DVD's in Kaffeine.
For several commercial and recorded DVD's (using K3b), it says that "the source can't be read". For others, it is able to play all the DVD. Still for others, it plays the warning and the logo, but after that it displays the "source can't be read" message.

I don't have an internet access for that computer, so I've downloaded libdvdcss2 from [http://download.videolan.org/pub/libdvdcss/1.2.8/deb/libdvdcss2_1.2.8-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.8/deb/libdvdcss2_1.2.8-1_i386.deb), instead of using apt. (can this be the reason?)

I also found that libdvdread3 has to be installed. I haven't checked yet (not at home), but I assume it is, because I can play *some* DVD's.

Second problem: the subtitles always show some flickering

Third problem: Letters such as those in the warning sign, or even letter in menus show some lines, like it's interlaced.

Any solutions?

Thanks, in advance.

Joao

---

### Post by philipacamaniac on 2005-05-11
I don't know about where you got that .deb, so maybe you should download the one most of use (K)ubuntu users are using from ftp.nerim.net (marillat)

The specific file you want is [ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/libdvdcss2_1.2.8-sarge0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/libdvdcss2_1.2.8-sarge0.0_i386.deb)

I can't guarantee that's the solution, but since we trust the marillat repo, it is a safe bet.

---

