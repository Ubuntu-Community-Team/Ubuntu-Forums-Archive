---
title: "Great plugins of Compiz."
date: 2010-02-23
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-23
Hi all, I saw some great plugins of Compiz in action in youtube videos.Thy are:-
1. Screensaver
2. Newton
3. Elements
4. Freewins
5. Stack Window Switcher

How can install these plugins ? Some post tells that I should use git or make [I do not know how to compile a source code and have not used git for anything.] Is it available if I add some ppa or some other repo ? What is compiz++? Are all plugins available by default in compiz++?

Also tell me if there are any other great compiz plugins not installed by default.

Thank you all in advance.

---

### Post by fr0sty on 2010-02-23
First off, lets start with the easy way to get compiz installed: 1. Applications: Add Remove
2. type in ccsm
3. select compiz
4. install

As for the extras try this:

maybe give this line of code a try in Terminal:

> sudo apt-get install compiz*

That should give you a bunch of the extra plugins.

---

### Post by hariks0 on 2010-02-23
I already have almost all the pluginsand ccsm. AFAIK, the above are the ones I miss. Thank you for your guidance. What next?

---

### Post by koleoptero on 2010-02-24
Know that you may have stability issues when playing with compiz. If you decide to go ahead with it then go with these commands to add the compiz ppa and install the unsupported plugins. I don't know for sure which plugins it will install but it's bound to have more than the usual ones.

sudo add-apt-repository ppa:compiz/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install compiz-fusion-plugins-unsupported

---

### Post by hariks0 on 2010-02-24
Thank you koleaptro, But my repo is already the ppa of compiz with all unsupported plugins installed. I think there is some special way for getting these additional plugins. Can somebody suggest?

---

### Post by nilarimogard on 2010-02-24
You have to compile the latest Compiz Plugins from GIT. In [this post]("http://www.webupd8.org/2010/01/try-gstyle-project-new-gnome-theme.html") there is a script at the bottom which automatically downloads and compiles Compiz and all the Compiz plugins from git (but the script is in French).

---

### Post by hariks0 on 2010-03-02
> **nilarimogard said:**
> You have to compile the latest Compiz Plugins from GIT. In [this post]("http://www.webupd8.org/2010/01/try-gstyle-project-new-gnome-theme.html") there is a script at the bottom which automatically downloads and compiles Compiz and all the Compiz plugins from git (but the script is in French).

Thank you. But that did not help much. The plugins I asked for were not installed and the error descriptions did not help much as it was in French.

Instead [this script]("http://forum.compiz.org/viewtopic.php?f=114&t=12012") did the job very clean.

---

### Post by karmila on 2010-07-28
> **hariks0 said:**
> Thank you. But that did not help much. The plugins I asked for were not installed and the error descriptions did not help much as it was in French.

Instead [this script]("http://forum.compiz.org/viewtopic.php?f=114&t=12012") did the job very clean.

Me again :p

i tried to install with script from [here]("http://ultimateeditionoz.com/forum/viewtopic.php?f=63&t=874") but it's no longer working because the dev has changed the script.

And yes [this script]("http://forum.compiz.org/viewtopic.php?f=114&t=12012") is up to date. Working flawlessly, except i couldn't find the newton effect :(

---

### Post by hariks0 on 2010-07-28
Try the following in terminal one by one

```
git clone git://anongit.compiz.org/users/xytovl/newton
cd newton
make clean
make
make install
```

BTW, the repository of all plugins of compiz is [here]("http://git.compiz.org/"). Click on the item you want, in the next page, there will be a line at the left bottom that starts in git://... Copy that and paste it in terminal prefixing *git clone* just like the first command above. All the rest is same. Compile as many as you need and enjoy.

Happy compizing !

---

### Post by karmila on 2010-07-28
> **hariks0 said:**
> Try the following in terminal one by one

```
git clone git://anongit.compiz.org/users/xytovl/newton
cd newton
make clean
make
make install
```

