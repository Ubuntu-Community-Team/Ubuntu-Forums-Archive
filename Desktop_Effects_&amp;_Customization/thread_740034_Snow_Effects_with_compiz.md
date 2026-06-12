---
title: "Snow Effects with compiz"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by JayDeePlus on 2008-03-30
ok........i'm something of a noob since coming back to ubuntu.........alot has changed.......when i was last here beryl was the desktop plugin for the 3d envirnment.........now it's compiz............

so i'm sure someone else has asked this but.........where do i get the install for the snow/autumn effect and how do i enable in compiz?.........

---

### Post by el_ricardo on 2008-03-30
i think the snow plugin is one of the experimental plugins that you have to compile yourself. It's called snowglobe now, and there's a howto [here]("http://forum.compiz-fusion.org/showthread.php?t=5303").

---

### Post by JayDeePlus on 2008-03-30
El Ricardo thankx man..........ur help kicked A**!!!!..........lol.............i appreciate it man.............i'll bring this back up if i have ne questions........

---

### Post by JayDeePlus on 2008-03-30
actually after trying to go through some of the steps.......... i think i do have some questions now......lol

> 
Extracting the source code

Example: For 3D Windows, you would do this:
Code:

tar -xf '/tmp/3d.tar.gz' -C ~/compiz/

This creates a directory at ~/compiz/3d.

Compiling a plugin after extraction
Switch to the directory created from extracting the tarball.


Example: For Freewins, you would do this:
Code:

cd ~/compiz/freewins-0.3-0.6

Once you are in the directory, you can compile the plugin:

Code:

make
make install


i have done this and still do now know how to add snow effect to evirnent........i do now see the option to enable snow effect in CCSM........is theyre something i'm missing?............i am a real noob on unix.......lol....

but it's saying.......it's not fully walking this out...........i mean ok he saying compile the plugin after extraction......but i don't kno what is the directory the plugin extracted to..........how do i figure that out..........

also.........what is freewins?..............is it something i should have with my version of ubuntu 7.10?...............is it something that i already have with my version and i juss don't kno how to get to it?.............

finally.........is there a complete guide with links to these plugins or do i have to use the terminal every time i need to add upgrade?.........if so........is there like a 101 page on all these codes i'll need to learn so i can properly work through ........ i'm feeling really stupid trying to do stuff.............:lolflag:

---

### Post by el_ricardo on 2008-03-30
freewins is one of the plugins, it allows you to move windows in 3d, so you can tilt them, rotate them etc. that tutorial isn't just for the snow plugin, it's for all the experimental plugins. Here's how you'd install snow:

1. install dependancies

```

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

```

2. make a directory for all your plugins to download to

```

mkdir -p  ~/compiz/

```

3. download the plugin's source

```

wget -O /tmp/snow.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugins/snow;a=snapshot;h=01d0ff6ec71dae4699bc990e0114569c8ad4e083'

```

5. extract, and compile the source

```

tar -xf '/tmp/snow.tar.gz' -C ~/compiz/

```

```

cd ~/compiz/snowglobe

```
[I]
"snowglobe" should be the name of the directory, but if it's not, check by doing "ls ~/compiz" (without quotes)[/I]

```

make
make install

```

6. If all has gone to plan, the snowglobe plugin should now be installed, now just restart X (ctrl+alt+backspace)

now you should be able to access it in the ccsm

hope that helps!

---

### Post by jryprt on 2008-03-30
.......

---

### Post by JayDeePlus on 2008-03-31
that last reply "try my guide" helped alot...........i think i got it from here...........thnx so much for the help.........

---

### Post by JayDeePlus on 2008-04-17
> TRY My Guide

what can't i access this like no more?.............i recently upgrade(with a from copy of hardy and the upgrade with 7.10)..........and it erased all my settings...........got do i get this back?........

---

### Post by JayDeePlus on 2008-04-18
still need help with this

---

### Post by jryprt on 2008-04-18
> **JayDeePlus said:**
> what can't i access this like no more?.............i recently upgrade(with a from copy of hardy and the upgrade with 7.10)..........and it erased all my settings...........got do i get this back?........

