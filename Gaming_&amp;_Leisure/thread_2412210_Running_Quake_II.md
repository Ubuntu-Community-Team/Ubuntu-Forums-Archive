---
title: "Running Quake II"
date: 2019-02-09
forum: Gaming &amp; Leisure
---

### Post by Notre on 2019-02-09
I've seen a few other posts on running Quake II ([https://ubuntuforums.org/showthread.php?t=56769&highlight=Running+Quake+II](https://ubuntuforums.org/showthread.php?t=56769&highlight=Running+Quake+II), [https://ubuntuforums.org/showthread.php?t=708908&highlight=Running+Quake+II](https://ubuntuforums.org/showthread.php?t=708908&highlight=Running+Quake+II), [https://askubuntu.com/questions/809204/game-package-manager-quake-2-install](https://askubuntu.com/questions/809204/game-package-manager-quake-2-install)) but they're either pretty old or I'm doing something wrong.

The last link is the most recent and seems like it 'should' work.  I tried this:

```

sudo apt-get install yamagi-quake2
sudo apt install quake2 game-data-packager
game-data-packager quake2 --package quake2-demo-data

```

The last command gave this output:
```

WARNING:game-data-packager.build:Failed to download "ftp://ftp.debian.nl/pub/idsoftware/idstuff/quake2/q2-314-demo-x86.exe": <urlopen error ftp error: error_perm('550 Failed to change directory.',)>
INFO:game-data-packager.build:downloading ftp://mirrors.syringanetworks.net/idgames/idstuff/quake2/q2-314-demo-x86.exe
INFO:game-data-packager.build:generating package quake2-demo-data

```

But, at the end of the day, I do have this file generated:

```
quake2-demo-data_44_all.deb
```


Ultimately, I want to run the full game and I have an original quake II DVD.  But I thought maybe running the demo might be easier to start with.

After all the above, I ran:

```
gdebi quake2-demo-data_44_all.deb
```

This gave this output:

```

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done

Quake II demo data files
 Quake II requires an engine and game data to play. This package contains
 the data from the demo version of id Software's game "Quake II", and was
 generated using the "game-data-packager" program from the Debian package of
 the same name.
 .
 To play Quake II using this data, install the quake2 package.
Need to be root to install packages

```


When I run ```
quake2
```, a dialog persistently appears that says this:

```
Missing data; see usr/share/doc/quake2/README.Debian
```

That file talks about the need to have game data.  A couple of excerpts from that file:

```
The Quake II engine requires game data to run.  The data is not freely
redistributable.  You should use the 'game-data-packager' tool to install it.
```


```
Demo files are freely downloadable and can also be packaged using
game-data-packager.
```

Can anyone please point me to where I'm going wrong?  I didn't manually copy any files to any locations. I assumed the installers/programs would handle all that. I'm running Ubuntu 16.04. Thank you!

---

### Post by CatKiller on 2019-02-09
> **Notre said:**
> 
Can anyone please point me to where I'm going wrong?  I didn't manually copy any files to any locations.

```
Need to be root to install packages

```

Use ```
sudo dpkg -i quake2-demo-data_44_all.deb
``` instead.

---

### Post by Notre on 2019-02-10
Awesome! That did it.  Thanks for the help! Now the demo version works perfectly!

I do have the full version on a DVD.  I can run this successfully under wine, but the framerates are not as good, so it'd be awesome to get this working with yamagi-quake2.

To that end, I tried to create the package for the full game install.  Instead of doing this:

```

game-data-packager quake2 --package quake2-demo-data

```

I instead did this:

```

game-data-packager quake2 --package quake2-full-data ./baseq2/

```

while in the ~/.wine/drive_c/Q2OEM folder.  The result of this attempt contains a bunch of output, with this at the top:

```

INFO:game-data-packager.build:identifying ./baseq2/pak0.pak
WARNING:game-data-packager.build:found possible "baseq2/pak0.pak" but it is not one of the expected versions:
    file:   ./baseq2/pak0.pak
    size:   70786697 bytes
    md5:    bd4f28ed19a4b47eb8066b5afd1d0507
    sha1:   ff62e618bd3a5ea894816fcec785ea632d8e2204
    sha256: 5ab14aa375d4e1cdbb20ef61ffc7f68dd9acd06283c049e26c27d8fba527ba89
expected one of:
  baseq2/pak0.pak?6be3f40:
    size:   194965474 bytes
    md5:    4f7dafbfb99c30d5455bc63003da8357
    sha1:   6be3f40f61ab9534d503316f95ac766cbfe6e77c
    sha256: 7fea4fe24b5871787962cd8f1df3bd55b93baf34fea5743e3f90fcc8e5675995
  baseq2/pak0.pak?demo:
    size:   49951322 bytes
    md5:    27d77240466ec4f3253256832b54db8a
    sha1:   None
    sha256: None
  baseq2/pak0.pak?1dd586a:
    size:   183997730 bytes
    md5:    1ec55a724dc3109fd50dde71ab581d70
    sha1:   1dd586a3230d1ac5bfd34e57cc796000d4c252c2
    sha256: 1ce99eb11e7e251ccdf690858effba79836dbe5e32a4083ad00a13ecda491679

```

Am I out of luck?

---

### Post by CatKiller on 2019-02-10
I've never come across the game-data-packager thing before. You could try simply copying the .pak files from the dvd or Wine directory to the install directory.

---

### Post by Notre on 2019-02-10
I think that did it - thanks again! :)

---

