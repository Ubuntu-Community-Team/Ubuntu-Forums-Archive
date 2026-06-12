---
title: "Trouble Compiling Warzone 2100 Beta 10"
date: 2010-02-26
forum: Gaming &amp; Leisure
---

### Post by MasterNetra on 2010-02-26
I did run ./autogen and installed what it told me to. but when trying to configure and make It claims it can't find sdl package...its not in repo so where do I find it?

```

$ ./configure && make depend
checking for a BSD-compatible install... /usr/bin/install -c                        
checking whether build environment is sane... yes                                   
checking for a thread-safe mkdir -p... /bin/mkdir -p                                
checking for gawk... no                                                             
checking for mawk... mawk                                                           
checking whether make sets $(MAKE)... yes                                           
checking how to create a ustar tar archive... gnutar                                
checking build system type... i686-pc-linux-gnu                                     
checking host system type... i686-pc-linux-gnu                                      
checking for style of include used by make... GNU                                   
checking for gcc... gcc                                                             
checking for C compiler default output file name... a.out                           
checking whether the C compiler works... yes                                        
checking whether we are cross compiling... no                                       
checking for suffix of executables...                                               
checking for suffix of object files... o                                            
checking whether we are using the GNU C compiler... yes                             
checking whether gcc accepts -g... yes                                              
checking for gcc option to accept ISO C89... none needed                            
checking dependency style of gcc... gcc3                                            
checking for gcc option to accept ISO C99... -std=gnu99                             
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99  
checking for ranlib... ranlib                                                       
checking for g++... g++                                                             
checking whether we are using the GNU C++ compiler... yes                           
checking whether g++ accepts -g... yes                                              
checking dependency style of g++... gcc3                                            
checking for bison... bison -y                                                      
checking for bison >= 1.31... found 2.4.1, ok                                       
checking for flex... flex                                                           
checking lex output file root... lex.yy                                             
checking lex library... -lfl                                                        
checking whether yytext is a pointer... yes                                         
checking for flex >= 2.5.33... found 2.5.35, ok                                     
checking for flex != 2.5.34... not found, good                                      
checking whether perl executable path has been provided... no                       
checking for perl... /usr/bin/perl                                                  
checking for a sed that does not truncate output... /bin/sed                        
checking for grep that handles long lines and -e... /bin/grep                       
checking for perl version... 5.10.0                                                 
checking for gawk... (cached) mawk                                                  
checking how to run the C preprocessor... gcc -std=gnu99 -E                         
checking for egrep... /bin/grep -E                                                  
checking for ANSI C header files... yes                                             
checking for sys/types.h... yes                                                     
checking for sys/stat.h... yes                                                      
checking for stdlib.h... yes                                                        
checking for string.h... yes                                                        
checking for memory.h... yes                                                        
checking for strings.h... yes                                                       
checking for inttypes.h... yes                                                      
checking for stdint.h... yes                                                        
checking for unistd.h... yes                                                        
checking minix/config.h usability... no                                             
checking minix/config.h presence... no                                              
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for strlcpy... no
checking for strlcat... no
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
./configure: line 6943: gt_INTL_MACOSX: command not found
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
./configure: line 7831: msgfmt: command not found
checking for msgfmt >= 0.15... ./configure: line 7849: [: : integer expression expected
./configure: line 7851: [: : integer expression expected
found , ok
./configure: line 7831: xgettext: command not found
checking for xgettext >= 0.15... ./configure: line 7849: [: : integer expression expected
./configure: line 7851: [: : integer expression expected
found , ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for pkg-config >= 0.9... found 0.22, ok
checking whether to build NSIS installer... no
checking whether to compile in debug mode... no
checking for SDL... configure: error: Package requirements (sdl >= 1.2) were not met:

No package 'sdl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SDL_CFLAGS
and SDL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by DoktorSeven on 2010-02-26
It's talking about "libsdl1.2", which should be in your packages.  And since you're compiling, you need "libsdl1.2-dev" -- ANYTIME you are compiling something and it complains about a missing package, do an apt-cache search (or search in Synaptic) for that package and install the most likely candidate **that ends in *-dev***.

---

### Post by MasterNetra on 2010-02-26
> **DoktorSeven said:**
> It's talking about "libsdl1.2", which should be in your packages.  And since you're compiling, you need "libsdl1.2-dev" -- ANYTIME you are compiling something and it complains about a missing package, do an apt-cache search (or search in Synaptic) for that package and install the most likely candidate **that ends in *-dev***.

Thanks! Finally started playing with compile, sure helps to know when it needs something its lib+(listed requirement)+-dev, at this rate though it may take awhile to get Warzone Beta 10 compiled (is running into many other requirements) lol

Edit: Just ran into "vorbisfile", must hunt for that, no libvorbisfile-dev in repo, closes to it is some ruby file, tried it but no go. :/

---

### Post by Perfect Storm on 2010-02-26
```
sudo apt-get install libvorbis-dev
```

If it's not available, you need to check your source list and see if deb-src are enable for all of your sources.

You can also check my guide (a bit dated 8.10), but it will give you a hint how to compile warzone: [http://gwos.org/doku.php/guides:64bit:warzone_2100](http://gwos.org/doku.php/guides:64bit:warzone_2100)

---

### Post by MasterNetra on 2010-02-26
lol no wonder I was doing:

```

sudo apt-get install libvorbisfile-dev

```

I suppose thats one way of not getting it lol.

Edit: Just realised also that I forgot o switch OS info to Kubuntu 9.10, and I didn't have source checked in KPackage's software sources either.

---

### Post by MasterNetra on 2010-02-27
Gah, it crashes when I save a game. Its Beta I know, but I think I'll stick with stable... so now how do I remove it? Its not seen by the package managers.

---

### Post by Perfect Storm on 2010-02-27
Did you use checkinstall or make install?

---

### Post by MasterNetra on 2010-02-27
> **Artificial Intelligence said:**
> Did you use checkinstall or make install?

Yes, but it failed due to the lack of a version number in desc or something like that, trying it again this time putting in some values.

Edit: Done though and removed. lol thanks. I had thought sense it installed(was playable) despite the failure that I was still in the clear I guess not if you want to remove it later.

---

