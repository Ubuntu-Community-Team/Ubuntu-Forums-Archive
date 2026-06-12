---
title: "Guide: Howto get Smooth Tasks installed:"
date: 2009-10-15
forum: Desktop Environments
---

### Post by t.rei on 2009-10-15
Hello,
 
I myself am using Smooth Tasks on Kubuntu for quite a while now. It is under active development and improving quickly. In my opinion it is by far the best "Taskbar" the linux environments have to offer currently, but that might be a matter of taste.
 
So for anyone who would like to give it a try and still be able to remove it comfortably here's a little howto:
 
**1. Get Smooth Tasks**
[http://kde-look.org/content/show.php/Smooth+Tasks?content=101586](http://kde-look.org/content/show.php/Smooth+Tasks?content=101586)
 
**2. get checkinstall if you don't already have it.**
You might need to also get some kde development packages to compile. Please report here if any. Since I already have all of them installed on my system I do not quite know what else needs to be installed. Thanks.
```
apt-get install checkinstall kdelibs5-dev kdebase-workspace-dev
```

**3. unpack the package and cd into the directory**
Using Dolphin:
* Right click on the package -> extract here.
* click on the folder
* press F4 to bring up the integrated konsole
 
**4. build the package**
type into the console:
```
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
make -j 2
sudo checkinstall
```--> for (2) enter 'smoothtasks' (without any ' )
--> for (11) also enter 'smoothtasks' 
 
The last two steps are important, because if you download updated sources and want to rebuild the package you need to enter these exact two names, otherwise you might end up with "could not install because it provides X wich is already provided by Y" errors.
 
Checkinstall will now have built and installed a package named smoothtasks to your system. (removable by running 'apt-get remove smoothtasks' or 'dpkg -r smoothtasks')
 
**5. restart your plasma-desktop**
Hit your krunner key-combo (default: alt+f2)
```
kquitapp plasma-desktop
```Hit the krunner key again
```
plasma-desktop
```**6. Now add smoothtasks to your panel **
and set it up the way you like it. ;)
 
 
All thanks go to [COLOR=darkred]**panzi**[/COLOR] who has done a GREAT job providing this to the community.

---

### Post by t.rei on 2009-10-16
edit: changed killall to kquitapp

---

### Post by Falc7 on 2009-10-16
I get this message:
 ```
jamie@jamie-kubuntu:~/Desktop/smooth-tasks-src-wip-2009-10-15/build$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`                                                                                                               
-- The C compiler identification is GNU                                                                              
-- The CXX compiler identification is GNU                                                                            
-- Check for working C compiler: /usr/bin/gcc                                                                        
-- Check for working C compiler: /usr/bin/gcc -- works                                                               
-- Detecting C compiler ABI info                                                                                     
-- Detecting C compiler ABI info - done                                                                              
-- Check for working CXX compiler: /usr/bin/c++                                                                      
-- Check for working CXX compiler: /usr/bin/c++ -- works                                                             
-- Detecting CXX compiler ABI info                                                                                   
-- Detecting CXX compiler ABI info - done                                                                            
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):                                             
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in                                                           
  /home/jamie/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps                                                                                                                    
Call Stack (most recent call first):                                                                                 
  CMakeLists.txt:1 (find_package)                                                                                    


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
jamie@jamie-kubuntu:~/Desktop/smooth-tasks-src-wip-2009-10-15/build$

