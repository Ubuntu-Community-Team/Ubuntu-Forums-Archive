---
title: "Problem compiling from source"
date: 2009-06-13
forum: General Help
---

### Post by Shampyon on 2009-06-13
I've been trying to com[ile Mizio from source, but I keep getting this error:

```
checking build system type... i686-pc-linux-gnu   
checking host system type... i686-pc-linux-gnu    
checking target system type... i686-pc-linux-gnu  
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes                      
checking whether build environment is sane... yes           
checking for gawk... gawk                                   
checking whether make sets $(MAKE)... yes                   
checking for style of include used by make... GNU           
checking for gcc... gcc                                     
checking for C compiler default output... a.out             
checking whether the C compiler works... yes                
checking whether we are cross compiling... no               
checking for suffix of executables...                       
checking for suffix of object files... o                    
checking whether we are using the GNU C compiler... yes     
checking whether gcc accepts -g... yes                      
checking for gcc option to accept ANSI C... none needed     
checking dependency style of gcc... gcc3                    
checking how to run the C preprocessor... gcc -E            
checking for g++... g++                                     
checking whether we are using the GNU C++ compiler... yes   
checking whether g++ accepts -g... yes                      
checking dependency style of g++... gcc3                    
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes                   
checking whether g++ supports -Wno-long-long... yes            
checking whether g++ supports -Wnon-virtual-dtor... yes        
checking whether g++ supports -fno-exceptions... yes           
checking whether g++ supports -fno-check-new... yes            
checking whether g++ supports -fno-common... yes               
checking whether g++ supports -fexceptions... yes              
checking how to run the C++ preprocessor... g++ -E             
not using lib directory suffix                                 
checking for ld used by GCC... /usr/bin/ld                     
checking if the linker (/usr/bin/ld) is GNU ld... yes          
checking for /usr/bin/ld option to reload object files... -r   
checking for BSD-compatible nm... /usr/bin/nm -B               
checking for a sed that does not truncate output...                                                                                                                                   
checking whether ln -s works... yes                                                                                                                                                   
checking how to recognise dependant libraries... pass_all                                                                                                                             
checking for egrep... grep -E                                                                                                                                                         
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
checking dlfcn.h usability... yes                                                                                                                                                     
checking dlfcn.h presence... yes                                                                                                                                                      
checking for dlfcn.h... yes                                                                                                                                                           
checking the maximum length of command line arguments... 32768                                                                                                                        
checking command to parse /usr/bin/nm -B output from gcc object... ok                                                                                                                 
checking for objdir... .libs                                                                                                                                                          
checking for ranlib... ranlib                                                                                                                                                         
checking for strip... strip                                                                                                                                                           
checking if gcc static flag  works... no                                                                                                                                              
checking if gcc supports -fno-rtti -fno-exceptions... no                                                                                                                              
checking for gcc option to produce PIC... -fPIC                                                                                                                                       
checking if gcc PIC flag -fPIC works... yes                                                                                                                                           
checking if gcc supports -c -o file.o... yes                                                                                                                                          
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes                                                                                                        
checking whether -lc should be explicitly linked in... no                                                                                                                             
checking how to hardcode library paths into programs... immediate                                                                                                                     
checking whether stripping libraries is possible... yes                                                                                                                               
checking dynamic linker characteristics... GNU/Linux ld.so                                                                                                                            
checking if libtool supports shared libraries... yes                                                                                                                                  
checking whether to build shared libraries... yes                                                                                                                                     
checking whether to build static libraries... no                                                                                                                                      
configure: creating libtool                                                                                                                                                           
appending configuration tag "CXX" to libtool                                                                                                                                          
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes                                                                                                        
checking for g++ option to produce PIC... -fPIC                                                                                                                                       
checking if g++ PIC flag -fPIC works... no                                                                                                                                            
checking if g++ supports -c -o file.o... no                                                                                                                                           
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes                                                                                                        
checking whether -lc should be explicitly linked in... yes                                                                                                                            
checking how to hardcode library paths into programs... immediate                                                                                                                     
checking whether stripping libraries is possible... yes                                                                                                                               
checking dynamic linker characteristics... GNU/Linux ld.so                                                                                                                            
appending configuration tag "GCJ" to libtool                                                                                                                                          
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no                                                                                                                     
checking for gcj option to produce PIC... -fPIC                                                                                                                                       
checking if gcj PIC flag -fPIC works... no                                                                                                                                            
checking if gcj supports -c -o file.o... no                                                                                                                                           
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes                                                                                                        
checking whether -lc should be explicitly linked in... yes                                                                                                                            
checking how to hardcode library paths into programs... immediate                                                                                                                     
checking whether stripping libraries is possible... yes                                                                                                                               
checking dynamic linker characteristics... GNU/Linux ld.so                                                                                                                            
checking for msgfmt... /usr/bin/msgfmt                                                                                                                                                
checking for gmsgfmt... /usr/bin/msgfmt                                                                                                                                               
checking for xgettext... /usr/bin/xgettext                                                                                                                                            
checking for strlcat... no                                                                                                                                                            
checking if strlcat needs custom prototype... yes - in libkdefakes                                                                                                                    
checking for strlcpy... no                                                                                                                                                            
checking if strlcpy needs custom prototype... yes - in libkdefakes                                                                                                                    
checking for main in -lutil... yes                                                                                                                                                    
checking for main in -lcompat... no                                                                                                                                                   
checking for crypt in -lcrypt... yes                                                                                                                                                  
checking for socklen_t... socklen_t                                                                                                                                                   
checking for dnet_ntoa in -ldnet... no                                                                                                                                                
checking for dnet_ntoa in -ldnet_stub... no                                                                                                                                           
checking for inet_ntoa... yes                                                                                                                                                         
checking for connect... yes                                                                                                                                                           
checking for remove... yes                                                                                                                                                            
checking for shmat... yes                                                                                                                                                             
checking crt_externs.h usability... no                                                                                                                                                
checking crt_externs.h presence... no                                                                                                                                                 
checking for crt_externs.h... no                                                                                                                                                      
checking for _NSGetEnviron... no                                                                                                                                                      
checking for sys/types.h... (cached) yes                                                                                                                                              
checking for stdint.h... (cached) yes                                                                                                                                                 
checking for poll in -lpoll... no                                                                                                                                                     
checking CoreAudio/CoreAudio.h usability... no                                                                                                                                        
checking CoreAudio/CoreAudio.h presence... no                                                                                                                                         
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking if Qt compiles without flags... yes
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
```

I've tried installing the KDE modules through Synaptic, and ran
```
 sudo apt-get install kde-devel

```
in Konsole. The error still comes up.

---

### Post by Agent ME on 2009-06-13
Try grabbing the [kdebase-dev](apt://kdebase-dev) package. If that doesn't do it, I'd look for any other packages matching the pattern "kde*-dev".

---

### Post by Shampyon on 2009-06-13
> **Agent ME said:**
> Try grabbing the [kdebase-dev](apt://kdebase-dev) package. If that doesn't do it, I'd look for any other packages matching the pattern "kde*-dev".

It doesn't seem to have had any effect, unfortunately :(

---

### Post by viezz on 2009-06-13
```
configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
```

did you used some specific prefix path? because from the error information, it looks like you've used it.

---

### Post by Shampyon on 2009-06-13
That's just what I get from using the basic *./configure* command.

---

