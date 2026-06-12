---
title: "Trying to install, cmake errors"
date: 2009-02-03
forum: General Help
---

### Post by Gotaro on 2009-02-03
I'm trying to install the yaWP widget, but I'm getting errors that another person has said he didn't get (original thread, "[_ISO a RELIABLE weather widget_](http://ubuntuforums.org/showthread.php?t=1057478)").  These are the same errors I got when I tried to manually compile the source code before.  On my previous quest to install a C++ compiler and whatever dependencies I thought I needed, I broke KDE to the point I could no longer login.  So step-by-step instructions might be needed! ^^;
```

gotaro@gotaro-linux:~/Downloads/yawp-0.1.65$ ./install.sh
KDE version: 4.2.00                                      
Using CMakeLists.kde42.txt                               
-- The C compiler identification is GNU                  
-- The CXX compiler identification is unknown            
-- Check for working C compiler: /usr/bin/gcc            
-- Check for working C compiler: /usr/bin/gcc -- works   
-- Detecting C compiler ABI info                         
-- Detecting C compiler ABI info - done                  
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.                  
-- Looking for Q_WS_X11                                                         
-- Looking for Q_WS_X11 - found                                                 
-- Looking for Q_WS_WIN                                                         
-- Looking for Q_WS_WIN - not found.                                            
-- Looking for Q_WS_QWS                                                         
-- Looking for Q_WS_QWS - not found.                                            
-- Looking for Q_WS_MAC                                                         
-- Looking for Q_WS_MAC - not found.                                            
-- Found Qt-Version 4.4.3 (using /usr/bin/qmake)                                
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so                                
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so - found                        
-- Looking for gethostbyname                                                    
-- Looking for gethostbyname - found                                            
-- Looking for connect                                                          
-- Looking for connect - found                                                  
-- Looking for remove                                                           
-- Looking for remove - found                                                   
-- Looking for shmat                                                            
-- Looking for shmat - found                                                    
-- Looking for IceConnectionNumber in ICE                                       
-- Looking for IceConnectionNumber in ICE - found                               
-- Found X11: /usr/lib/libX11.so                                                
-- Looking for include files CMAKE_HAVE_PTHREAD_H                               
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found                       
-- Looking for pthread_create in pthreads                                       
-- Looking for pthread_create in pthreads - not found                           
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE
-- Found Automoc4: /usr/bin/automoc4
-- Found Perl: /usr/bin/perl
-- Performing Test _OFFT_IS_64BIT
CMake Error at /usr/share/cmake-2.6/Modules/CMakeCXXInformation.cmake:17 (GET_FILENAME_COMPONENT):
  get_filename_component called with incorrect number of arguments
Call Stack (most recent call first):
  CMakeLists.txt:3 (PROJECT)


CMake Error: CMAKE_CXX_COMPILER not set, after EnableLanguage
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Performing Test _OFFT_IS_64BIT - Failed
-- Phonon Version: 4.3.0
-- Found Phonon: /usr/lib/libphonon.so
-- Found Phonon Includes: /usr/include/KDE;/usr/include
-- Found KDE 4.2 include dir: /usr/include
-- Found KDE 4.2 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
CMake Error at po/CMakeLists.txt:6 (MESSAGE):
  Please install the msgfmt binary


-- Configuring incomplete, errors occurred!
/home/gotaro/Downloads/yawp-0.1.65/build
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
Compilation failed, sorry :-(
```

This is a double post, sorry.  I guess it's time to migrate out of "Absolute Beginners"! :P  I see now I've been abusing it!

---

### Post by Crafty Kisses on 2009-02-03
Do you have the following package installed?
```
sudo apt-get install build-essential
```

---

### Post by Gotaro on 2009-02-03
> **Codename said:**
> Do you have the following package installed?
```
sudo apt-get install build-essential
```
I didn't have that package, and the install gets further after getting it!
```
gotaro@gotaro-linux:~/Downloads/yawp-0.1.65$ ./install.sh
KDE version: 4.2.00
Using CMakeLists.kde42.txt
-- The CXX compiler identification is GNU
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Found Qt-Version 4.4.3 (using /usr/bin/qmake)
-- Found X11: /usr/lib/libX11.so
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Phonon Version: 4.3.0
-- Found KDE 4.2 include dir: /usr/include
-- Found KDE 4.2 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
CMake Error at po/CMakeLists.txt:6 (MESSAGE):
  Please install the msgfmt binary


-- Configuring incomplete, errors occurred!
/home/gotaro/Downloads/yawp-0.1.65/build
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
Compilation failed, sorry :-(
```
I'm not sure about this "msgfmt" business! >:[  The search results in nothing from Adept.

---

### Post by Gotaro on 2009-02-03
Bump.  Let's hope for success today!  :)

---

### Post by binbash on 2009-02-03
Hmm 

  Please install the msgfmt binary

I guess msgfmt comes from gettext-tools so install it and try again

---

### Post by Gotaro on 2009-02-03
> **binbash said:**
> Hmm 

  Please install the msgfmt binary

I guess msgfmt comes from gettext-tools so install it and try again
That package isn't available for me?  Maybe I need another repository?  I instead tried installing gettext-kde, but that didn't help.

And again, another person had none of the same issues I'm having.
> **MistralWind said:**
> I just did this, as per the notes:
> tar -zxf yawp*
./install.sh
The automatic installer script worked fine for me, though YMMV. (My 8.10 was an upgrade.)

---

### Post by binbash on 2009-02-03
I am not on ubuntu but sudo apt-get install gettext or search for it : sudo apt-cache search gettext

---

### Post by SuperSonic4 on 2009-02-03
> **binbash said:**
> I am not on ubuntu but sudo apt-get install gettext or search for it : sudo apt-cache search gettext

I had this problem this afternoon, I found that 
```
sudo apt-get install gettext
```

solved the problem and install works from then on

---

### Post by Gotaro on 2009-02-03
> **SuperSonic4 said:**
> I had this problem this afternoon, I found that 
```
sudo apt-get install gettext
```

solved the problem and install works from then on
Yay!  That did it!  I don't know if it just reinstalled it or what..  I know I at least had gettext-base already installed.  Thanks to both of you for your help!  :)

---

### Post by kernelnewbie1 on 2010-05-13
:P

apt-get install gettext ! 

Thanks for every one on this thread........... it helped me a lot ,

---

### Post by carolinason on 2011-10-09
the thank you button is gone, so thank you for this post.

---

### Post by oldos2er on 2011-10-09
Closed, necromancy.

---

