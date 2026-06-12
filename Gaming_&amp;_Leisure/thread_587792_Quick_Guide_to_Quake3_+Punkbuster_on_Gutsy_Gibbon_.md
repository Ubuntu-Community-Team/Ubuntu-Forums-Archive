---
title: "Quick Guide to Quake3 +Punkbuster on Gutsy Gibbon x86_64"
date: 2007-10-23
forum: Gaming &amp; Leisure
---

### Post by otac0n on 2007-10-23
to prep and get the installer, do:
```

you@yourpc:~$ sudo apt-get install ia32-libs ia32-libs-sdl
you@yourpc:~$ wget ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run

```


in the meantime, do:
```

you@yourpc:~$ sudo mkdir -p /usr/local/games/quake3/baseq3

```
(Now, copy your pak0.pk3 into the new baseq3 directory.)


once both are complete, to set up quake, do:
```

you@yourpc:~$ sudo linux32 sh linuxq3apoint-1.32b-3.x86.run

```
(Go through the setup with default answers.)


to update to 1.32c, do:
```

you@yourpc:~$ wget ftp://ftp.idsoftware.com/idstuff/quake3/quake3-1.32c.zip
you@yourpc:~$ cd /usr/local/games/quake3
you@yourpc:/usr/local/games/quake3$ sudo unzip -fo ~/quake3-1.32c Quake\ III\ Arena\ 1.32c/linux/q3ded
you@yourpc:/usr/local/games/quake3$ sudo unzip -fo ~/quake3-1.32c Quake\ III\ Arena\ 1.32c/linux/quake3-smp.x86
you@yourpc:/usr/local/games/quake3$ sudo unzip -fo ~/quake3-1.32c Quake\ III\ Arena\ 1.32c/linux/quake3.x86
you@yourpc:/usr/local/games/quake3$ cd ~
you@yourpc:~$ rm quake3-1.32c.zip

```

YAY! all done. To launch quake, do:
```

you@yourpc:~$ quake3

```
(Now, exit quake.)

to update punkbuster, do:
```

you@yourpc:~$ cd ~/.q3a/pb
you@yourpc:~$ wget http://www.evenbalance.com/downloads/pbweb.x86
you@yourpc:~$ chmod +x pbweb.x86
you@yourpc:~$ ./pbweb.x86

```

Now, have fun!

Yeah, Gutsy is really my first time installing linux on my home PC.  So far so good, except I'm missing sound. :(

Good luck!

edit:
found this for use as a launcher icon ;)
[http://de.wikipedia.org/wiki/Bild:Quake_3_Logo.svg](http://de.wikipedia.org/wiki/Bild:Quake_3_Logo.svg)

---

### Post by Virtus92 on 2008-01-17
Thx, nice. I think I'm gonna use this for my site.
I hope that's ok?

---

### Post by disturbedite on 2008-01-17
just a quick question...
why does anyone still use the official q3?
ioquake3 (the continuation of q3 development & bug fixing) is already all the way up to version 1.35.

it works great & i'm using it...

i suppose if one really, really wants to use punkbuster, that might be a reason tho.  but ioquake3 supports playing on other networks & servers.

---

### Post by Virtus92 on 2008-01-20
Ok, I'll check that out. But I don't think it's as good as the original.

---

### Post by disturbedite on 2008-01-20
it IS the original, q3 has been open sourced so the community is providing updates to q3.  a new name had to be created simply to distinguish the updates from ID software, from what i understand.

---

### Post by supernova_hq on 2008-01-29
I can't get the game to go fullscreen. Even if i go into "System", "Display" and the set "fullscreen" to "on", i even tried "off" then "on".

Anyone else have this problem (or find a solution)?

Edit: also don't have sound (like you mentioned).

---

### Post by LeDechaine on 2008-02-09
hmm. I'm guessing this thread is about the "complete" game and not the demo, since **linuxq3apoint-1.32b-3.x86.run** is a patch.
(At least, according to one or two websites..)

---

