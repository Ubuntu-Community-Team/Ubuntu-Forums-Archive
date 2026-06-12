---
title: "unmet dependencies"
date: 2009-04-16
forum: General Help
---

### Post by kingnebby on 2009-04-16
i have no clue here can some one give a hand

> The following packages have unmet dependencies:
  smplayer: Depends: libqt4-network (>= 4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
            Depends: libqt4-xml (>= 4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
            Depends: libqtcore4 (>= 4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
            Depends: libqtgui4 (>= 4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
E: Broken packages


---

### Post by mc4man on 2009-04-16
You should post whether you are using jaunty or intrepid.
In either case you have sources and or packages installed from both.

> smplayer: Depends: libqt4-network (>= [COLOR="Red"]4.5.0~+rc1[/COLOR]) but [COLOR="Blue"]4.4.3-0ubuntu1.2[/COLOR] is to be installed

Your (s)mplayer appears to be from a jaunty alpha source (red), but the intrepid version(s) (blue) of the dependencies is what's available from your source repo's

Maybe post your sources list
```
cat /etc/apt/sources.list
```


Note from jaunty changelog
> qt4-x11 (4.5.0-0ubuntu1) jaunty; urgency=low

  * New upstream release
  * Use lzma compression
  * Add 0274-shm-native-image-fix.diff from qt-copy

 -- Jonathan Riddell <jriddell@ubuntu.com>  Tue, 03 Mar 2009 13:31:00 +0000

qt4-x11 ([COLOR="Red"]4.5.0~+rc1-0ubuntu1[/COLOR]) jaunty; urgency=low

  * New upstream release candidate (rc1)
.....clippped
 Roderick B. Greening <roderick.greening@gmail.com>  [COLOR="Red"]Thu, 19 Feb 2009[/COLOR] 12:04:00 -0330




---

