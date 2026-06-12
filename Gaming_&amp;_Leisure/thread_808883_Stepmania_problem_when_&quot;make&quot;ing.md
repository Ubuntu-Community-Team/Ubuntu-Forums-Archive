---
title: "Stepmania problem when &quot;make&quot;ing"
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by louis3234 on 2008-05-26
Hi, I am kinda noob to ubuntu.
I met a problem when I tried to install StepMania. After I ./configure it, then I typed command make, then it shows like this:

if g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/lua50 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -finline-limit=300   -Wall -W -Wno-unused -Wno-switch -O3 -MT Screen.o -MD -MP -MF ".deps/Screen.Tpo" \
          -c -o Screen.o `test -f 'Screen.cpp' || echo './'`Screen.cpp; \
        then mv -f ".deps/Screen.Tpo" ".deps/Screen.Po"; \
        else rm -f ".deps/Screen.Tpo"; exit 1; \
        fi
GameState.h:88: error: extra qualification ‘GameState::’ on member ‘GetRandomCharacter’
GameState.h:89: error: extra qualification ‘GameState::’ on member ‘GetDefaultCharacter’

Someone help!! I really don't know what does it mean or how to fix it!

---

### Post by Cappy on 2008-05-27
Stepmania is available precompiled here:
[http://www.getdeb.net/app/StepMania](http://www.getdeb.net/app/StepMania)

or

[http://www.stepmania.com/wiki/Downloads](http://www.stepmania.com/wiki/Downloads)

---

### Post by louis3234 on 2008-05-27
Yes, I believe I got one of those packages, and its the same problem. When I tried the precompiled packages, it says:"Dependency is not satisfiable:libcairo2"
I checked the Package Manager, I have all the libairo2 files. The problem is still not solved.:confused:

---

### Post by AJB2K3 on 2008-05-27
> **louis3234 said:**
> Yes, I believe I got one of those packages, and its the same problem. When I tried the precompiled packages, it says:"Dependency is not satisfiable:libcairo2"
I checked the Package Manager, I have all the libairo2 files. The problem is still not solved.:confused:
Double check the libcairo2 versions numbers. could be that you have a different version to whats required.

---

### Post by DoktorSeven on 2008-05-27
If you want to try and fix it, these errors:

```
GameState.h:88: error: extra qualification ‘GameState::’ on member ‘GetRandomCharacter’
GameState.h:89: error: extra qualification ‘GameState::’ on member ‘GetDefaultCharacter’
```

are something from the latest versions of GCC (g++); a coder didn't heed a warning that this was dodgy code in the past and now GCC has made it into an error.

Find and open GameState.h and go to the lines listed (88 and 89).  There should be something like this there:

GameState::GetRandomCharacter
and
GameState::GetDefaultCharacter

There will probably be more code around that, but these are the two parts we're concerned with.  Just remove the "GameState::" part (including the two colons), being sure not to remove any additional characters including spaces and other punctuation, from both of these.

---

### Post by louis3234 on 2008-05-27
> **DoktorSeven said:**
> There will probably be more code around that, but these are the two parts we're concerned with.  Just remove the "GameState::" part (including the two colons), being sure not to remove any additional characters including spaces and other punctuation, from both of these.

Thx for the help, but after I changed it, it has new problem now:

ScreenEvaluation.cpp:412:   instantiated from here
StdString.h:1090: error: no matching function for call to ‘replace(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, const char*&)’
make[2]: *** [ScreenEvaluation.o] Error 1

Geez this is getting tough:(

---

### Post by JTLenzz on 2008-05-27
> ScreenEvaluation.cpp:412: instantiated from here
StdString.h:1090: error: no matching function for call to &#8216;replace(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, const char*&)&#8217;
make[2]: *** [ScreenEvaluation.o] Error 1

Open (from stepmania folder) src/StdString.h and in front of the function call at line 1090 put "this->" (without quotes) so you get:

```
this->replace(this->begin()+nIdx, this->begin()+nIdx+nOldLen, szRealNew);
```

Another error you may come across is:

```
In file included from ScreenNetworkOptions.cpp:13:
NetworkSyncServer.h:120: error: extra qualification &#8216;StepManiaLanServer::&#8217; on member &#8216;ListPlayers&#8217;

```

Fix by opening NetworkSyncServer.h and removing the "StepManiaLanServer::" part in front of ListPlayers()

---

### Post by louis3234 on 2008-05-28
Thanks for the help but, MORE PROBLEMS!!!!! ](*,)
Here is the error message:

```
if g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/lua50 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -finline-limit=300   -Wall -W -Wno-unused -Wno-switch -O3 -MT InputHandler_SDL.o -MD -MP -MF ".deps/InputHandler_SDL.Tpo" \
          -c -o InputHandler_SDL.o `test -f 'arch/InputHandler/InputHandler_SDL.cpp' || echo './'`arch/InputHandler/InputHandler_SDL.cpp; \
        then mv -f ".deps/InputHandler_SDL.Tpo" ".deps/InputHandler_SDL.Po"; \
        else rm -f ".deps/InputHandler_SDL.Tpo"; exit 1; \
        fi
arch/InputHandler/InputHandler_SDL.cpp:126: error: ‘int SDL_EventMask’ redeclared as different kind of symbol
/usr/include/SDL/SDL_events.h:108: error: previous declaration of ‘typedef enum SDL_EventMasks SDL_EventMask’
arch/InputHandler/InputHandler_SDL.cpp: In constructor ‘InputHandler_SDL::InputHandler_SDL()’:
arch/InputHandler/InputHandler_SDL.cpp:176: error: expected unqualified-id before ‘|=’ token
arch/InputHandler/InputHandler_SDL.cpp: In member function ‘virtual void InputHandler_SDL::Update(float)’:
arch/InputHandler/InputHandler_SDL.cpp:195: error: expected primary-expression before ‘)’ token
make[2]: *** [InputHandler_SDL.o] Error 1
```

What do I do....:(

---

### Post by DoktorSeven on 2008-05-28
Whoah.  At this point, you might be better off trying g++-3.4 to compile.

**sudo apt-get install gcc-3.4 g++-3.4**

Don't worry, it'll install alongside the normal gcc/g++ and won't interfere with it.

Do a **make clean**, then before you do the ./configure step again, do this:

```

export CC=gcc-3.4
export CXX=g++-3.4

```

When you do ./configure, it should use g++ version 3.4, which will hopefully turn all those errors into just warnings.  (And it might be best to just undo all the changes you've made and try to compile the source from a newly extracted source tree.)

The change to 3.4 is only temporary and will only persist while that terminal session is open (and within that terminal only), by the way.

---

### Post by louis3234 on 2008-05-28
> **DoktorSeven said:**
> Whoah.  At this point, you might be better off trying g++-3.4 to compile.

**sudo apt-get install gcc-3.4 g++-3.4**

Don't worry, it'll install alongside the normal gcc/g++ and won't interfere with it.

Do a **make clean**, then before you do the ./configure step again, do this:

```

export CC=gcc-3.4
export CXX=g++-3.4

```

When you do ./configure, it should use g++ version 3.4, which will hopefully turn all those errors into just warnings.  (And it might be best to just undo all the changes you've made and try to compile the source from a newly extracted source tree.)

The change to 3.4 is only temporary and will only persist while that terminal session is open (and within that terminal only), by the way.

Thanks for the help, but it's the same problem...any more ideas?:(

---

### Post by PheonixKotori on 2008-05-29
Hi, and can I first say I'd strongly recommend using a pre-compiled binary from the Stepmania site. I just finished compiling it from source myself, after 2 patches, 4 hours, 6 dependency resolutions, and over a dozen swears :). 

That said, I didn't encounter your particular error, but that's probably because I patched it before it came up. Check the bottom post here:

[http://www.stepmania.com/forums/showthread.php?p=116881](http://www.stepmania.com/forums/showthread.php?p=116881) 

Download the two patch files to your Stepmania-src directory. Apply them from the command line with 'patch -p0 <gcc41.patch' and likewise for the other file. That may get you through a rough spot. 

A third patch I used with success was glibc.patch, found here:

[http://aur.archlinux.org/packages/stepmania/stepmania/stepmania-3.9-glibc.patch](http://aur.archlinux.org/packages/stepmania/stepmania/stepmania-3.9-glibc.patch) .

Treat it the same as the others. Then try make again.

One final note: I did all this, and ended up with the executable which ran fine (after I resolved a sound issue). Except if I passed a song, it would instantly repeat that song; if I failed it, it would exit to the menu as it should. While building it myself was a good experience, the end result wasn't much to look at. YMMV!

---

### Post by louis3234 on 2008-05-29
> **PheonixKotori said:**
> 
Download the two patch files to your Stepmania-src directory. Apply them from the command line with 'patch -p0 <gcc41.patch' and likewise for the other file. That may get you through a rough spot. 


Hey there, I don't quite understand how to apply them(forgive me 
T_T), when I tried, it says:
```
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -urNad src/GameState.h src/GameState.h
|--- src/GameState.h    2004-08-30 00:35:14.000000000 -0400
|+++ src/GameState.h    2006-11-30 20:10:36.000000000 -0500
--------------------------
File to patch:

```
How do I do this?:confused:

---

### Post by PheonixKotori on 2008-05-30
Well, I didn't see anything like that. Perhaps the patch files are in the wrong directory? My patch files are in my Stepmania-3.9-src folder, along with the configure and Makefiles. Maybe make sure that same folder is your working directory when you issue the patch command.

On the other hand, if there is no Stepmania-3.9-src/src/GameState.h file (which is what the error output is suggesting), then you have bigger problems that a patch will fix! You'd want to re-download the entire source and start from there. But those patch files locate their targets using relative path names, so it's likely just a case of the files being in the wrong place.

---

### Post by louis3234 on 2008-06-03
Oh my god..It's getting more and more confusing. Last time I put it under the wrong folder. But after I changed it, it said:```
patching file src/GameState.h
Reversed (or previously applied) patch detected!  Assume -R? [n]
```
After I hit enter for few times, it looks like this:```
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file src/GameState.h.rej
patching file src/NetworkSyncServer.h
Reversed (or previously applied) patch detected!  Assume -R? [n]
```
Darn that.:(

---

### Post by PheonixKotori on 2008-06-05
Not sure what to tell you. When I got those messages, I just deleted the source folder I was working on (after copying the patch files) and started over from a clean source folder.

---

### Post by louis3234 on 2008-06-08
GOD! The link is no longer available(the first two), when I tried for the third one, it's the "can't find file to patch at input line 3" error message again. Do you have other ways?

---

### Post by Folken Laëneck on 2008-06-09
I have found some others location for patches in this thread : [http://www.stepmania.com/forums/showthread.php?p=116881]("http://www.stepmania.com/forums/showthread.php?p=116881")

I also updated an how-to to apply these patches at : [http://doc.ubuntu-fr.org/stepmania]("http://doc.ubuntu-fr.org/stepmania")

Unfortunately, make fails with 2 errors :
```
arch/Threads/Threads_Pthreads.cpp: In member function &#8216;virtual int ThreadImpl_Pthreads::Wait()&#8217;:
arch/Threads/Threads_Pthreads.cpp:47: error: cast from &#8216;void*&#8217; to &#8216;int&#8217; loses precision
make[2]: *** [Threads_Pthreads.o] Error 1
make[2]: Leaving directory `/home/folken/Install/StepMania-3.9-src/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/folken/Install/StepMania-3.9-src/src'
make: *** [all-recursive] Error 1

```

Anobody has a solution ?
- I'm on Gutsy 64bits -

I've found an easier solution than compiling.
Just use the binary version provide on SourceForge and install lacking librairies using [getlibs]("http://ubuntuforums.org/showthread.php?t=474790")

---

