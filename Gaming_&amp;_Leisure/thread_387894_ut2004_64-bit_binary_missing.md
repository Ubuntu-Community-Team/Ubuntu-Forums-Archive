---
title: "ut2004 64-bit binary missing"
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by Admiral Frosty on 2007-03-18
I'm running Kubuntu 6.10, the AMD64 version. I've installed ut2004, the community bonus packs and the megapack from liflg, and it launches fails with this error:
```
frosty@eva-buntu:~$ sh ut2004
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

From looking around on the 'tubes, I saw that I had to point the launcher to the 64 binary, namely ut2004-bin-linux-amd64. Only issue is that I don't have one! I only have the plain 32-bit ut2004-bin. Where's my 64-bit binary!?

---

### Post by livingtarget on 2007-03-19
The installer should automatically install 64 bit binaries when you run the installer(s). 

Maybe it's not the installer, have you checked if you actually have libstdc++ ?

for 64 it should be "lib64stdc++6" I think, try installing that if you haven't got it.

Of course it asks for version 5 rather than 6, I'm sure you could try to symlink it. If you know how. Although this may cause problems.

You could attempt to install the 3369.2 patch independently as well and see if you can get the 64 binaries. If the patch comes in a tar.gz file you can manually check if it has the binary files in it. Should be in /System/ folder.

---

### Post by Admiral Frosty on 2007-03-19
Turns out that libstdc++6 was installed, but libstdc++5 wasn't. Installing that and then reinstalling the game makes it work just fine, until I install the megapatch, which makes it bail with this:

```
Assertion failed: sizeof(*this)==GetClass()->GetPropertiesSize() [File:UnGame.cpp] [Line: 149]

History:

Exiting due to error

```

This is a whole 'nother error, one which I've found all over the internet, so fixing it shouldn't be too hard. Thanks for your help!

---

