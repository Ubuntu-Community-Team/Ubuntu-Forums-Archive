---
title: "Compi-zFusion problem"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by Hawk__0 on 2007-11-29
Hey I accidentally added the extra plugins for fiesty, when i'm running gutsy, and then i apt-get updated it.
this is what i added to /etc/apt/sources.list:
 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

So after the update, obviously compiz-fusion crashes, and i cant get into the settings manager.  i tried "reinstalling" it with the package manager, and it didn't fix anything.  I have then removed the fiesty apt lines in sources.list, and im stuck.

what should i do?

---

### Post by santiagoward2000 on 2007-11-29
> **Hawk__0 said:**
> Hey I accidentally added the extra plugins for fiesty, when i'm running gutsy, and then i apt-get updated it.
this is what i added to /etc/apt/sources.list:
 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

So after the update, obviously compiz-fusion crashes, and i cant get into the settings manager.  i tried "reinstalling" it with the package manager, and it didn't fix anything.  I have then removed the fiesty apt lines in sources.list, and im stuck.

what should i do?

Hi!
Have you removed these repositories before reinstalling it?

---

### Post by Hawk__0 on 2007-11-29
no, but i was about to try.  guess ill try that now and see what happens :P haha.

---

### Post by santiagoward2000 on 2007-11-29
> **Hawk__0 said:**
> no, but i was about to try.  guess ill try that now and see what happens :P haha.

Haha! Tell us how that goes!

---

### Post by Hawk__0 on 2007-11-29
ok it all works now, thanks!

but my initial problem still persists... 
Is there any way to get snow and the other extra plugins to work under gutsy??
EDIT: and the 3d windows option, i miss that

---

### Post by santiagoward2000 on 2007-11-29
> **Hawk__0 said:**
> ok it all works now, thanks!

but my initial problem still persists... 
Is there any way to get snow and the other extra plugins to work under gutsy??

Well, yes, but you'll have to compile them yourself. I did it following this guide:
[http://forum.compiz-fusion.org/showthread.php?t=5303]("http://forum.compiz-fusion.org/showthread.php?t=5303")
And they are working quite well... (except for some small thing with freewins and my quit button, which I haven't solved yet :( )

---

### Post by Hawk__0 on 2007-11-29
ok thanks, thats wicked i didn't know some of those plugins existed... however.. i can't seem to compile any of them!
i downloaded all the dependencies that are listed there... and whenever i compiled stars or snow (haven't tried others yet) i get this:
```
steve@steve:~/compiz/stars-0.6$ make
convert   : star.xml.in -> build/star.xml
bcop'ing  : build/star.xml -> build/star_options.h
bcop'ing  : build/star.xml -> build/star_options.c
schema    : build/star.xml -> build/compiz-star.schema
compiling : star.c -> build/star.loIn file included from star.c:44:
build/star_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from star.c:44:
build/star_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
star.c:58: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
star.c: In function 'stepSnowPositions':
star.c:179: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c:179: error: (Each undeclared identifier is reported only once
star.c:179: error: for each function it appears in.)
star.c: In function 'snowToggle':
star.c:222: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowPaintOutput':
star.c:361: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowDrawWindow':
star.c:394: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'updateSnowTextures':
star.c:484: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowInitScreen':
star.c:562: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowFiniScreen':
star.c:601: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowDisplayOptionChanged':
star.c:629: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowInitDisplay':
star.c:729: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowFiniDisplay':
star.c:738: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowInit':
star.c:773: error: 'displayPrivateIndex' undeclared (first use in this function)
star.c: In function 'snowFini':
star.c:783: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/star.lo] Error 1

```

---

### Post by Takster on 2007-11-29
[http://ubuntuforums.org/showpost.php?p=3816927&postcount=1](http://ubuntuforums.org/showpost.php?p=3816927&postcount=1)

---

### Post by Hawk__0 on 2007-11-29
tha was a really sweet find, but i still can't compile them :(
```

steve@steve:~/Desktop$ chmod 755 plugins.sh 
steve@steve:~/Desktop$ ./plugins.sh 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-bcop is already the newest version.
compiz-dev is already the newest version.
build-essential is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgconf2-dev is already the newest version.
librsvg2-dev is already the newest version.
libdbus-1-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libgnome-desktop-dev is already the newest version.
x11proto-scrnsaver-dev is already the newest version.
libxss-dev is already the newest version.
libxslt1-dev is already the newest version.
libtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

  Choose a plugin that you'd like to install
  [1] 3d Windows
  [2] Atlantis2
  [3] Anaglyph
  [4] Freewins
  [5] Photowheel
  [6] Screensaver
  [7] Snow
  [8] Falling Leaves
--> 7
--18:49:44--  http://gitweb.opencompositing.org/?p=fusion/plugins/snow;a=snapshot;h=01d0ff6ec71dae4699bc990e0114569c8ad4e083
           => `/tmp/snow.tar.gz'
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [  <=>                                ] 8,710         24.64K/s             

18:49:45 (24.58 KB/s) - `/tmp/snow.tar.gz' saved [8710]

convert   : snow.xml.in -> build/snow.xml
bcop'ing  : build/snow.xml -> build/snow_options.h
bcop'ing  : build/snow.xml -> build/snow_options.c
schema    : build/snow.xml -> build/compiz-snow.schema
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
This does not have a snowflake image set. To set it, go into your settings manager and add the following string
/usr/share/ccsm/images/snowflake.png
steve@steve:~/Desktop$ 


```

---

### Post by santiagoward2000 on 2007-11-29
Sorry, I don't know what could be wrong...

---

### Post by Hawk__0 on 2007-11-29
arg...
i always get errors when i compile.  i dont know why.
i have build-essential, and gcc.
i installed all the requirements...
why!?
WHYYYYYYY!?

:(

---

### Post by Takster on 2007-11-29
what version compiz are you using, i think you are getting this because it is old.
> 
Your version of compiz is too old to compile directly against the git version of anaglyph.

```
tak@Ubuntu:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                            Compiz option code generator
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1         Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1                  Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1                Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1                  Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings
tak@Ubuntu:~$
```

---

### Post by Hawk__0 on 2007-11-29
```
ii  compiz                                     1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager
ii  compiz-bcop                                0.6.100~git20070906+3v1ubuntu0       Compiz option code generator
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1    Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
steve@steve:~/Desktop$ 


```

---

### Post by Takster on 2007-11-29
Looks like one for the [http://forum.compiz-fusion.org/index.php](http://forum.compiz-fusion.org/index.php) guys to figure out. :)

---

### Post by Hawk__0 on 2007-11-30
I have tried google and the compiz community forum, so far no good.  I did however find that im not the only user getting this problem.  Is there really nobody out there that found a fix for this??
BUMP!!

---

