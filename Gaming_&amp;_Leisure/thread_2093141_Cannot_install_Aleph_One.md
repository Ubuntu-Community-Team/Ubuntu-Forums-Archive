---
title: "Cannot install Aleph One"
date: 2012-12-10
forum: Gaming &amp; Leisure
---

### Post by Whipp on 2012-12-10
Hi I'm having problems with this I've come a long way and solved a lot of problems thus far but now I'm stuck after spending many hours and days at this.

I have a 2GHZ quad core AMD processor, 64 bit, Radeon HD5670 graphics card, 2GB ram, Motherboard M4A87TD EVO.

I'm trying to install Aleph One by compiling from source. I downloaded the tarball and open terminal in window and press ./configure. After some problems that now completes fine. Now the problem is the next step: When I type "make" I get this gobbldey guk error:

GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for x86_64-pc-linux-gnu
Reading makefiles...
Updating goal targets....
 File `all' does not exist.
   File `all-am' does not exist.
  Must remake target `all-am'.
  Successfully remade target file `all-am'.
Must remake target `all'.
Successfully remade target file `all'.
make[3]: Entering directory `/home/brian/AlephOne-20120514/Source_Files/LibNAT'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/brian/AlephOne-20120514/Source_Files/LibNAT'
Making all in Lua
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for x86_64-pc-linux-gnu
Reading makefiles...
Updating goal targets....
 File `all' does not exist.
   File `all-am' does not exist.
     File `liba1lua.a' does not exist.
       File `lua_map.o' does not exist.
      Must remake target `lua_map.o'.
make[3]: Entering directory `/home/brian/AlephOne-20120514/Source_Files/Lua'
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../Source_Files/CSeries -I../../Source_Files/Files -I../../Source_Files/GameWorld -I../../Source_Files/Input -I../../Source_Files/Misc -I../../Source_Files/ModelView -I../../Source_Files/Network -I../../Source_Files/Pfhortran -I../../Source_Files/RenderMain -I../../Source_Files/RenderOther -I../../Source_Files/Sound -I../../Source_Files/XML -I../../Source_Files  -I/usr/include/libpng12   -D_FORTIFY_SOURCE=2    -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DSDL  -g -O2 -MT lua_map.o -MD -MP -MF .deps/lua_map.Tpo -c -o lua_map.o lua_map.cpp
In file included from lua_map.h:39:0,
                 from lua_map.cpp:24:
lua_templates.h: In instantiation of &#8216;static index_t L_LazyEnum<name, index_t>::ToIndex(lua_State*, int) [with char* name = ((char*)(& Lua_Sound_Name)); index_t = short int; lua_State = lua_State]&#8217;:
lua_map.cpp:1204:33:   required from here
lua_templates.h:499:8: error: &#8216;_lookup&#8217; was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
lua_templates.h:499:8: note: declarations in dependent base &#8216;L_Enum<((char*)(& Lua_Sound_Name)), short int>&#8217; are not found by unqualified lookup
lua_templates.h:499:8: note: use &#8216;L_LazyEnum::_lookup&#8217; instead
make[3]: *** [lua_map.o] Error 1
make[3]: Leaving directory `/home/brian/AlephOne-20120514/Source_Files/Lua'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/brian/AlephOne-20120514/Source_Files'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brian/AlephOne-20120514'
make: *** [all] Error 2

So now it's stuck at this point, I can't get to the final step of "sudo make install"

Can anyone tell me how to fix this? thanks!



:popcorn:

These are the instructions I have followed thus far:

Aleph One/SDL Unix Installation Instructions
============================================

