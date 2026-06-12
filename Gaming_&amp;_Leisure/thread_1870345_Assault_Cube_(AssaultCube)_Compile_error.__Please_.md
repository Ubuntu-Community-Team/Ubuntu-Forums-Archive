---
title: "Assault Cube (AssaultCube) Compile error.  Please help me with this."
date: 2011-10-27
forum: Gaming &amp; Leisure
---

### Post by iamanidiot123 on 2011-10-27
Hello to you all,
I am trying to compile AssaultCube from source.  
However compiling it gives me this error:
```
daniel@daniel-desktop:~/cubesource/source/src$ make
make -C ../enet all
make[1]: Entering directory `/home/daniel/cubesource/source/enet'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/daniel/cubesource/source/enet'
g++ -O3 -fomit-frame-pointer -Wall -fsigned-char -rdynamic -I. -Ibot -I../enet/include -I/usr/include `sdl-config --cflags` -idirafter ../include   -c -o client.o client.cpp
client.cpp:45:1: error: reference to ‘string’ is ambiguous
tools.h:106:14: error: candidates are: typedef char string [260]
/usr/include/c++/4.6/bits/stringfwd.h:65:33: error:                 typedef struct std::basic_string<char> std::string
client.cpp:45:1: error: ‘string’ does not name a type
client.cpp: In function ‘void abortconnect()’:
client.cpp:52:5: error: ‘clientpassword’ was not declared in this scope
client.cpp: In function ‘void connectserv_(const char*, const char*, const char*, int)’:
client.cpp:79:16: error: ‘clientpassword’ was not declared in this scope
client.cpp: In function ‘void addmsg(int, const char*, ...)’:
client.cpp:346:5: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:347:5: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:348:16: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp: At global scope:
client.cpp:365:8: error: reference to ‘string’ is ambiguous
tools.h:106:14: error: candidates are: typedef char string [260]
/usr/include/c++/4.6/bits/stringfwd.h:65:33: error:                 typedef struct std::basic_string<char> std::string
client.cpp:365:8: error: ‘string’ does not name a type
client.cpp: In function ‘void c2sinfo(playerent*)’:
client.cpp:457:32: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:470:19: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:472:23: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:472:39: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:474:16: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:475:20: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp:478:9: error: reference to ‘messages’ is ambiguous
client.cpp:307:15: error: candidates are: vector<unsigned char> messages
/usr/include/c++/4.6/bits/localefwd.h:185:11: error:                 template<class _CharT> struct std::messages
client.cpp: In function ‘void sendintro()’:
client.cpp:512:42: error: ‘clientpassword’ was not declared in this scope
client.cpp: At global scope:
client.cpp:722:1: error: reference to ‘string’ is ambiguous
tools.h:106:14: error: candidates are: typedef char string [260]
/usr/include/c++/4.6/bits/stringfwd.h:65:33: error:                 typedef struct std::basic_string<char> std::string
client.cpp:722:1: error: ‘string’ does not name a type
client.cpp: In function ‘void getdemo(char*, char*)’:
client.cpp:726:23: error: ‘demosubpath’ was not declared in this scope
client.cpp:727:21: error: ‘demosubpath’ was not declared in this scope
client.cpp: At global scope:
client.cpp:274:1: warning: ‘__dummy_echo’ defined but not used [-Wunused-variable]
client.cpp:275:1: warning: ‘__dummy_toserver’ defined but not used [-Wunused-variable]
client.cpp:276:1: warning: ‘__dummy_toserverme’ defined but not used [-Wunused-variable]
client.cpp:277:1: warning: ‘__dummy_connectserv’ defined but not used [-Wunused-variable]
client.cpp:278:1: warning: ‘__dummy_connectadmin’ defined but not used [-Wunused-variable]
client.cpp:279:1: warning: ‘__dummy_lanconnect’ defined but not used [-Wunused-variable]
client.cpp:280:1: warning: ‘__dummy_modconnectserv’ defined but not used [-Wunused-variable]
client.cpp:281:1: warning: ‘__dummy_modconnectadmin’ defined but not used [-Wunused-variable]
client.cpp:282:1: warning: ‘__dummy_modlanconnect’ defined but not used [-Wunused-variable]
client.cpp:283:1: warning: ‘__dummy_trydisconnect’ defined but not used [-Wunused-variable]
client.cpp:284:1: warning: ‘__dummy_whereami’ defined but not used [-Wunused-variable]
client.cpp:285:1: warning: ‘__dummy_go_to’ defined but not used [-Wunused-variable]
client.cpp:292:1: warning: ‘__dummy_current_version’ defined but not used [-Wunused-variable]
client.cpp:643:1: warning: ‘__dummy_addauthkey’ defined but not used [-Wunused-variable]
client.cpp:644:1: warning: ‘__dummy___dummy_hasauthkey’ defined but not used [-Wunused-variable]
client.cpp:645:1: warning: ‘__dummy_genauthkey’ defined but not used [-Wunused-variable]
client.cpp:646:1: warning: ‘__dummy_saveauthkeys’ defined but not used [-Wunused-variable]
client.cpp:647:1: warning: ‘__dummy___dummy_auth’ defined but not used [-Wunused-variable]
client.cpp:739:1: warning: ‘__dummy_sendmap’ defined but not used [-Wunused-variable]
client.cpp:740:1: warning: ‘__dummy_getmap’ defined but not used [-Wunused-variable]
client.cpp:741:1: warning: ‘__dummy_deleteservermap’ defined but not used [-Wunused-variable]
client.cpp:742:1: warning: ‘__dummy_resetsecuremaps’ defined but not used [-Wunused-variable]
client.cpp:743:1: warning: ‘__dummy_securemap’ defined but not used [-Wunused-variable]
client.cpp:744:1: warning: ‘__dummy_getdemo’ defined but not used [-Wunused-variable]
client.cpp:745:1: warning: ‘__dummy_listdemos’ defined but not used [-Wunused-variable]
make: *** [client.o] Error 1
daniel@daniel-desktop:~/cubesource/source/src$ 

