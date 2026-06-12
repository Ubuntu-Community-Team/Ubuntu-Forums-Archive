---
title: "Ksirk won't run after install"
date: 2010-02-04
forum: Gaming &amp; Leisure
---

### Post by troyer81 on 2010-02-04
Hello,

I've tried getting Ksirk to run with no luck.  I found it in the repositories and it installed with no errors, but when I type ksirk in the terminal window, I get the following message:

```
ksirk: error while loading shared libraries: libkdegames.so.1: cannot open shared object file: No such file or directory
```libkdegames5 is installed and /usr/lib/libkdegames.so.5 is present, but there is no libkdegames.so.1 symlink or library.  I tried to create another symlink to the same library (wild shot, but thought I'd see if it worked) and got the following:

```
ksirk: symbol lookup error: /usr/lib/libksirk_gamelogic.so: undefined symbol: _ZN5KGame4loadE7QStringb
```Yeah, I know I expected that.  I guess my question is - has anyone else had this problem?  Do I really need to find some package that installs the libkdegames.so.1 library?  I'd really like to play Ksirk, but I definitely don't want to go through the hassle of recompiling the binary.

FYI, the other kdegames games (kapman, kgoldrunner, etc.) run just fine, so it seems isolated to just ksirk.  I've tried reinstalling both packages to no avail.  Thanks in advance for any help.

Jon

---