As implied by its name, Aleph One/SDL requires the Simple DirectMedia Layer
(SDL) library, available from the official SDL site:

  [http://www.libsdl.org/](http://www.libsdl.org/)

If you didn't install SDL from source, you have to install the "SDL-devel"
package to compile Aleph One.

You also have to install the "SDL_image" and "SDL_net" libraries which can be
found here:

  [http://www.libsdl.org/projects/SDL_image/](http://www.libsdl.org/projects/SDL_image/)
  [http://www.libsdl.org/projects/SDL_net/](http://www.libsdl.org/projects/SDL_net/)

Support for Lua scripting, which may be required by some scenarios, requires
you to have Lua installed. The source is available from the official Lua site:

  [http://www.lua.org](http://www.lua.org)

Precompiled RPM packages of Lua can be downloaded from:

  [http://gwpr03.microlink.com.br/~acosta/lua/](http://gwpr03.microlink.com.br/~acosta/lua/)

The mutiplayer audio chat feature of Aleph One requires the Speex library
which can be downloaded from

  [http://www.speex.org](http://www.speex.org)


Installing the program
----------------------

As with any autoconfiguring GNU software, installation is as easy as this:

 $ ./configure
 $ make
 [become root]
 # make install

---

### Post by maxmalkav on 2012-12-12
Today I've been trying to compile Aleph too, I got the same error.
I also got this error message in the log:

```

lua_templates.h:499:8: note: use ‘L_LazyEnum::_lookup’ instead

```

I edited lua_templates, line 499 changing _lookup for L_LazyEnum:_lookup. Now the code is compiling, but I don't know if it's going to work properly ;)

---

### Post by holastickboy on 2012-12-13
Normally Playdeb has a package, but they are currently having hardware issues and the site is down.  Makes life much easier.  Don't think I have compiled a decent sized program (with the exception of small apps such as no-ip) since the year 2000.  Did it work in the end?

---

### Post by decoherence on 2012-12-13
Hi,

I just ran across this problem and wanted to report that maxmalkav's suggestion (which is to do what the error message suggests) works for me on Fedora 17. It compiles and even runs!

Double shotguns, here I come!

Thanks guys :)

---

### Post by Whipp on 2012-12-22
> **maxmalkav said:**
> Today I've been trying to compile Aleph too, I got the same error.
I also got this error message in the log:

```

lua_templates.h:499:8: note: use ‘L_LazyEnum::_lookup’ instead

```I edited lua_templates, line 499 changing _lookup for L_LazyEnum:_lookup. Now the code is compiling, but I don't know if it's going to work properly ;)

That looks like it should work, how do you edit a Lua Template? But if what you installed was just the engine, you will still need the marathon files that have the actual game files that run like you can see here: [http://alephone.cebix.net/](http://alephone.cebix.net/)

So anyway I'm going to look into this I haven't looked at my log and I'm not sure where it is, and I'm not sure how to edit a lua template but at least this is something to look into, I was totally out of suggestions on what to try, thanks!

---

### Post by Whipp on 2012-12-22
Hmmm no luck yet on figuring out how to edit lua_templates. Google reveals nothing yet :(

---

### Post by Whipp on 2012-12-22
I got it! I went to my installation folder > source files > LUA > then opened lua_templates.h with GEANY editor. The text editor opens it but I figured out had to use geany otherwise I have to count 499 lines of code LOL. So I ran make with success, then run sudo make install, and now it installed fine. All I think I need to do now is type the correct command in a terminal to start it.

EDIT: Still can't get the program to run though, says images, sounds, etc files are not correctly installed DOH!

---

### Post by Sealbhach on 2013-01-10
I had to change line 499 in lua_templates.h to look like this
```
else if(L_LazyEnum::_lookup(L, index, to)) return to; 
```Note there are two :: after the Enum

The compiler complained that there was only one, at first.

That message about maps, images sounds etc means the AlephOne binary is is looking for the game data files for whatever game you want to play.

You can specify where the game data files are at the command line. 

Say for example you want to play **Excalibur: Morgana's Revenge** you can download the game from [here]("http://sourceforge.net/projects/emr3/files/complete-scenario4%20%28linux%29/EMR%203.0%202007-06-02%20%28Linux%29/emr-3.0-0602.tgz/downloadhttp://"). Extract it somewhere in your home folder e.g. in this example a folder called Games. This package contains game data files in the share-emr subfolder. To play them using AlephOne, launch it with the command:

```
ALEPHONE_DATA='/home/yourusername/Games/emr-3.0/share-emr' alephone
```Change the command to whatever your setup is.

However, that particular game comes with a makefile so you can make and sudo make install it so that it plays as the makers intended it.

.

---

