---
title: "skulltag:    libFLAC++.so.5 cannot open shared object file"
date: 2007-12-01
forum: Gaming &amp; Leisure
---

### Post by mooglinux on 2007-12-01
I suddenly have an urge to play doom this afternoon, have tried using zdoom but it will not compile, prboom freezes and so does lxdoom.

so skulltag looks promising, but after i try to run it, installing all the dependancies, it gives me this message:
```
)$ ./skulltag.exe
./skulltag.exe: error while loading shared libraries: libFLAC++.so.5: cannot open shared object file: No such file or directory

```

so what do i have to fix for this? i checked synaptic and it looks like i have version 7 and 8 of libflac, so what on earth is going on?

any suggestions?

---

### Post by happyhamster on 2007-12-01
Apparently the game expects to find libFLAC++.so.5 but you have a later version. What you can do is make a symbolic link pointing to your version (in my case libFLAC++.so.6.0.1).

- In a terminal:

sudo ln -s  /usr/lib/libFLAC++.so.6.0.1 /usr/lib/libFLAC++.so.5

- Again assuming that libFLAC++.so.6.0.1 is your version. If not, you can determine the correct name using:

sudo updatedb 

- to update the search-database (this could take a minute). When it's finished:

locate libFLAC

---

### Post by blithen on 2007-12-02
Didn't work for me, anything else?

---

### Post by mooglinux on 2007-12-02
yea, no luck here either. still get the same message.

---

### Post by mooglinux on 2007-12-02
okay, perhaps i should clarify my situation a little.

i tried creating the symbolic link and the first time it took it without a message, presumably it worked. now if i try to create the link again, i get this message:

ln: creating symbolic link `/usr/lib/libFLAC++.so.5' to `/usr/lib/libFLAC++.so.6.0.1': File exists

is this saying that libFLAC++.so.5 exists? or that the symbolic link already exists?

---

### Post by dfreer on 2007-12-02
Why not check?
```
ls -l /usr/bin/libFLAC*
```

Furthermore, instead of linking a newer library to an older one (libflac++6 -> libflac++5c2), why don't you just install the older library? Granted, libflac++5c2 is not available in the Gutsy repositories, but you can easily grab it from feisty and install it.

Here's it's page:
[http://packages.ubuntu.com/feisty/libs/libflac++5c2](http://packages.ubuntu.com/feisty/libs/libflac++5c2)
and here's a direct download (for i386):
[http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac++5c2_1.1.2-5ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac++5c2_1.1.2-5ubuntu2.1_i386.deb)

I'd advise removing that symbolic link, it's only going to cause you problems later. -_-

---

### Post by disturbedite on 2007-12-02
yeah, thats what i was gonna say.  just install the libFLAC++5c2 from an older ubuntu release.

---

### Post by mooglinux on 2007-12-02
sounds good, but i have amd64 rather than i386, where can i get a download libflac++5c2 for amd64?

---

### Post by blithen on 2007-12-02
DId it same thing. I've been looking into the situation.
It's been a bug for awhile, and the problem is probably back from zDoom, they are having troubles with it 'cause zDoom isn't for linux.

---

### Post by mooglinux on 2007-12-02
well, no luck. i downloaded the package and installed it, removed the symbolic link, and same message. 

here is the output of ls -l /usr/lib/libFLAC*
```
-rw-r--r-- 1 root root 425776 2007-11-08 14:31 /usr/lib/libFLAC.a
-rw-r--r-- 1 root root 144176 2007-11-08 14:31 /usr/lib/libFLAC++.a
-rw-r--r-- 1 root root    820 2007-11-08 14:31 /usr/lib/libFLAC.la
-rw-r--r-- 1 root root    850 2007-11-08 14:31 /usr/lib/libFLAC++.la
lrwxrwxrwx 1 root root     16 2007-12-01 14:33 /usr/lib/libFLAC.so -> libFLAC.so.8.0.1
lrwxrwxrwx 1 root root     18 2007-12-01 14:33 /usr/lib/libFLAC++.so -> libFLAC++.so.6.0.1
lrwxrwxrwx 1 root root     18 2007-12-02 21:14 /usr/lib/libFLAC++.so.5 -> libFLAC++.so.5.0.0
-rw-r--r-- 1 root root 134432 2007-11-08 14:29 /usr/lib/libFLAC++.so.5.0.0
lrwxrwxrwx 1 root root     18 2007-12-01 14:33 /usr/lib/libFLAC++.so.6 -> libFLAC++.so.6.0.1
-rw-r--r-- 1 root root 105704 2007-11-08 14:31 /usr/lib/libFLAC++.so.6.0.1
lrwxrwxrwx 1 root root     16 2007-12-02 20:24 /usr/lib/libFLAC.so.7 -> libFLAC.so.7.0.0
-rw-r--r-- 1 root root 277952 2007-11-08 14:29 /usr/lib/libFLAC.so.7.0.0
lrwxrwxrwx 1 root root     16 2007-12-01 14:33 /usr/lib/libFLAC.so.8 -> libFLAC.so.8.0.1
-rw-r--r-- 1 root root 287936 2007-11-08 14:31 /usr/lib/libFLAC.so.8.0.1

```

looks like libFLAC++.so.5 is a symbolic link to libFLAC++.so.5.0.0
perhaps skulltag is looking in the wrong directory? in /usr/bin instead of /usr/lib?

---

### Post by dfreer on 2007-12-03
Run ldd on the executable, to see what it's looking for (not sure where your exectuble for skulltag is, but you probably do):
```
ldd ./skulltag
```

As for libflac++5c2, since you are running amd64 it makes things slightly different. Is this "skulltag" a 64-bit program, or 32-bit? If it's 64-bit, then you would use the 64-bit package of libflac++5c2 found here:
[http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac++5c2_1.1.2-5ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac++5c2_1.1.2-5ubuntu2.1_amd64.deb)

If it is a 32-bit program, then we'll need to use the 32-bit libraries of libflac++5c2. There is several ways of doing this, perhaps the simplest would be to extract the shared libraries directly into your /usr/lib32. The other would be for me to make a debian package of it, although if it's not needed in the first place, there is no point.

EDIT: on a side note, when you run the **ls -l /usr/lib/libFLAC*** command, you need to make sure that the symbolic links show up in *blue*, not *red*. If the symbolic links are for some reason messed up, they show up red.

---

### Post by disturbedite on 2007-12-03
> **blithen said:**
> ...and the problem is probably back from zDoom, they are having troubles with it 'cause zDoom isn't for linux.

thats not true, i compiled it myself.  there is a linux version.

EDIT:
unless you meant a 64bit version.... the fmod dependency of zdoom (and hence every port based on zdoom, such as skulltag) prevent them from being compiled on 64bit machines.  (since there is not a 64bit version of the fmod (3,75 is required) library.  but i conversed with the skulltag linux dev and he said that it might be possible to just the 32bit version of fmod with skulltag).

---

### Post by Gavla on 2007-12-12
I'm holding my breath, disturbedite. Yr praising of skulltag on this forum made me go and have a look at the website, and it looks like it might be my new doom port of choice... But I've not got any port working on my amd64.

When they make this work with our system, or at least someone writes the for dummies workaround, remind us, won't ya?

---

