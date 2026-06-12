---
title: "HOW TO: Get 3d Windows working on Gutsy's default compiz"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by scottDkoDer on 2007-11-03
Well, for those that are using Gutsy and would like to have the additional eyecandy plug-in '3d Windows' working with Gutsy's default compiz-fusion, I'm presenting this guide.  This tutorial assumes that:

1) You already have Gutsy installed.
2) You already have Gutsy's default compiz working.
3) You are running as user and not root.

NOTE: compiz-fusion is installed by default in Ubuntu Gutsy and will work as long as you have a video card with appropriate drivers and proper configuration.  This is beyond the scope of this tutorial, but there are a plethora of guides to configure your graphics card on Gutsy.  Also, thanks to ArielTM of ubuntuforums.org for this informative information.

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
cd /tmp && wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
sudo chown $LOGNAME /usr/local/src && cd /usr/local/src
tar -xvf '/tmp/3d.tar.gz' && cd '3d'
make
sudo make install
```

If there are any problems, please check the prerequisites first, ensure you have followed all instructions and commands, and then post any problems or suggested changes here.  Otherwise, enjoy.

---

### Post by frodon on 2007-11-05
If you have time provide uninstall instructions for those who want to try this and wish to uninstall it if not satisfied of the result.

---

### Post by russo.mic on 2007-11-05
Just turn the option of 3d windows off if you don't like it.

---

### Post by dondolo on 2007-11-05
doesen't work for me

> convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h
bcop'ing  : build/3d.xml -> build/3d_options.c
schema    : build/3d.xml -> build/compiz-3d.schema
compiling : 3d.c -> build/3d.loIn file included from 3d.c:47:
build/3d_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from 3d.c:47:
build/3d_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
3d.c:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
3d.c: In function 'tdPreparePaintScreen':
3d.c:216: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c:216: error: (Each undeclared identifier is reported only once
3d.c:216: error: for each function it appears in.)
3d.c: In function 'tdPaintWindow':
3d.c:294: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdAddWindow':
3d.c:570: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintTransformedOutput':
3d.c:591: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintOutput':
3d.c:669: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdDonePaintScreen':
3d.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintTop':
3d.c:739: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintBottom':
3d.c:759: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkFirst':
3d.c:775: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkLast':
3d.c:782: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkNext':
3d.c:789: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkPrev':
3d.c:796: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindowWalker':
3d.c:803: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForDisplay':
3d.c:824: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForDisplay':
3d.c:880: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForScreen':
3d.c:907: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForScreen':
3d.c:929: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitDisplay':
3d.c:959: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniDisplay':
3d.c:969: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitScreen':
3d.c:981: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniScreen':
3d.c:1027: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindow':
3d.c:1044: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniWindow':
3d.c:1063: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInit':
3d.c:1070: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFini':
3d.c:1079: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/3d.lo] Error 1


---

### Post by adarkenigma on 2007-11-05
okay i follow the guide and it compiled right 

but i dont see no option for 3d window in ccsm?

---

### Post by xjgnsdof on 2007-11-12
It works perfectly on my end. The setting for 3D windows is under "Effects." For me, it's the first setting in that category.

---

### Post by mikeg113 on 2007-11-14
Sweet! Thanks, this worked like a charm for me! Would be possible to use this method to install the compiz screensaver plugin as well? [http://youtube.com/watch?v=Rmz9a9pJR_s]("http://youtube.com/watch?v=Rmz9a9pJR_s")

---

### Post by Redenbacher on 2007-11-14
Gave it a go and hit a wall, with the following error:

tar: /tmp/3d.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now



*NOTE* Copied and Pasted wrong - Ignore this!

---

### Post by Redenbacher on 2007-11-14
Got it working great, except that the 'substance' of the windows flickers when rotating the cube... any idea why?

Sorry for double post

---

### Post by Luci4 on 2007-11-15
Worked fine for me thanks!
although being a newbie, I don't yet know what I can do with this.... ;)

---

### Post by DaymItzJack on 2007-11-15
Worked for me also but it was choppy and I disabled it right away.

---

### Post by kamilek_snk on 2007-12-27
I have problem with "make"

```

compiling : 3d.c -> build/3d.loIn file included from 3d.c:47:
build/3d_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from 3d.c:47:
build/3d_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
3d.c:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
3d.c: In function 'tdPreparePaintScreen':
3d.c:216: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c:216: error: (Each undeclared identifier is reported only once
3d.c:216: error: for each function it appears in.)
3d.c: In function 'tdPaintWindow':
3d.c:294: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdAddWindow':
3d.c:570: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintTransformedOutput':
3d.c:591: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintOutput':
3d.c:669: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdDonePaintScreen':
3d.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintTop':
3d.c:739: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintBottom':
3d.c:759: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkFirst':
3d.c:775: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkLast':
3d.c:782: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkNext':
3d.c:789: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkPrev':
3d.c:796: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindowWalker':
3d.c:803: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForDisplay':
3d.c:824: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForDisplay':
3d.c:880: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForScreen':
3d.c:907: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForScreen':
3d.c:929: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitDisplay':
3d.c:959: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniDisplay':
3d.c:969: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitScreen':
3d.c:981: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniScreen':
3d.c:1027: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindow':
3d.c:1044: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniWindow':
3d.c:1063: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInit':
3d.c:1070: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFini':
3d.c:1079: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/3d.lo] Error 1
```

Anyone can help me, please ?

---

### Post by octesian on 2008-01-21
> **kamilek_snk said:**
> I have problem with "make"

```

compiling : 3d.c -> build/3d.loIn file included from 3d.c:47:
build/3d_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from 3d.c:47:
build/3d_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
3d.c:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
3d.c: In function 'tdPreparePaintScreen':
3d.c:216: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c:216: error: (Each undeclared identifier is reported only once
3d.c:216: error: for each function it appears in.)
3d.c: In function 'tdPaintWindow':
3d.c:294: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdAddWindow':
3d.c:570: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintTransformedOutput':
3d.c:591: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintOutput':
3d.c:669: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdDonePaintScreen':
3d.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintTop':
3d.c:739: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintBottom':
3d.c:759: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkFirst':
3d.c:775: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkLast':
3d.c:782: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkNext':
3d.c:789: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkPrev':
3d.c:796: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindowWalker':
3d.c:803: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForDisplay':
3d.c:824: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForDisplay':
3d.c:880: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForScreen':
3d.c:907: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForScreen':
3d.c:929: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitDisplay':
3d.c:959: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniDisplay':
3d.c:969: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitScreen':
3d.c:981: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniScreen':
3d.c:1027: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindow':
3d.c:1044: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniWindow':
3d.c:1063: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInit':
3d.c:1070: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFini':
3d.c:1079: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/3d.lo] Error 1
```

Anyone can help me, please ?

I have the same problem.

---

### Post by dark_phantom on 2008-01-21
I'll give it a try, posting to bookmark it. :)

---

### Post by octesian on 2008-01-27
I found a .deb on the compiz forums with all the unsupported plugins.  Unfortunately I cant remember where in the compiz forums.

---

### Post by ju5tin on 2008-02-22
Worked for me, many thanks

---

