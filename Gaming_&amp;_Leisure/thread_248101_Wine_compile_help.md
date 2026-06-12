---
title: "Wine compile help"
date: 2006-08-31
forum: Gaming &amp; Leisure
---

### Post by tumler on 2006-08-31
Hey,
I'm just needing some help from someone who knows how to compile wine and include the dlls at the same time. As the wine binary already contains dlls why doesn't the compiled wine doe so?

I have already installed git,flex,bison,gcc and then I gotta install
```
sudo apt-get install xlibs-dev
```
to get x11 drivers working

getting wine
```
git clone git://source.winehq.org/git/wine.git wine-git
```

compiling
```
cd wine-git
./configure && make clean && make depend && make
```

When trying to run games it gets stuck at missing dlls.

Shouldn't there be a lib containing these dlls so they can get compiled? cause the binary has them.

---

### Post by croak77 on 2006-08-31
Why not use a binary? Or download the missing dll's and put them in your system32 folder. Or maybe the game(s) you are trying do not run in wine.

---

### Post by justin whitaker on 2006-09-01
Wine does not contain ALL the dlls....the most common ones, yes, but not all. Since you didn't list which games you are trying to run, check WineHQ and see if one of the workarounds requires additional dlls. Place the DLL in your wine directory with all the others, and give it another shot.

---

