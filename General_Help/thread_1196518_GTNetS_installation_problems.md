---
title: "GTNetS installation problems"
date: 2009-06-25
forum: General Help
---

### Post by tendy on 2009-06-25
Hello, 

I am using ubuntu jaunty, and trying to install GTNetS, and here is the installation manual:

> [COLOR=#000099]_[SIZE=3]Installation Steps[/SIZE]_[/COLOR]
         1. [U]Create Dependency List
        [/U]   
            In the _GTNetS_ (main folder)
            $ make depend
        
        **Note: “make depend” may result in an error in the EXAMPLES directory when using the sun studio compilers. This can be safely ignored**
        [U]2. [U]Create libraries with debugging symbols
        [/U]    
            $ make debug
        
        3. [U]Create libraries with optimal code
        [/U]    
            $ make opt
        
         **Note: make sure you have done make depend atleast once after checking out the sources**[/U][U]

First step is a success, but when I do the make debug part, here is the message:

[/U]> [U]root@ubuntu:/home/tendy/Desktop/GTNetS-Oct-10-08# make debug
make -C SRC debug
make[1]: Entering directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
Compiling debug aiff
g++ -g -fPIC -DLinux -Wall -DHAVE_QT -I/usr/include/qt3 -I/home/tendy/Desktop/GTNetS-Oct-10-08/SRC -o /home/tendy/Desktop/GTNetS-Oct-10-08/OBJDBG/aiff.o -c aiff.cc
aiff.cc: In static member function ‘static double AIFF::ConvertFromExtended(char*)’:
aiff.cc:482: error: ‘memcpy’ was not declared in this scope
aiff.cc: In static member function ‘static void AIFF::ConvertToExtended(double, char*)’:
aiff.cc:526: error: ‘memcpy’ was not declared in this scope
aiff.cc:528: error: ‘memset’ was not declared in this scope
make[1]: *** [/home/tendy/Desktop/GTNetS-Oct-10-08/OBJDBG/aiff.o] Error 1
make[1]: Leaving directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
make: *** [SRC] Error 2
[/U]When I do the make opt part, here is the error message:

> make -C SRC opt
make[1]: Entering directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
Compiling opt aiff
g++ -O2 -fPIC -DLinux -Wall -DHAVE_QT -I/usr/include/qt3 -I/home/tendy/Desktop/GTNetS-Oct-10-08/SRC -o /home/tendy/Desktop/GTNetS-Oct-10-08/OBJOPT/aiff.o -c aiff.cc
aiff.cc: In static member function ‘static double AIFF::ConvertFromExtended(char*)’:
aiff.cc:482: error: ‘memcpy’ was not declared in this scope
aiff.cc: In static member function ‘static void AIFF::ConvertToExtended(double, char*)’:
aiff.cc:526: error: ‘memcpy’ was not declared in this scope
aiff.cc:528: error: ‘memset’ was not declared in this scope
make[1]: *** [/home/tendy/Desktop/GTNetS-Oct-10-08/OBJOPT/aiff.o] Error 1
make[1]: Leaving directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
make: *** [SRC] Error 2:confused::confused:

[B]Can someone help me?? Thanks a lot.. :D
[/B]

---