```

Something to do with client.cpp. 

Thanks in advance for a fast reply!

---

### Post by thatguruguy on 2011-10-27
> **iamanidiot123 said:**
> 
I am trying to compile AssaultCube from source.  


Why?

---

### Post by iamanidiot123 on 2011-10-27
@thatguruguy:
Becuase I want to.  I came here for help, not becuase I want to be questioned.  Thank you.

---

### Post by Perfect Storm on 2011-10-27
I think he asked because you rarely need to compile anything nowadays: Check Playdeb - [http://www.playdeb.net/software/Assault%20Cube](http://www.playdeb.net/software/Assault%20Cube)

---

### Post by iamanidiot123 on 2011-10-27
> **Artificial Intelligence said:**
> I think he asked because you rarely need to compile anything nowadays: Check Playdeb - [http://www.playdeb.net/software/Assault%20Cube](http://www.playdeb.net/software/Assault%20Cube)

That's nice, but I would still like to have my question answered so:
1) I can avoid this problem in the future
2) When I get stuck I do not need to make another thread on this forum
3) In case a few sites are down or my internet connection is problematic, I can still compile a few things instead of waiting for something to be fixed.  That website was very helpful though

---

### Post by thatguruguy on 2011-10-27
You can also get Assault Cube by simply unpacking the .tar.bz2 file available [here]("http://assault.cubers.net/download.html") and extracting it to a directory in your home directory, and then just clicking on "assaultcube.sh" file you'll find in the directory.  It should run without any problems.

If you insist upon compiling it, make sure you have all the pre-requisites:

```
sudo apt-get install libsdl-ttf2.0-0 libsdl-ttf2.0-dev  libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev  libsdl1.2-dev libsdl1.2debian-all xorg-dev libtool freeglut3  freeglut3-dev libglew1.5 libglew1.5-dev libglu1-mesa libglu1-mesa-dev  libgl1-mesa-glx libgl1-mesa-dev libsdl-sound1.2-dev
```

... should get you just about everything you need.

---

### Post by iamanidiot123 on 2011-10-31
> **thatguruguy said:**
> You can also get Assault Cube by simply unpacking the .tar.bz2 file available [here]("http://assault.cubers.net/download.html") and extracting it to a directory in your home directory, and then just clicking on "assaultcube.sh" file you'll find in the directory.  It should run without any problems.

If you insist upon compiling it, make sure you have all the pre-requisites:

```
sudo apt-get install libsdl-ttf2.0-0 libsdl-ttf2.0-dev  libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev  libsdl1.2-dev libsdl1.2debian-all xorg-dev libtool freeglut3  freeglut3-dev libglew1.5 libglew1.5-dev libglu1-mesa libglu1-mesa-dev  libgl1-mesa-glx libgl1-mesa-dev libsdl-sound1.2-dev
```

... should get you just about everything you need.
Okay... When I tried that it says all the pakcages already are installed... But anyway, thanks.

---

### Post by thatguruguy on 2011-10-31
In that case, you may want to re-download the source files. I've been able to get them to build on my computer without issue.  The errors you're getting suggests that there's something wrong with the source files you're using.

---