I had that thread closed had a misunderstanding . I just put the tarball back up.
[Here is the link](http://ubuntuforums.org/showthread.php?p=4079057#post4079057) to the thread.

---

### Post by JayDeePlus on 2008-04-18
this is what i get when i click that link


> JayDeePlus, you do not have permission to access this page. This could be due to one of several reasons:

   1. Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
   2. If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.


do i need to be a mod or something to view this?.......

---

### Post by jryprt on 2008-04-18
> **JayDeePlus said:**
> this is what i get when i click that link




do i need to be a mod or something to view this?.......

It must be locked .
Try [This link](http://members.cox.net/mushroomlake/Compiz.html)

---

### Post by JayDeePlus on 2008-04-18
i get this when i try to wget and sudo make install the snow tar


> jaydee@jaydee-desktop:~/compiz/snow$ make
compiling : snow.c -> build/snow.loIn file included from snow.c:39:
build/snow_options.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/snow_options.h:109: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/snow_options.h:110: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
snow.c:68: error: expected specifier-qualifier-list before ‘CompTexture’
snow.c:95: error: expected specifier-qualifier-list before ‘PaintOutputProc’
snow.c: In function ‘snowThink’:
snow.c:117: error: dereferencing pointer to incomplete type
snow.c:119: error: dereferencing pointer to incomplete type
snow.c:121: error: dereferencing pointer to incomplete type
snow.c:122: error: dereferencing pointer to incomplete type
snow.c:127: error: dereferencing pointer to incomplete type
snow.c: In function ‘stepSnowPositions’:
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:154: error: ‘TRUE’ undeclared (first use in this function)
snow.c:154: error: (Each undeclared identifier is reported only once
snow.c:154: error: for each function it appears in.)
snow.c:156: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:157: error: dereferencing pointer to incomplete type
snow.c:158: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:169: error: dereferencing pointer to incomplete type
snow.c:169: error: ‘CompWindowTypeDesktopMask’ undeclared (first use in this function)
snow.c:170: warning: implicit declaration of function ‘addWindowDamage’
snow.c:170: warning: nested extern declaration of ‘addWindowDamage’
snow.c:174: warning: implicit declaration of function ‘damageScreen’
snow.c:174: warning: nested extern declaration of ‘damageScreen’
snow.c:177: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:181: error: expected declaration specifiers or ‘...’ before ‘CompAction’
snow.c:182: error: expected declaration specifiers or ‘...’ before ‘CompActionState’
snow.c: In function ‘snowToggle’:
snow.c:189: warning: implicit declaration of function ‘getIntOptionNamed’
snow.c:189: warning: nested extern declaration of ‘getIntOptionNamed’
snow.c:190: warning: implicit declaration of function ‘findScreenAtDisplay’
snow.c:190: warning: nested extern declaration of ‘findScreenAtDisplay’
snow.c:190: warning: assignment makes pointer from integer without a cast
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:200: error: ‘TRUE’ undeclared (first use in this function)
snow.c:201: warning: control reaches end of non-void function
snow.c: In function ‘setupDisplayList’:
snow.c:224: error: dereferencing pointer to incomplete type
snow.c:226: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:226: warning: implicit declaration of function ‘glGenLists’
snow.c:226: warning: nested extern declaration of ‘glGenLists’
snow.c:228: warning: implicit declaration of function ‘glNewList’
snow.c:228: warning: nested extern declaration of ‘glNewList’
snow.c:228: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:228: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:229: warning: implicit declaration of function ‘glBegin’
snow.c:229: warning: nested extern declaration of ‘glBegin’
snow.c:229: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:231: warning: implicit declaration of function ‘glColor4f’
snow.c:231: warning: nested extern declaration of ‘glColor4f’
snow.c:232: warning: implicit declaration of function ‘glVertex3f’
snow.c:232: warning: nested extern declaration of ‘glVertex3f’
snow.c:240: warning: implicit declaration of function ‘glEnd’
snow.c:240: warning: nested extern declaration of ‘glEnd’
snow.c:241: warning: implicit declaration of function ‘glEndList’
snow.c:241: warning: nested extern declaration of ‘glEndList’
snow.c: In function ‘beginRendering’:
snow.c:248: error: dereferencing pointer to incomplete type
snow.c:249: warning: implicit declaration of function ‘glEnable’
snow.c:249: warning: nested extern declaration of ‘glEnable’
snow.c:249: error: ‘GL_BLEND’ undeclared (first use in this function)
snow.c:251: warning: implicit declaration of function ‘glTexEnvf’
snow.c:251: warning: nested extern declaration of ‘glTexEnvf’
snow.c:251: error: ‘GL_TEXTURE_ENV’ undeclared (first use in this function)
snow.c:251: error: ‘GL_TEXTURE_ENV_MODE’ undeclared (first use in this function)
snow.c:251: error: ‘GL_MODULATE’ undeclared (first use in this function)
snow.c:253: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘FALSE’ undeclared (first use in this function)
snow.c:260: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:260: error: dereferencing pointer to incomplete type
snow.c:264: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:266: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:267: error: dereferencing pointer to incomplete type
snow.c:268: error: dereferencing pointer to incomplete type
snow.c:270: warning: implicit declaration of function ‘enableTexture’
snow.c:270: warning: nested extern declaration of ‘enableTexture’
snow.c:270: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:271: error: ‘COMP_TEXTURE_FILTER_GOOD’ undeclared (first use in this function)
snow.c:275: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:277: warning: implicit declaration of function ‘glTranslatef’
snow.c:277: warning: nested extern declaration of ‘glTranslatef’
snow.c:279: warning: implicit declaration of function ‘glRotatef’
snow.c:279: warning: nested extern declaration of ‘glRotatef’
snow.c:280: warning: implicit declaration of function ‘glCallList’
snow.c:280: warning: nested extern declaration of ‘glCallList’
snow.c:280: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:287: warning: implicit declaration of function ‘disableTexture’
snow.c:287: warning: nested extern declaration of ‘disableTexture’
snow.c:287: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:292: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:293: error: dereferencing pointer to incomplete type
snow.c:299: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:306: error: ‘GL_REPLACE’ undeclared (first use in this function)
snow.c:307: error: dereferencing pointer to incomplete type
snow.c:309: warning: implicit declaration of function ‘glDisable’
snow.c:309: warning: nested extern declaration of ‘glDisable’
snow.c:310: warning: implicit declaration of function ‘glBlendFunc’
snow.c:310: warning: nested extern declaration of ‘glBlendFunc’
snow.c:310: error: ‘GL_ONE’ undeclared (first use in this function)
snow.c:310: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
snow.c: At top level:
snow.c:318: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
snow.c:318: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c:352: warning: type defaults to ‘int’ in declaration of ‘CompTransform’
snow.c:352: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c: In function ‘initiateSnowFlake’:
snow.c:381: error: dereferencing pointer to incomplete type
snow.c:383: error: dereferencing pointer to incomplete type
snow.c:386: error: dereferencing pointer to incomplete type
snow.c:392: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:400: error: dereferencing pointer to incomplete type
snow.c:406: error: dereferencing pointer to incomplete type
snow.c:413: error: dereferencing pointer to incomplete type
snow.c: In function ‘setSnowflakeTexture’:
snow.c:423: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c: In function ‘updateSnowTextures’:
snow.c:431: error: dereferencing pointer to incomplete type
snow.c:432: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:436: error: dereferencing pointer to incomplete type
snow.c:438: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:440: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:442: warning: implicit declaration of function ‘finiTexture’
snow.c:442: warning: nested extern declaration of ‘finiTexture’
snow.c:442: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:443: warning: implicit declaration of function ‘glDeleteLists’
snow.c:443: warning: nested extern declaration of ‘glDeleteLists’
snow.c:443: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:446: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:447: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:448: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:450: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:454: error: ‘CompMatrix’ undeclared (first use in this function)
snow.c:454: error: ‘mat’ undeclared (first use in this function)
snow.c:457: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:458: warning: implicit declaration of function ‘readImageToTexture’
snow.c:458: warning: nested extern declaration of ‘readImageToTexture’
snow.c:458: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:459: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:459: error: dereferencing pointer to incomplete type
snow.c:460: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:461: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:462: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:464: warning: implicit declaration of function ‘compLogMessage’
snow.c:464: warning: nested extern declaration of ‘compLogMessage’
snow.c:464: error: dereferencing pointer to incomplete type
snow.c:464: error: ‘CompLogLevelWarn’ undeclared (first use in this function)
snow.c:465: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:465: error: dereferencing pointer to incomplete type
snow.c:468: error: dereferencing pointer to incomplete type
snow.c:468: error: ‘CompLogLevelInfo’ undeclared (first use in this function)
snow.c:469: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:469: error: dereferencing pointer to incomplete type
snow.c:471: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:472: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:474: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:477: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:479: warning: implicit declaration of function ‘glTexCoord2f’
snow.c:479: warning: nested extern declaration of ‘glTexCoord2f’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_X’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_X’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_Y’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_Y’
snow.c:480: warning: implicit declaration of function ‘glVertex2f’
snow.c:480: warning: nested extern declaration of ‘glVertex2f’
snow.c:482: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘width’
snow.c:484: error: ‘SnowTexture’ has no member named ‘width’
snow.c:485: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘width’
snow.c:487: error: ‘SnowTexture’ has no member named ‘width’
snow.c:497: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c: In function ‘snowInitScreen’:
snow.c:510: error: dereferencing pointer to incomplete type
snow.c:513: error: dereferencing pointer to incomplete type
snow.c:517: error: dereferencing pointer to incomplete type
snow.c:520: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:521: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:522: error: ‘FALSE’ undeclared (first use in this function)
snow.c:523: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:525: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:537: warning: implicit declaration of function ‘WRAP’
snow.c:537: warning: nested extern declaration of ‘WRAP’
snow.c:537: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:537: error: ‘snowPaintOutput’ undeclared (first use in this function)
snow.c:538: error: ‘drawWindow’ undeclared (first use in this function)
snow.c:538: error: ‘snowDrawWindow’ undeclared (first use in this function)
snow.c:540: error: dereferencing pointer to incomplete type
snow.c:543: error: ‘TRUE’ undeclared (first use in this function)
snow.c:544: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniScreen’:
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:557: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:559: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:560: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:563: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:564: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:566: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:567: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:569: warning: implicit declaration of function ‘UNWRAP’
snow.c:569: warning: nested extern declaration of ‘UNWRAP’
snow.c:569: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:570: error: ‘drawWindow’ undeclared (first use in this function)
snow.c: In function ‘snowDisplayOptionChanged’:
snow.c:580: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:591: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:591: error: ‘TRUE’ undeclared (first use in this function)
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:624: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:642: error: dereferencing pointer to incomplete type
snow.c:643: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c: In function ‘snowInitDisplay’:
snow.c:663: warning: implicit declaration of function ‘allocateScreenPrivateIndex’
snow.c:663: warning: nested extern declaration of ‘allocateScreenPrivateIndex’
snow.c:667: error: ‘FALSE’ undeclared (first use in this function)
snow.c:670: error: too many arguments to function ‘snowSetToggleInitiate’
snow.c:677: error: dereferencing pointer to incomplete type
snow.c:678: error: dereferencing pointer to incomplete type
snow.c:680: error: dereferencing pointer to incomplete type
snow.c:682: error: ‘TRUE’ undeclared (first use in this function)
snow.c:683: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniDisplay’:
snow.c:689: error: dereferencing pointer to incomplete type
snow.c:691: warning: implicit declaration of function ‘freeScreenPrivateIndex’
snow.c:691: warning: nested extern declaration of ‘freeScreenPrivateIndex’
snow.c: In function ‘snowInit’:
snow.c:698: warning: implicit declaration of function ‘allocateDisplayPrivateIndex’
snow.c:698: warning: nested extern declaration of ‘allocateDisplayPrivateIndex’
snow.c:700: error: ‘FALSE’ undeclared (first use in this function)
snow.c:702: error: ‘TRUE’ undeclared (first use in this function)
snow.c:703: warning: control reaches end of non-void function
snow.c: In function ‘snowFini’:
snow.c:708: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
snow.c:708: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
snow.c: In function ‘snowGetVersion’:
snow.c:715: error: ‘ABIVERSION’ undeclared (first use in this function)
snow.c:716: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:718: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘snowVTable’
snow.c:736: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/snow.lo] Error 1


know what that means?.....:confused:

---

### Post by jryprt on 2008-04-18
Try asking [Here](http://forum.compiz-fusion.org/index.php)

---

### Post by JayDeePlus on 2008-04-19
> Sorry about the mis-instructions from before. ^^; It's been a while.

Code:

sudo chown -R $(whoami):$(whoami) ~/.compiz/

That command uses superuser privileges to change the owner and group of the ~/.compiz directory and everything under it to belong to you. The reason you didn't have permission to that directory before is because you accidentally created that directory as the superuser, probably when you used "sudo make install" to install a Compiz plugin.

To take that one command apart:

    * sudo - run a command with another user's privileges (defaults to superuser)
    * chown - change the user or group ownership of a file or directory
    * -R - recursively, including all files and directories inside the specified directory
    * $(whoami):$(whoami) - set the new owner and group both equal to the output of the whoami command
    * ~/.compiz - the directory this command should modify


There are way~ too many other commands to list, but you can always find more information about a specific command online.
Code:

man <command>

is also good if the technical style of the man page doesn't bother you.


all in all...........it was a permissions problem to my home directory.....the sudo chown command reset the permissions and i was able to get the tar and install it.........that everyone for the help on this...............

---

