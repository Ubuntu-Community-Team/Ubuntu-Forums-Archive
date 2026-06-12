---
title: "Compiz blinds, helix and sandstorm animations in ibex?"
date: 2009-01-19
forum: General Help
---

### Post by KhaaL on 2009-01-19
I'm trying to find a way to enable these effects in ubuntu but can't find a way to do this. Is there a repo with the neccesary packages or another way get them?

---

### Post by DJ_Peng on 2009-01-19
[This]("http://forum.compiz-fusion.org/showthread.php?t=10273") may be what you're looking for, although I'm not 100% certain. I found that after several searches when I finally searched the [Compiz Forums]("http://forum.compiz-fusion.org/") for Helix.

---

### Post by ellalan on 2009-01-19
> **KhaaL said:**
> I'm trying to find a way to enable these effects in ubuntu but can't find a way to do this. Is there a repo with the neccesary packages or another way get them?
I have got Helix,Blind effects but without Sandstorm by installing this script from the French Ubuntu forum.
As you probably know its not stable and you would back up and please do not blame me if anything goes wrong. I am very disappointed with me because I have introduced this link to another member and he had a lot of problems un installing this version of compiz.
However it works fine in my system and I couldn't find these effects in any other Git versions of compiz I found in this forum.
[http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1)

I have attached some screen shots,just for you to have a look at the effects available in the compiz 0.7.9 git version.

---

### Post by johnjohn2 on 2009-01-20
> **ellalan said:**
> I have got Helix,Blind effects but without Sandstorm by installing this script from the French Ubuntu forum.
As you probably know its not stable and you would back up and please do not blame me if anything goes wrong. I am very disappointed with me because I have introduced this link to another member and he had a lot of problems un installing this version of compiz.
However it works fine in my system and I couldn't find these effects in any other Git versions of compiz I found in this forum.
[http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1)

I have attached some screen shots,just for you to have a look at the effects available in the compiz 0.7.9 git version.

Worked for me dude

cheers
:popcorn:

---

### Post by ellalan on 2009-01-20
> **johnjohn2 said:**
> Worked for me dude

cheers
:popcorn:
You are welcome, I am glad it worked for you.

---

### Post by DJ_Peng on 2009-01-21
> **ellalan said:**
> I have got Helix,Blind effects but without Sandstorm by installing this script from the French Ubuntu forum.
...
[http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1)

I have attached some screen shots,just for you to have a look at the effects available in the compiz 0.7.9 git version.
Does anyone know how that will behave on a system set to en_US? I'd like to check out the new animations if I can get them installed.

---

### Post by KhaaL on 2009-01-22
Since I'm not too comfortable to let scripts mess with my computer, i went with the road where i can mess up my computer manually by my hands :D


I tried compiling extra animations but it fails with this error:
> 
khaal@Xeraphim:~/compiz/extra-animations$ make clean
removing  : ./build
khaal@Xeraphim:~/compiz/extra-animations$ make 
convert   : animationplus.xml.in -> build/animationplus.xml
schema    : build/animationplus.xml -> build/compiz-animationplus.schema
compiling : helix.c -> build/helix.lo
compiling : blinds.c -> build/blinds.lo
compiling : extra-animations/helix.c -> build/extra-animations/helix.lo
compiling : extra-animations/blinds.c -> build/extra-animations/blinds.lo
compiling : extra-animations/animationplus.c -> build/extra-animations/animationcompiling : extra-animations/animationplus.c -> build/extra-animations/animationplus.lo
compiling : extra-animations/shatter.c -> build/extra-animations/shatter.loextra-animations/shatter.c: In function &#8216;fxShatterInit&#8217;:
extra-animations/shatter.c:46: error: &#8216;AnimAddonFunctions&#8217; has no member named &#8216;tessellateIntoGlass&#8217;
make: *** [build/extra-animations/shatter.lo] Error 1
khaal@Xeraphim:~/compiz/extra-animations$ 



Any ideas?

---

### Post by jordan420 on 2009-05-07
hey guy. i tried to go that way as well but continue to get a similar error ```
compiling : shatter.c -> build/shatter.loIn file included from animationplus.h:14,
                 from shatter.c:31:
/usr/include/compiz/compiz-core.h:48:20: error: GL/glx.h: No such file or directory
In file included from animationplus.h:14,
                 from shatter.c:31:
/usr/include/compiz/compiz-core.h:1588: error: expected specifier-qualifier-list before ‘GLXPixmap’
/usr/include/compiz/compiz-core.h:1729: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
/usr/include/compiz/compiz-core.h:1733: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
/usr/include/compiz/compiz-core.h:1736: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
/usr/include/compiz/compiz-core.h:1741: error: expected declaration specifiers or ‘...’ before ‘GLXDrawable’
/usr/include/compiz/compiz-core.h:1763: error: expected declaration specifiers or ‘...’ before ‘*’ token
/usr/include/compiz/compiz-core.h:1766: warning: type defaults to ‘int’ in declaration of ‘GLXPixmap’
/usr/include/compiz/compiz-core.h:1766: error: ‘GLXPixmap’ declared as function returning a function
/usr/include/compiz/compiz-core.h:1766: warning: function declaration isn’t a prototype
/usr/include/compiz/compiz-core.h:2136: error: expected specifier-qualifier-list before ‘GLXCreatePixmapProc’
make: *** [build/shatter.lo] Error 1
``` did you ever manage to compile your successfully?

---

### Post by KhaaL on 2009-05-08
Nah, never got it going. I've given up as this was taking more time than what it was worth. Hoping for a good soul dropping a .deb at us...

---

### Post by jordan420 on 2009-05-10
hey man. i gave up compiling it as well and tried the french script. and despite how  much i dislike some of there decisions on the political side they have managed to forge a fine method of installing compiz from git. ime running it now and its working beautifully on my dell laptop (gm965) with jaunty. give it a try i dont think it'll mess anything up.

---