BTW, the repository of all plugins of compiz is [here]("http://git.compiz.org/"). Click on the item you want, in the next page, there will be a line at the left bottom that starts in git://... Copy that and paste it in terminal prefixing *git clone* just like the first command above. All the rest is same. Compile as many as you need and enjoy.

Happy compizing !

thanks, this is a really precious information... also the tips for compiling too :KS

---

### Post by klikevil on 2010-08-06
> **hariks0 said:**
> Try the following in terminal one by one

```
git clone git://anongit.compiz.org/users/xytovl/newton
cd newton
make clean
make
make install
```BTW, the repository of all plugins of compiz is [here]("http://git.compiz.org/"). Click on the item you want, in the next page, there will be a line at the left bottom that starts in git://... Copy that and paste it in terminal prefixing *git clone* just like the first command above. All the rest is same. Compile as many as you need and enjoy.

Happy compizing !


seotechd@EdenII:~/Compiz$ git clone git://anongit.compiz.org/users/xytovl/newton
Initialized empty Git repository in /home/seotechd/Compiz/newton/.git/
remote: Counting objects: 59, done.
remote: Compressing objects: 100% (56/56), done.
remote: Total 59 (delta 21), reused 0 (delta 0)
Receiving objects: 100% (59/59), 59.17 KiB, done.
Resolving deltas: 100% (21/21), done.
seotechd@EdenII:~/Compiz$ cd newton
seotechd@EdenII:~/Compiz/newton$ make clean
make: *** No rule to make target `clean'.  Stop.
seotechd@EdenII:~/Compiz/newton$ ls
CMakeLists.txt    newton.xml.in  src
seotechd@EdenII:~/Compiz/newton$ 



where teh hell is the make file? lol

---

### Post by hariks0 on 2010-08-07
Try downloading the same again. If it does not work, I can provide the other files in my .../newton.

Please post back.

---

### Post by c.dric on 2010-08-07
> **hariks0 said:**
> Hi all, I saw some great plugins of Compiz in action in youtube videos.Thy are:-
1. Screensaver
2. Newton
3. Elements
4. Freewins
5. Stack Window Switcher


Could you post the link to the video ? I'm curious.

Thx.
Cédric

---

### Post by hariks0 on 2010-08-07
Search in youtube for these. If you did not find one, just post back. I will upload one from my PC and post the link here. :p

---

### Post by 5735guy on 2010-08-07
Here is the method I used to succesfully compile Compiz 0.9.0 on Ubuntu Lucid and Linux Mint Isadora

Download Desktop.tar.gz from the site below then use my script
[http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/](http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/)

SYNAPTIC

Default Compiz (complete removal)

TERMINAL

sudo add-apt-repository ppa:falk-t-j/lucid-latest
sudo apt-get update

sudo apt-get install compiz-git

SYNAPTIC

compiz-git (complete removal)

TERMINAL

cd ~/Desktop && tar -xf Desktop.tar.gz

./install_compiz_090.sh

Alt+F2

/opt/compiz/bin/compiz++

set up CCSM

REBOOT

Alt+F2

/opt/compiz/bin/compiz++

Compiz 0.9.0 compilation is now complete :guitar:

----------------------------------------

A little tidying up

SYNAPTIC

Remove falkTX repository

TERMINAL

sudo apt-get autoremove

SYNAPTIC

Purge package residuals

:guitar::guitar:

---

### Post by c.dric on 2010-08-08
> **hariks0 said:**
> Search in youtube for these. If you did not find one, just post back. I will upload one from my PC and post the link here. :p

I don't feel like searching in Youtube. 
99% of the results is gonna be about effects i've already seen or used.

I thought you found something out of the ordinary and could provide a shortcut. :)

---

### Post by hariks0 on 2010-08-08
Here are the plugin videos;-

[Screensaver]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DRmz9a9pJR_s&sa=X&ei=6fFeTJTiIYm4uQPxgtiZDA&ved=0CBYQuAIwAA&usg=AFQjCNHKlXRiE5vto688Lz3QQPc_aTBsUw")
[Newton]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DAu0kLuRj4tI&sa=X&ei=UvJeTM3fLY6KvQOOlNyZDA&ved=0CBYQuAIwAA&usg=AFQjCNElDs9OMfulehlIPWlQ0S7T2Qu5ow")
[Freewins]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DSSHQPDGuKnU&sa=X&ei=hvJeTLyALZGqvQPMhdmZDA&ved=0CBYQuAIwAA&usg=AFQjCNFyUse8FNZF6kjNVwqMYUL3aEkBKw") and
[Stackswitch]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DdJbgjBX8DaI&sa=X&ei=vvJeTMHlMIK2vQPw3ciZDA&ved=0CCwQuAIwAw&usg=AFQjCNH_JTntNSbWFL4W3QQWIgtgX5y4Mg")

They are the first results in google. But I have watched almost all these.

Enjoy :popcorn:

---

### Post by karmila on 2010-09-05
> **hariks0 said:**
> Here are the plugin videos;-

[Screensaver]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DRmz9a9pJR_s&sa=X&ei=6fFeTJTiIYm4uQPxgtiZDA&ved=0CBYQuAIwAA&usg=AFQjCNHKlXRiE5vto688Lz3QQPc_aTBsUw")
[Newton]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DAu0kLuRj4tI&sa=X&ei=UvJeTM3fLY6KvQOOlNyZDA&ved=0CBYQuAIwAA&usg=AFQjCNElDs9OMfulehlIPWlQ0S7T2Qu5ow")
[Freewins]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DSSHQPDGuKnU&sa=X&ei=hvJeTLyALZGqvQPMhdmZDA&ved=0CBYQuAIwAA&usg=AFQjCNFyUse8FNZF6kjNVwqMYUL3aEkBKw") and
[Stackswitch]("http://www.google.co.in/url?q=http://www.youtube.com/watch%3Fv%3DdJbgjBX8DaI&sa=X&ei=vvJeTMHlMIK2vQPw3ciZDA&ved=0CCwQuAIwAw&usg=AFQjCNH_JTntNSbWFL4W3QQWIgtgX5y4Mg")

They are the first results in google. But I have watched almost all these.

Enjoy :popcorn:
Hi, hariks0!

I've installed all those plugins. Screensaver and stackswitch works perfectly but I still cannot make the other two effects work.

Newton, I don't understand on how keybindings work. Only one of them working but only make my window flying over the edge of my screen. The other none.

Freewins make my computer hung. I even need to hard reset my computer. 

Would you share how to make them work?

---

### Post by hariks0 on 2010-09-06
Regarding freewins, I also had the same problem. But what you have to do is click and drag the body of the window with the key binding. We initially do it on the title bar and the machine is hung. About newton, I will post the settings in my ccsm when I reach home.

---

### Post by karmila on 2010-09-06
> **hariks0 said:**
> Regarding freewins, I also had the same problem. But what you have to do is click and drag the body of the window with the key binding. We initially do it on the title bar and the machine is hung. About newton, I will post the settings in my ccsm when I reach home.

OK, I'm waiting ):P

---

### Post by hariks0 on 2010-09-06
I don't think I have made much modifications of the default settings. The screenshots are attached.
;)

Also try my settings profile. It is named ccsm.doc but actually it is .txt :popcorn:

---

### Post by karmila on 2010-09-06
Obviously i have different newton than you are. The git command not success for me, here it is:

```
strider@strider-desktop:~$ git clone git://anongit.compiz.org/users/xytovl/newton
Initialized empty Git repository in /home/strider/newton/.git/
remote: Counting objects: 59, done.
remote: Compressing objects: 100% (56/56), done.
remote: Total 59 (delta 21), reused 0 (delta 0)
Receiving objects: 100% (59/59), 59.17 KiB | 36 KiB/s, done.
Resolving deltas: 100% (21/21), done.
strider@strider-desktop:~$ cd newton
strider@strider-desktop:~/newton$ make clean
make: *** No rule to make target `clean'.  Stop.
strider@strider-desktop:~/newton$ make
make: *** No targets specified and no makefile found.  Stop.
```So, I compiled it manually from the source I got here [http://forum.compiz.org/viewtopic.php?f=89&t=8555&start=20](http://forum.compiz.org/viewtopic.php?f=89&t=8555&start=20) attached in one post.

Any suggestion?

---

### Post by karmila on 2010-09-06
I forget to say thanks for your ccsm setting. Reading it now!

---

### Post by hariks0 on 2010-09-06
Suggestions? Hmm, try the plugin with the settings available and post back.:p
BTW, the Plugin I have is attached. Try compiling that for the options similar to mine. Also, I have set the show desktop hot spot in *General>General options>Key bindings>Show desktop as Bottom left*. If you move the mouse to that corner all windows will be minimized and move it again all are back.

---

### Post by karmila on 2010-09-07
> **hariks0 said:**
> Suggestions? Hmm, try the plugin with the settings available and post back.:p
BTW, the Plugin I have is attached. Try compiling that for the options similar to mine. Also, I have set the show desktop hot spot in *General>General options>Key bindings>Show desktop as Bottom left*. If you move the mouse to that corner all windows will be minimized and move it again all are back.

It works, I have the same setting as yours now. It's happy get things sort ;)

Can you make mini windows like in the video? How?

---

### Post by hariks0 on 2010-09-07
No. I also am not able to generate the miniature windows. Will post back if found out. Try that compiz forun which is not accessible from my office.

---

### Post by nkamath on 2010-12-21
Hi ! 
I hv tried to compile & got the results below:
My question is how to compile with ObjC  (I hv loaded gObjC from synaptics)
There is also an warning shown /usr/include/...........

saibaba@saibaba-laptop:~$ cd newton
saibaba@saibaba-laptop:~/newton$ make clean
removing  : ./build
saibaba@saibaba-laptop:~/newton$ make && make install
convert   : newton.xml.in -> build/newton.xml
bcop'ing  : build/newton.xml -> build/newton_options.h
bcop'ing  : build/newton.xml -> build/newton_options.c
schema    : build/newton.xml -> build/compiz-newton.schema
compiling : newton.c -> build/newton.loIn file included from newton.c:23:
[B]/usr/include/compiz/compiz-core.h:1297: warning: declaration does not declare anything
newton.c:413: warning: ‘newtonToggleMovable’ defined but not used[/B]
compiling : newton.c -> build/newton.lo
compiling : chipmunk/cpPolyShape.c -> build/chipmunk/cpPolyShape.lo
compiling : chipmunk/cpSpaceHash.c -> build/chipmunk/cpSpaceHash.lo
compiling : chipmunk/cpSpace.c -> build/chipmunk/cpSpace.lo
compiling : chipmunk/chipmunk.c -> build/chipmunk/chipmunk.lo
compiling : chipmunk/cpArray.c -> build/chipmunk/cpArray.lo
compiling : chipmunk/cpHashSet.c -> build/chipmunk/cpHashSet.lo
compiling : chipmunk/cpBody.c -> build/chipmunk/cpBody.lo
compiling : chipmunk/cpBB.c -> build/chipmunk/cpBB.lo
compiling : chipmunk/cpCollision.c -> build/chipmunk/cpCollision.lochipmunk/cpCollision.c:349: warning: no previous prototype for ‘cpInitCollisionFuncs’
compiling : chipmunk/cpCollision.c -> build/chipmunk/cpCollision.lo
compiling : chipmunk/cpVect.c -> build/chipmunk/cpVect.lo
compiling : chipmunk/cpShape.c -> build/chipmunk/cpShape.lo
compiling : chipmunk/cpArbiter.c -> build/chipmunk/cpArbiter.lo
compiling : chipmunk/cpJoint.c -> build/chipmunk/cpJoint.lo
compiling : src/cpJoint.cpp -> build/src/cpJoint.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpJoint.cpp -> build/src/cpJoint.lo
compiling : src/cpShape.cpp -> build/src/cpShape.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpShape.cpp -> build/src/cpShape.lo
compiling : src/cpSpaceHash.cpp -> build/src/cpSpaceHash.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpSpaceHash.cpp -> build/src/cpSpaceHash.lo
compiling : src/cpBB.cpp -> build/src/cpBB.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpBB.cpp -> build/src/cpBB.lo
compiling : src/cpHashSet.cpp -> build/src/cpHashSet.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpHashSet.cpp -> build/src/cpHashSet.lo
compiling : src/cpBody.cpp -> build/src/cpBody.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpBody.cpp -> build/src/cpBody.lo
compiling : src/cpVect.cpp -> build/src/cpVect.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpVect.cpp -> build/src/cpVect.lo
compiling : src/newton.cpp -> build/src/newton.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
In file included from src/newton.cpp:23:
src/newton.h:23: fatal error: core/core.h: No such file or directory
compilation terminated.
make: *** [build/src/newton.lo] Error 1
saibaba@saibaba-laptop:~/newton$

---

### Post by xfearxnxloathing on 2011-01-25
> **hariks0 said:**
> Try the following in terminal one by one

```
git clone git://anongit.compiz.org/users/xytovl/newton
cd newton
make clean
make
make install
```

BTW, the repository of all plugins of compiz is [here]("http://git.compiz.org/"). Click on the item you want, in the next page, there will be a line at the left bottom that starts in git://... Copy that and paste it in terminal prefixing *git clone* just like the first command above. All the rest is same. Compile as many as you need and enjoy.

Happy compizing !

i'm a noob, well not really but with this way of installing i am.
when i do this, this is what i get:```
hybrid@ultra:~$ git clone git://anongit.compiz.org/users/xytovl/newton
fatal: destination path 'newton' already exists and is not an empty directory.
hybrid@ultra:~$ cd newton
hybrid@ultra:~/newton$ make clean
make: *** No rule to make target `clean'.  Stop.
hybrid@ultra:~/newton$ 
```

---

### Post by hariks0 on 2011-01-25
It seems that the \newton folder is already there. Remove it and try again.

----------------
Now playing: [A.R. Rahman - Bombay Theme Music](http://www.foxytunes.com/artist/a.r.+rahman/track/bombay+theme+music?locale=chrome://global/locale/intl.properties)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by xfearxnxloathing on 2011-03-01
> **hariks0 said:**
> It seems that the \newton folder is already there. Remove it and try again.

----------------
Now playing: [A.R. Rahman - Bombay Theme Music](http://www.foxytunes.com/artist/a.r.+rahman/track/bombay+theme+music?locale=chrome://global/locale/intl.properties)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

gotcha! but unfortunately i still get errors =\
> hybrid@ultra:~/newton$ **make clean**
removing  : ./build
hybrid@ultra:~/newton$ **make**
convert   : newton.xml.in -> build/newton.xml
bcop'ing  : build/newton.xml -> build/newton_options.h
bcop'ing  : build/newton.xml -> build/newton_options.c
schema    : build/newton.xml -> build/compiz-newton.schema
compiling : cpSpaceHash.c -> build/cpSpaceHash.lo
compiling : cpVect.c -> build/cpVect.lo
compiling : cpArray.c -> build/cpArray.lo
compiling : cpJoint.c -> build/cpJoint.lo
compiling : cpArbiter.c -> build/cpArbiter.lo
compiling : cpShape.c -> build/cpShape.lo
compiling : cpPolyShape.c -> build/cpPolyShape.lo
compiling : cpCollision.c -> build/cpCollision.locpCollision.c: In function ‘findVerts’:
cpCollision.c:174: warning: cast from pointer to integer of different size
cpCollision.c:180: warning: cast from pointer to integer of different size
cpCollision.c: In function ‘findPointsBehindSeg’:
cpCollision.c:233: warning: cast from pointer to integer of different size
cpCollision.c: In function ‘seg2poly’:
cpCollision.c:274: warning: cast from pointer to integer of different size
cpCollision.c:276: warning: cast from pointer to integer of different size
cpCollision.c: At top level:
cpCollision.c:367: warning: no previous prototype for ‘cpInitCollisionFuncs’
compiling : cpCollision.c -> build/cpCollision.lo
compiling : cpBB.c -> build/cpBB.lo
compiling : cpSpace.c -> build/cpSpace.locpSpace.c: In function ‘queryFunc’:
cpSpace.c:411: warning: cast from pointer to integer of different size
cpSpace.c:411: warning: cast from pointer to integer of different size
compiling : cpSpace.c -> build/cpSpace.lo
compiling : cpBody.c -> build/cpBody.lo
compiling : chipmunk.c -> build/chipmunk.lo
compiling : cpHashSet.c -> build/cpHashSet.lo
compiling : newton.c -> build/newton.loIn file included from newton.c:23:
/usr/include/compiz/compiz-core.h:1296: warning: declaration does not declare anything
compiling : newton.c -> build/newton.lo
compiling : src/cpVect.cpp -> build/src/cpVect.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpVect.cpp -> build/src/cpVect.lo
compiling : src/cpHashSet.cpp -> build/src/cpHashSet.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpHashSet.cpp -> build/src/cpHashSet.lo
compiling : src/cpBody.cpp -> build/src/cpBody.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/cpBody.cpp -> build/src/cpBody.lo
compiling : src/chipmunk.cpp -> build/src/chipmunk.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
compiling : src/chipmunk.cpp -> build/src/chipmunk.lo
compiling : src/cpCollision.cpp -> build/src/cpCollision.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
src/cpCollision.cpp: In function ‘int findVerts(cpContact**, cpPolyShape*, cpPolyShape*, cpVect, cpFloat)’:
src/cpCollision.cpp:174: error: cast from ‘cpPolyShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp:180: error: cast from ‘cpPolyShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp: In function ‘void findPointsBehindSeg(cpContact**, int*, int*, cpSegmentShape*, cpPolyShape*, cpFloat, cpFloat)’:
src/cpCollision.cpp:233: error: cast from ‘cpPolyShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp: In function ‘int seg2poly(cpShape*, cpShape*, cpContact**)’:
src/cpCollision.cpp:274: error: cast from ‘cpSegmentShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp:276: error: cast from ‘cpSegmentShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp: In function ‘void cpInitCollisionFuncs()’:
src/cpCollision.cpp:367: warning: no previous declaration for ‘void cpInitCollisionFuncs()’
make: *** [build/src/cpCollision.lo] Error 1
hybrid@ultra:~/newton$ **make install**
compiling : src/cpCollision.cpp -> build/src/cpCollision.locc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wnested-externs" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=c99" is valid for C/ObjC but not for C++
src/cpCollision.cpp: In function ‘int findVerts(cpContact**, cpPolyShape*, cpPolyShape*, cpVect, cpFloat)’:
src/cpCollision.cpp:174: error: cast from ‘cpPolyShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp:180: error: cast from ‘cpPolyShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp: In function ‘void findPointsBehindSeg(cpContact**, int*, int*, cpSegmentShape*, cpPolyShape*, cpFloat, cpFloat)’:
src/cpCollision.cpp:233: error: cast from ‘cpPolyShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp: In function ‘int seg2poly(cpShape*, cpShape*, cpContact**)’:
src/cpCollision.cpp:274: error: cast from ‘cpSegmentShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp:276: error: cast from ‘cpSegmentShape*’ to ‘unsigned int’ loses precision
src/cpCollision.cpp: In function ‘void cpInitCollisionFuncs()’:
src/cpCollision.cpp:367: warning: no previous declaration for ‘void cpInitCollisionFuncs()’
make: *** [build/src/cpCollision.lo] Error 1


---

