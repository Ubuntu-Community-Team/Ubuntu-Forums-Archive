---
title: "I want to install xmame"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by Zerocool10482 on 2005-12-25
Hi, I just wanted to know how to install xmame or any program that runs ROMs. I know there are other postings but they don't every answer the question. :confused: The package manager doesn't have xmame. Or I can't find it. I'm a total newbie and I'm tried everything. Please make it easy. I just want to know if I can run ROMs. Thanks

---

### Post by The Warlock on 2005-12-25
The package manager does have xmame, just make sure you have the universe repositories enabled. It should also have snes9x, gens, and visualboyadvance, if you like those kind of things. There are non-repository Linux versions of ePSXe. I think there's an N64 emulator somewhere too. No Saturn emulator, but then, the ones for Windows are quite flaky as well.

---

### Post by leech on 2005-12-28
The version of xmame in the Ubuntu repositories is quite old.  What you'll want to do is to go to [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=xmame&searchon=names&subword=1&version=unstable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=xmame&searchon=names&subword=1&version=unstable&release=all) and download xmame-common, xmame-sdl, and xmame-tools.  Then in a terminal you can just do 

```
sudo dpkg -i xmame*
```

Afterwards you'll probably want to use gxmame as well.  The package at [http://thefnords.org/gxmame_0.35beta2-1_i386.deb](http://thefnords.org/gxmame_0.35beta2-1_i386.deb) should work for you.

Leech

---

### Post by nolan- on 2005-12-28
There is a howto posted in the forums mate :-

[HTML]http://www.ubuntuforums.org/showthread.php?t=86213&highlight=wine[/HTML]

I installed no problems at all using this guide....

Nol

---

