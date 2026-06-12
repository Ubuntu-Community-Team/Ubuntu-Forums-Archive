---
title: "Freetype fonts problem with Wine"
date: 2009-06-01
forum: General Help
---

### Post by afrodeity on 2009-06-01
This is a problem that is plaguing me. Can't seem to find a solution. Is there anybody who knows how to install freetype fonts? I have the freetype-2.3.9.tar.gz but not sure how to proceed?

This is the problem which isn't solved by installing msstcorefonts.

```
afrodeity@afrodeity-desktop:~/Desktop$ winecfg
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
wine: Unhandled page fault on write access to 0x00000004 at address 0x7bc452d6 (thread 0015), starting debugger...
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:ole:apartment_createwindowifneeded CreateWindow failed with error 127
afrodeity@afrodeity-desktop:~/Desktop$ 

```

---

### Post by afrodeity on 2009-06-03
I downloaded the Freetype fonts and did a make and makefile install, but Wine not finding them. How do I get Wine to find the fonts?

---

### Post by Teutorix on 2009-06-03
I think there are some fixes for this, but you need to build wine from source after editing it. Something i have never managed to do.

---

### Post by afrodeity on 2009-06-03
```
afrodeity@afrodeity-desktop:~$ dpkg -l "*freetype*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  freetype       <none>         (no description available)
un  freetype0      <none>         (no description available)
un  freetype0-dev  <none>         (no description available)
un  freetype1      <none>         (no description available)
un  freetype1-dev  <none>         (no description available)
ii  libfreetype6   2.3.5-1ubuntu4 FreeType 2 font engine, shared library files
ii  libfreetype6-d 2.3.5-1ubuntu4 FreeType 2 font engine, development files
afrodeity@afrodeity-desktop:~$ 

```

---

### Post by afrodeity on 2009-06-03
Okay, I've managed to sort out the software sources problem and am building wine using this [http://wiki.winehq.org/APTRepository](http://wiki.winehq.org/APTRepository)

but just some minor hassles with where to put freetype source files.

ran

dpkg -i wine*.deb

```

checking for freetype-config... freetype-config
checking for -lfreetype... not found
configure: error: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.
Use the --without-freetype option if you really want this.
make: *** [config.status] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
Build command 'cd wine-1.0.0 && dpkg-buildpackage -b -uc' failed.
E: Child process failed
afrodeity@afrodeity-desktop:~/wine-1.0.0$ 

```

I extracted the Freetype to the Wine directory and its now in :~/wine-1.0.0/Freetype which isn't picked up with the dpkg command. Wondering what to do?

---

### Post by afrodeity on 2009-06-03
```
afrodeity@afrodeity-desktop:~/wine-1.0.0$ freetype-config
Usage: freetype-config [OPTION]...
Get FreeType compilation and linking information.

Options:
  --prefix               display `--prefix' value used for building the
                         FreeType library
  --prefix=PREFIX        override `--prefix' value with PREFIX
  --exec-prefix          display `--exec-prefix' value used for building
                         the FreeType library
  --exec-prefix=EPREFIX  override `--exec-prefix' value with EPREFIX
  --version              display libtool version of the FreeType library
  --ftversion            display FreeType version number
  --libs                 display flags for linking with the FreeType library
  --libtool              display library name for linking with libtool
  --cflags               display flags for compiling with the FreeType
                         library
afrodeity@afrodeity-desktop:~/wine-1.0.0$ freetype-config --libs
-L/usr/local/lib -lfreetype -lz

```

---

### Post by perat on 2012-03-24
What is next?

$ freetype-config --libs
-L/usr/local/lib -lfreetype -lz

taras@taras-WS-1864:~/wine32$ ../wine-git/configure --with-wine64=../wine64 LDFLAGS=-L/usr/local/lib LIBS=-lfreetype CFLAGS=-lz
checking whether gcc -m32 works... no
configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries.

---