```

---

### Post by t.rei on 2009-10-16
Hm, ok - this is what it looks like for me. If I understand correctly there might be a requirement for qt-dev files? It's a rather wild quess, but you might try and check if 
```
sudo apt-get install libqt4-dev
```changes anything.

```
$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
-- The C compiler identification is GNU                                                                       
-- The CXX compiler identification is GNU                                                                     
-- Check for working C compiler: /usr/bin/gcc                                                                 
-- Check for working C compiler: /usr/bin/gcc -- works                                                        
-- Detecting C compiler ABI info                                                                              
-- Detecting C compiler ABI info - done                                                                       
-- Check for working CXX compiler: /usr/bin/c++                                                               
-- Check for working CXX compiler: /usr/bin/c++ -- works                                                      
-- Detecting CXX compiler ABI info                                                                            
-- Detecting CXX compiler ABI info - done                                                                     
-- Looking for Q_WS_X11                                                                                       
-- Looking for Q_WS_X11 - found                                                                               
-- Looking for Q_WS_WIN                                                                                       
-- Looking for Q_WS_WIN - not found.                                                                          
-- Looking for Q_WS_QWS                                                                                       
-- Looking for Q_WS_QWS - not found.                                                                          
-- Looking for Q_WS_MAC                                                                                       
-- Looking for Q_WS_MAC - not found.                                                                          
-- Found Qt-Version 4.5.2 (using /usr/bin/qmake)                                                              
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
-- Phonon Version: 4.3.1                                                                                       
-- Found Phonon: /usr/lib/libphonon.so                                                                         
-- Found Phonon Includes: /usr/include/qt4/KDE;/usr/include/qt4                                                
-- Performing Test _OFFT_IS_64BIT                                                                              
-- Performing Test _OFFT_IS_64BIT - Failed                                                                     
-- Performing Test HAVE_FPIE_SUPPORT                                                                           
-- Performing Test HAVE_FPIE_SUPPORT - Success                                                                 
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL                                                             
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success                                                   
-- Performing Test __KDE_HAVE_GCC_VISIBILITY                                                                   
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE 4.3 include dir: /usr/include
-- Found KDE 4.3 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Found KDE4Workspace: /usr/lib/cmake/KDE4Workspace-4.3.2/KDE4WorkspaceConfig.cmake
-- Configuring done
-- Generating done
-- Build files have been written to: /home/username/smooth-tasks-src-wip-2009-10-15/build

```

---

### Post by Falc7 on 2009-10-16
```
jamie@jamie-kubuntu:~/Desktop/smooth-tasks-src-wip-2009-10-15/build$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` 
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):                                                    
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in                                                                  
  /home/jamie/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps      
Call Stack (most recent call first):                                                                                        
  CMakeLists.txt:1 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
jamie@jamie-kubuntu:~/Desktop/smooth-tasks-src-wip-2009-10-15/build$

```

---

### Post by t.rei on 2009-10-16
ok, so there is still something missing.

This might have helped - and might help in the future.
```
$ dpkg -S FindKDE4Internal
kdelibs5-dev: /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake

```

```

sudo apt-get install kdelibs5-dev
```Updated howto to include the package. Hope this helps now, and thanks for the feedback.

---

### Post by Falc7 on 2009-10-17
```
jamie@jamie-kubuntu:~$ dpkg -S FindKDE4Internal
dpkg: *FindKDE4Internal* not found.

```

Strange.

---

### Post by t.rei on 2009-10-17
But it should find it after you installed kdelibs5-dev, doesn't it?

---

### Post by Falc7 on 2009-10-17
Tbh i am not sure, now i get this message:

```
jamie@jamie-kubuntu:~/Desktop/smooth-tasks-src-wip-2009-10-15/build$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
-- Looking for Q_WS_X11                                                                                                    
-- Looking for Q_WS_X11 - found                                                                                            
-- Looking for Q_WS_WIN                                                                                                    
-- Looking for Q_WS_WIN - not found.                                                                                       
-- Looking for Q_WS_QWS                                                                                                    
-- Looking for Q_WS_QWS - not found.                                                                                       
-- Looking for Q_WS_MAC                                                                                                    
-- Looking for Q_WS_MAC - not found.                                                                                       
-- Found Qt-Version 4.5.2 (using /usr/bin/qmake)                                                                           
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
-- Phonon Version: 4.3.1                                                                                                                
-- Found Phonon: /usr/lib/libphonon.so                                                                                                  
-- Found Phonon Includes: /usr/include/qt4/KDE;/usr/include/qt4                                                                         
-- Performing Test _OFFT_IS_64BIT                                                                                                       
-- Performing Test _OFFT_IS_64BIT - Failed                                                                                              
-- Performing Test HAVE_FPIE_SUPPORT                                                                                                    
-- Performing Test HAVE_FPIE_SUPPORT - Success                                                                                          
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL                                                                                      
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success                                                                            
-- Performing Test __KDE_HAVE_GCC_VISIBILITY                                                                                            
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success                                                                                  
-- Found KDE 4.3 include dir: /usr/include                                                                                              
-- Found KDE 4.3 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
------
                 NOTE: msgfmt not found. Translations will *not* be installed
------
CMake Error at /usr/share/cmake-2.6/Modules/FindPackageHandleStandardArgs.cmake:57 (MESSAGE):
  Could NOT find KDE4Workspace (missing: KDE4Workspace_CONFIG)
Call Stack (most recent call first):
  /usr/share/kde4/apps/cmake/modules/FindKDE4Workspace.cmake:70 (find_package_handle_standard_args)
  applet/CMakeLists.txt:5 (find_package)


-- Configuring incomplete, errors occurred!
jamie@jamie-kubuntu:~/Desktop/smooth-tasks-src-wip-2009-10-15/build$

```

