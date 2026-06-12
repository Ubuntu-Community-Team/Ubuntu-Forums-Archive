---
title: "Issue compiling extra compiz plugins"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by jjgy on 2007-12-09
I found a tarball list for some of the extra compiz plugins, and decided to give it a go.  I ran into some issues compiling, but discovered I didn't have all of the required packages (According to [this]("http://forum.compiz-fusion.org/showthread.php?t=5303") thread at least.)  I fixed that issue, only to be greeted with a new set of compile errors.    I've been poking around both the compiz forums and these forums a bit, but can't seem to figure out why these packages won't compile for me.  I've tried a few of the premade scripts that seemed to work for everyone else, but I've just keep running into the same damn errors.  I'll let you take a look..

**Terminal output for compiz snow plugin**

```

[user]@[machine]:~/compiz/snow$ make
compiling : snow.c -> build/snow.loIn file included from snow.c:39:
build/snow_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from snow.c:39:
build/snow_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
snow.c:53: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
snow.c: In function 'stepSnowPositions':
snow.c:151: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c:151: error: (Each undeclared identifier is reported only once
snow.c:151: error: for each function it appears in.)
snow.c: In function 'snowToggle':
snow.c:194: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowPaintOutput':
snow.c:326: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowDrawWindow':
snow.c:359: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'updateSnowTextures':
snow.c:435: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowInitScreen':
snow.c:513: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowFiniScreen':
snow.c:552: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowDisplayOptionChanged':
snow.c:580: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowInitDisplay':
snow.c:680: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowFiniDisplay':
snow.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowInit':
snow.c:698: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowFini':
snow.c:708: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/snow.lo] Error 1

```

same issue applies with make install, and root privs don't solve anything.  Obviously, I'm a total linux newb, so any help at all is greatly appreciated.

---

### Post by PinkFloyd102489 on 2007-12-09
The attached tarball was taken from a guide on these forums.I cant find the guide right now, but I'll provide the steps.


1. Untar/gzip the archive
2. cd into the directory
3. Give executable permissions to plugins.sh
4. ./plugins.sh


It'll come up with a list to which you enter the appropriate number that you wish you install.

---

### Post by jjgy on 2007-12-09
Very handy script, but it doesn't change the problem.  These extra plugins just don't want to compile for some reason.  I'll take a gander through my repos and make sure I didn't end up with a weird compiz install somehow, but I'm fairly certain it's all good.  I'm a bit new to linux though, so I'm afraid hunting down a compile error isn't going to be something I'm any good at.  Oh, and before anyone asks, no,  I'm not on a  64bit :P

---

