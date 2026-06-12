---
title: "Compiling game-editor... or deb package available?"
date: 2009-10-21
forum: Gaming &amp; Leisure
---

### Post by charlieman on 2009-10-21
Hi, I've recently found out about [http://game-editor.com/]("http://game-editor.com/"). A game authoring software that's been recently opensourced (:P yay!) and I want to try it.

Apparently they have only demos for download, so I'm trying to compile it. Their [compiling instructions]("http://game-editor.svnrepository.com/code/trac.cgi/browser/trunk/compilation.txt") look confusing :confused: so before I start on this quest to get it working I wanted to know if someone out there has done it before to get some instructions or if there's a deb package already compiled.

Thanks for the help.

---

### Post by charlieman on 2009-10-21
Also, the demo didn't work, it needs libstd++5 and that package only exists for jaunty :(

---

### Post by Sindwiller on 2009-10-21
The compiling instructions seem to have been written with downloading every additional library as a source tarball yourself in mind. And why in the name of jesus christ do you have to get LLVM anyway. And why RakNet? An impossible networking library with an even more retarded license.

Besides these lines,

> 6	Configure the LibStatic project to:
7	Multi-threaded (/MT or /MTd)

everything seems pretty obvious to me. So what you do is...

```
mkdir llvm
cd llvm
svn co http://llvm.org/svn/llvm-project/llvm/trunk .
cd tools
svn co http://llvm.org/svn/llvm-project/cfe/trunk clang 
cd ..
./configure
make && sudo make install
cd tools/clang
make && sudo make install
```

So, what you first do is get llvm from SVN (check if you have installed the package 'subversion'), get the clang tool, too, configure the build process (if any error occurs when building it, post it), compile both and install both.

Afterwards you should check whether you have 'unzip' from universe installed and

```
cd ../../../
wget http://www.jenkinssoftware.com/raknet/downloads/RakNet-3.703.zip
unzip RakNet-3.703.zip
cd RakNet-3.703
./bootstrap
./configure
make && sudo make install
```

I'm not really sure about the actual process above, as I'm not running Linux at the moment so I can't confirm it, and RakNet's confusing.

Also

> sudo apt-get install libwxbase2.8-dev libwxgtk2.8-dev

should do install the wxWidgets development files, assuming that they want 2.8.

Then go to the game-editor directory and type 'make'... that should do it.

As I said, I'm not running Linux right now so I can't confirm that everything works as planned.

Cheers :)

---

### Post by charlieman on 2009-10-21
Wow thanks, will do it right now and post if I succeeded :D

---

### Post by kdnewton on 2009-10-21
I'd be interested to see a package of Game-Editor as well. I'm in the process of compiling llvm and it's inflating huuuge (~2GB). Taking a good long time (but what do I know about whether or not that's a long time to compile, I usually rely on .deb).

---

### Post by Vadi on 2009-10-21
I'll see if this can be added to PlayDeb.

---

### Post by Sindwiller on 2009-10-22
I wouldn't put too much faith into a rpg/game maker anyway, those apps are mostly very limiting and often feature obscure program design decisions to make things "easier".

What the hell do I know though.

> Wow thanks, will do it right now and post if I succeeded 

I'm wet with anticipation :)

---

### Post by menevia16a on 2012-11-05
> **Sindwiller said:**
> The compiling instructions seem to have been written with downloading every additional library as a source tarball yourself in mind. And why in the name of jesus christ do you have to get LLVM anyway. And why RakNet? An impossible networking library with an even more retarded license.

Besides these lines,



everything seems pretty obvious to me. So what you do is...

```
mkdir llvm
cd llvm
svn co http://llvm.org/svn/llvm-project/llvm/trunk .
cd tools
svn co http://llvm.org/svn/llvm-project/cfe/trunk clang 
cd ..
./configure
make && sudo make install
cd tools/clang
make && sudo make install
```

So, what you first do is get llvm from SVN (check if you have installed the package 'subversion'), get the clang tool, too, configure the build process (if any error occurs when building it, post it), compile both and install both.

Afterwards you should check whether you have 'unzip' from universe installed and

```
cd ../../../
wget http://www.jenkinssoftware.com/raknet/downloads/RakNet-3.703.zip
unzip RakNet-3.703.zip
cd RakNet-3.703
./bootstrap
./configure
make && sudo make install
```

I'm not really sure about the actual process above, as I'm not running Linux at the moment so I can't confirm it, and RakNet's confusing.

Also



should do install the wxWidgets development files, assuming that they want 2.8.

Then go to the game-editor directory and type 'make'... that should do it.

As I said, I'm not running Linux right now so I can't confirm that everything works as planned.

Cheers :)
In your 2nd code box the "wget" command line, were you put "http://www.jenkinssoftware.com/raknet/downloads/RakNet-3.703.zip", change it to [http://www.jenkinssoftware.com/raknet/downloads/RakNet-3.732.zip](http://www.jenkinssoftware.com/raknet/downloads/RakNet-3.732.zip)

---

### Post by frostwork on 2012-11-05
version numbers change after 3 years :}

---