---

### Post by t.rei on 2009-10-19
dpkg -S KDE4Workspace returned

kdebase-workspace-dev and kdelibs5-dev

---

### Post by Falc7 on 2009-10-19
```
jamie@jamie-kubuntu:~/Desktop/smooth-tasks-src-wip-2009-10-15/build$ dpkg -S KDE4Workspace returned
kdelibs5-dev: /usr/share/kde4/apps/cmake/modules/FindKDE4Workspace.cmake
dpkg: *returned* not found.

```

---

### Post by t.rei on 2009-10-20
the "S" stands for search - so I can look up on my install where the things are, that you are missing.

you need to run "apt-get install X" if X was the result of that search.

---

### Post by Falc7 on 2009-10-20
yay its working, thanks!

I've got Stasks installed a widget, how do i remove it completely from my add widgets menu?

I've just noticed a newer version has come out, to upgrade do i have to do it all over again? Or whats the best way?

---

### Post by Falc7 on 2009-10-27
Anyone know the best way to upgrade to the newest version? Do i need to completely remove the old one?

---

### Post by t.rei on 2009-10-27
No you dont.
All you have to do is - if you followed the instructions in this post - run it again in the new sources you downloaded and enter the same "names" as you did when you installed it the first time.

> 
--> for (2) enter 'smoothtasks' (without any ' )
--> for (11) also enter 'smoothtasks' 


---

### Post by Falc7 on 2009-10-27
ah thanks

---

### Post by pumrel on 2010-05-16
Hi,
I'm trying really hard, but there must be something I'm missing.

```
root@petr-sidux:/home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build# make -j 2
Scanning dependencies of target translations
Scanning dependencies of target plasma_applet_smooth-tasks_automoc                                                                                                                                                   
Generating TaskIcon.moc                                                                                                                                                                                              
[  0%] Built target translations                                                                                                                                                                                     
Generating Task.moc
Generating TaskItem.moc                                                                                                                                                                                              
Generating Light.moc                                                                                                                                                                                                 
Generating Applet.moc                                                                                                                                                                                                
Generating moc_PlasmaToolTip.cpp                                                                                                                                                                                     
Generating moc_FixedItemCountTaskbarLayout.cpp                                                                                                                                                                       
Generating moc_ToggleAnimation.cpp                                                                                                                                                                                   
Generating moc_LimitSqueezeTaskbarLayout.cpp                                                                                                                                                                         
Generating moc_ToolTipBase.cpp                                                                                                                                                                                       
Generating moc_ToolTipWidget.cpp                                                                                                                                                                                     
Generating moc_DelayedToolTip.cpp                                                                                                                                                                                    
Generating moc_FadedText.cpp                                                                                                                                                                                         
Generating moc_CloseIcon.cpp                                                                                                                                                                                         
Generating moc_ByShapeTaskbarLayout.cpp                                                                                                                                                                              
Generating moc_WindowPreview.cpp                                                                                                                                                                                     
Generating moc_SmoothToolTip.cpp                                                                                                                                                                                     
Generating moc_TaskStateAnimation.cpp                                                                                                                                                                                
Generating moc_FixedSizeTaskbarLayout.cpp                                                                                                                                                                            
Generating moc_MaxSqueezeTaskbarLayout.cpp                                                                                                                                                                           
Generating moc_TaskbarLayout.cpp                                                                                                                                                                                     
/home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/TaskbarLayout.h:218: Warning: Class TaskbarLayout implements the interface QGraphicsLayout but does not list it in Q_INTERFACES. qobject_cast to QGraphicsLayout will not work!
[  0%] Built target plasma_applet_smooth-tasks_automoc
[  3%] Generating ui_Appearance.h
[  7%] Generating qrc_resources.cxx                                                                                                                                                                                  
[ 11%] Generating ui_General.h                                                                                                                                                                                       
Scanning dependencies of target plasma_applet_smooth-tasks                                                                                                                                                           
[ 14%] Building CXX object applet/CMakeFiles/plasma_applet_smooth-tasks.dir/plasma_applet_smooth-tasks_automoc.o                                                                                                     
[ 18%] Building CXX object applet/CMakeFiles/plasma_applet_smooth-tasks.dir/SmoothTasks/Applet.o                                                                                                                     
In file included from /usr/include/KDE/NETRootInfo:1,                                                                                                                                                                
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/Applet.cpp:31:
/usr/include/KDE/../netwm.h:33:22: error: X11/Xlib.h: No such file or directory
/usr/include/KDE/../netwm.h:34:23: error: X11/Xutil.h: No such file or directory
/usr/include/KDE/../netwm.h:35:23: error: X11/Xatom.h: No such file or directory
In file included from /usr/include/KDE/NETRootInfo:1,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/WindowPreview.h:26,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/../../applet/SmoothTasks/CloseIcon.h:27,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/moc_CloseIcon.cpp:10,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/plasma_applet_smooth-tasks_automoc.cpp:12:
/usr/include/KDE/../netwm.h:33:22: error: X11/Xlib.h: No such file or directory
/usr/include/KDE/../netwm.h:34:23: error: X11/Xutil.h: No such file or directory
/usr/include/KDE/../netwm.h:35:23: error: X11/Xatom.h: No such file or directory
In file included from /usr/include/KDE/NETRootInfo:1,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/Applet.cpp:31:
/usr/include/KDE/../netwm.h:98: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:160: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:167: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:264: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:264: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:283: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:283: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:348: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:348: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:406: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:425: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:425: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:435: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:435: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:512: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:513: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:513: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:521: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:539: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:539: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:570: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:587: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:603: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:614: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:614: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:623: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:623: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:662: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:670: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:718: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:733: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:742: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:742: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:753: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:754: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:754: error: ‘Window’ has not been declared
In file included from /usr/include/KDE/NETRootInfo:1,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/Applet.cpp:31:
/usr/include/KDE/../netwm.h:768: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:781: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:782: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:782: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:790: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:790: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:805: error: ‘Atom’ has not been declared
/usr/include/KDE/../netwm.h:859: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:859: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:869: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:870: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1020: error: ‘Bool’ does not name a type
/usr/include/KDE/../netwm.h:1039: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1137: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1201: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:1206: error: ‘Time’ does not name a type
/usr/include/KDE/../netwm.h:1242: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:1247: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:1341: error: ‘Atom’ has not been declared
/usr/include/KDE/../netwm.h:1341: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1039: error: ‘True’ was not declared in this scope
/usr/include/KDE/../netwm.h:1363: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1363: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1367: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1368: error: ‘Window’ has not been declared
In file included from /usr/include/KDE/NETRootInfo:1,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/WindowPreview.h:26,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/../../applet/SmoothTasks/CloseIcon.h:27,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/moc_CloseIcon.cpp:10,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/plasma_applet_smooth-tasks_automoc.cpp:12:
/usr/include/KDE/../netwm.h:98: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:160: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:167: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:264: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:264: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:283: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:283: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:348: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:348: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:406: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:425: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:425: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:435: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:435: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:512: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:513: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:513: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:521: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:539: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:539: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:570: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:587: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:603: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:614: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:614: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:623: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:623: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:662: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:670: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:718: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:733: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:742: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:742: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:753: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:754: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:754: error: ‘Window’ has not been declared
In file included from /usr/include/KDE/NETRootInfo:1,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/WindowPreview.h:26,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/../../applet/SmoothTasks/CloseIcon.h:27,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/moc_CloseIcon.cpp:10,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/plasma_applet_smooth-tasks_automoc.cpp:12:
/usr/include/KDE/../netwm.h:768: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:781: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:782: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:782: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:790: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:790: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:805: error: ‘Atom’ has not been declared
/usr/include/KDE/../netwm.h:859: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:859: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:869: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:870: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1020: error: ‘Bool’ does not name a type
/usr/include/KDE/../netwm.h:1039: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1137: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1201: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:1206: error: ‘Time’ does not name a type
/usr/include/KDE/../netwm.h:1242: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:1247: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:1341: error: ‘Atom’ has not been declared
/usr/include/KDE/../netwm.h:1341: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1039: error: ‘True’ was not declared in this scope
/usr/include/KDE/../netwm.h:1363: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1363: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1367: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1368: error: ‘Window’ has not been declared
make[2]: *** [applet/CMakeFiles/plasma_applet_smooth-tasks.dir/plasma_applet_smooth-tasks_automoc.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [applet/CMakeFiles/plasma_applet_smooth-tasks.dir/SmoothTasks/Applet.o] Error 1
make[1]: *** [applet/CMakeFiles/plasma_applet_smooth-tasks.dir/all] Error 2
make: *** [all] Error 2
root@petr-sidux:/home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build# checkinstall 

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> smoothtasks
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@petr-sidux ]
1 -  Summary: [ smoothtasks ]
2 -  Name:    [ build ]
3 -  Version: [ 20100516 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ build ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name: 
>> smoothtasks

This package will be built according to these values: 

0 -  Maintainer: [ root@petr-sidux ]
1 -  Summary: [ smoothtasks ]
2 -  Name:    [ smoothtasks ]
3 -  Version: [ 20100516 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ build ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 11
Enter the provided features: 
>> smoothtasks

This package will be built according to these values: 

0 -  Maintainer: [ root@petr-sidux ]
1 -  Summary: [ smoothtasks ]
2 -  Name:    [ smoothtasks ]
3 -  Version: [ 20100516 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ smoothtasks ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
[  0%] Built target translations
[  0%] Built target plasma_applet_smooth-tasks_automoc
[  3%] Building CXX object applet/CMakeFiles/plasma_applet_smooth-tasks.dir/plasma_applet_smooth-tasks_automoc.o
In file included from /usr/include/KDE/NETRootInfo:1,                                                                                                                                                                
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/WindowPreview.h:26,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/../../applet/SmoothTasks/CloseIcon.h:27,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/moc_CloseIcon.cpp:10,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/plasma_applet_smooth-tasks_automoc.cpp:12:
/usr/include/KDE/../netwm.h:33:22: error: X11/Xlib.h: No such file or directory
/usr/include/KDE/../netwm.h:34:23: error: X11/Xutil.h: No such file or directory
/usr/include/KDE/../netwm.h:35:23: error: X11/Xatom.h: No such file or directory
In file included from /usr/include/KDE/NETRootInfo:1,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/WindowPreview.h:26,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/../../applet/SmoothTasks/CloseIcon.h:27,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/moc_CloseIcon.cpp:10,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/plasma_applet_smooth-tasks_automoc.cpp:12:
/usr/include/KDE/../netwm.h:98: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:160: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:167: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:264: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:264: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:283: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:283: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:348: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:348: error: expected ‘;’ before ‘*’ token
/usr/include/KDE/../netwm.h:406: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:425: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:425: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:435: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:435: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:512: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:513: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:513: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:521: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:539: error: ISO C++ forbids declaration of ‘Window’ with no type
/usr/include/KDE/../netwm.h:539: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/KDE/../netwm.h:570: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:587: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:603: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:608: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:614: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:614: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:623: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:623: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:662: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:670: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:718: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:733: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:742: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:742: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:753: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:754: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:754: error: ‘Window’ has not been declared
In file included from /usr/include/KDE/NETRootInfo:1,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/SmoothToolTip.h:36,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/applet/SmoothTasks/WindowPreview.h:26,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/../../applet/SmoothTasks/CloseIcon.h:27,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/moc_CloseIcon.cpp:10,
                 from /home/petr/temp/smooth-tasks-src-wip-2010-02-27/smooth-tasks-src-wip-2010-02-27/build/applet/plasma_applet_smooth-tasks_automoc.cpp:12:
/usr/include/KDE/../netwm.h:768: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:781: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:782: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:782: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:790: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:790: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:805: error: ‘Atom’ has not been declared
/usr/include/KDE/../netwm.h:859: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:859: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:869: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:870: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1020: error: ‘Bool’ does not name a type
/usr/include/KDE/../netwm.h:1039: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1137: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1201: error: ‘Time’ has not been declared
/usr/include/KDE/../netwm.h:1206: error: ‘Time’ does not name a type
/usr/include/KDE/../netwm.h:1242: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:1247: error: ‘Window’ does not name a type
/usr/include/KDE/../netwm.h:1341: error: ‘Atom’ has not been declared
/usr/include/KDE/../netwm.h:1341: error: ‘Bool’ has not been declared
/usr/include/KDE/../netwm.h:1039: error: ‘True’ was not declared in this scope
/usr/include/KDE/../netwm.h:1363: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1363: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1367: error: ‘Window’ has not been declared
/usr/include/KDE/../netwm.h:1368: error: ‘Window’ has not been declared
make[2]: *** [applet/CMakeFiles/plasma_applet_smooth-tasks.dir/plasma_applet_smooth-tasks_automoc.o] Error 1
make[1]: *** [applet/CMakeFiles/plasma_applet_smooth-tasks.dir/all] Error 2
make: *** [all] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I apologize for being on sidux and writing here but this has been the most relevant post I have found.

---

### Post by CraigPaleo on 2010-08-16
It's in the repos now. It's a great space saver on a single panel. I love it.

---

### Post by danielesil on 2011-03-21
> **t.rei said:**
> 
You might need to also get some kde development packages to compile. Please report here if any. Since I already have all of them installed on my system I do not quite know what else needs to be installed. Thanks.
```
apt-get install checkinstall kdelibs5-dev kdebase-workspace-dev
```

kdebase-workspace-dev was also needed for KDevelop4 : Thanks a lot !!!

---

