---
title: "Need help compiling from source.  Zaptel drivers."
date: 2009-05-27
forum: General Help
---

### Post by Buttons840 on 2009-05-27
I have a fresh install of Jaunty.

I attempted to install the latest version of the Zaptel drivers, version 1.4-12 is the current.
[http://downloads.digium.com/pub/asterisk/asterisk-1.4-current.tar.gz](http://downloads.digium.com/pub/asterisk/asterisk-1.4-current.tar.gz)
You can see the output from the make command below.

I then tried to use the source found in the Ubuntu repositories.  I ran apt-get source zaptel and then tried to compile the source, but received a similar error.  I did NOT use the diff file that game with the source, I don't know what it is, or what it's purpose is; it appears to be some sort of patch, probably to fix my problem.  Will someone explain to me how I can properly compile the source in the repos?

Preferable, someone can also help me install the current, version 12 source even though it's not from the Ubuntu repos.

Below is the output from the make:
> [SIZE="1"]
make[1]: Entering directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect'
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for GNU make... make
checking for asprintf... yes
checking for getloadavg... yes
checking for setenv... yes
checking for strcasestr... yes
checking for strndup... yes
checking for strnlen... yes
checking for strsep... yes
checking for strtoq... yes
checking for unsetenv... yes
checking for vasprintf... yes
checking how to run the C preprocessor... gcc -E
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
checking for initscr in -lcurses... yes
checking curses.h usability... yes
checking curses.h presence... yes
checking for curses.h... yes
checking for initscr in -lncurses... yes
checking for curses.h... (cached) yes
checking for pkg-config... pkg-config
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: creating ./config.status
config.status: creating makeopts
config.status: creating autoconfig.h
configure: configuring in mxml
configure: running /bin/bash './configure' --prefix=/usr/local  'CC=' 'LD=' 'AR=' 'CFLAGS=' --cache-file=/dev/null --srcdir=.
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for ar... /usr/bin/ar
checking for cp... /bin/cp
checking for ln... /bin/ln
checking for mkdir... /bin/mkdir
checking for nroff... /usr/bin/nroff
checking for rm... /bin/rm
checking for strdup... yes
checking for vsnprintf... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating mxml.list
config.status: creating mxml.pc
config.status: creating config.h
configure: Menuselect build configuration successfully completed
make[1]: Leaving directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect'
make[1]: Entering directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect'
make[2]: Entering directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect'
gcc -g -c -D_GNU_SOURCE -Wall    -c -o menuselect.o menuselect.c
gcc -g -c -D_GNU_SOURCE -Wall    -c -o strcompat.o strcompat.c
gcc -g -c -D_GNU_SOURCE -Wall    -c -o menuselect_curses.o menuselect_curses.c
make[3]: Entering directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect/mxml'
gcc -O -Wall   -c mxml-attr.c
gcc -O -Wall   -c mxml-entity.c
gcc -O -Wall   -c mxml-file.c
gcc -O -Wall   -c mxml-index.c
gcc -O -Wall   -c mxml-node.c
gcc -O -Wall   -c mxml-search.c
gcc -O -Wall   -c mxml-set.c
gcc -O -Wall   -c mxml-private.c
gcc -O -Wall   -c mxml-string.c
/bin/rm -f libmxml.a
/usr/bin/ar crvs libmxml.a mxml-attr.o mxml-entity.o mxml-file.o mxml-index.o mxml-node.o mxml-search.o mxml-set.o mxml-private.o mxml-string.o
a - mxml-attr.o
a - mxml-entity.o
a - mxml-file.o
a - mxml-index.o
a - mxml-node.o
a - mxml-search.o
a - mxml-set.o
a - mxml-private.o
a - mxml-string.o
ranlib libmxml.a
make[3]: Leaving directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect/mxml'
gcc -o menuselect menuselect.o strcompat.o menuselect_curses.o mxml/libmxml.a mxml/libmxml.a -lncurses 
make[2]: Leaving directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect'
make[1]: Leaving directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1/menuselect'
Generating input for menuselect ...
make[1]: Entering directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1'
make -C /lib/modules/2.6.28-11-generic/build ARCH=x86_64 SUBDIRS=/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel HOTPLUG_FIRMWARE=yes KBUILD_OBJ_M="pciradio.o tor2.o torisa.o wcfxo.o wct1xxp.o wctdm.o wcte11xp.o wcusb.o zaptel.o ztd-eth.o ztd-loc.o ztdummy.o ztdynamic.o zttranscode.o wct4xxp/ wctc4xxp/ xpp/ wctdm24xxp/ wcte12xp/" modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
gcc -o /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/makefw /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/makefw.c
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/makefw /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/pciradio.rbt radfw > /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/radfw.h
Loaded 42096 bytes from file
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/pciradio.o
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/makefw /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/tormenta2.rbt tor2fw > /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/tor2fw.h
Loaded 69900 bytes from file
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/tor2.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/torisa.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/wcfxo.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/wct1xxp.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/wctdm.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/wcte11xp.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/wcusb.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/zaptel-base.o
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/zaptel-base.c: In function ‘zt_ppp_xmit’:
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/zaptel-base.c:1722: warning: comparison of distinct pointer types lacks a cast
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/zaptel-base.c:1785: warning: comparison of distinct pointer types lacks a cast
  LD [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/zaptel.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/ztd-eth.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/ztd-loc.o
  CC [M]  /home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/ztdummy.o
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/ztdummy.c: In function ‘ztdummy_hr_int’:
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/ztdummy.c:202: error: ‘struct hrtimer’ has no member named ‘expires’
make[3]: *** [/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/ztdummy.o] Error 1
make[2]: *** [_module_/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/buttons/Asterisk/src/zaptel-1.4.12.1'
make: *** [all] Error 2[/SIZE]

---

### Post by Keith Hedger on 2009-05-27
If you look at the output from ./configure you will notice the line 'No package 'gtk+-2.0' found' this means it is looking for and can't find the gtk 2 dev files you must install these first by using synaptic or ```
 apt-get install libgtk2.0-dev
```
hope this helps

---

### Post by Buttons840 on 2009-05-27
Thank you.

But that didn't change anything.

---

### Post by Keith Hedger on 2009-05-28
what error are you getting now?

---

### Post by mynard on 2009-06-17
I'm also having this problem, just want to know if someone managed to find a solution to this question yet?

ta

---

### Post by Chronon on 2009-06-17
The .diff is a patch to be applied to the source with the patch program, for example:  ```
patch -p0 < patchfile
```

==
it starts complaining of errors at this point:
```
/home/buttons/Asterisk/src/zaptel-1.4.12.1/kernel/ztdummy.c:202: error: &#8216;struct hrtimer&#8217; has no member named &#8216;expires&#8217;
```

Does the patch alter this line?

---

### Post by deanhiller on 2009-10-11
I am running into the same problem on a dual core 64 bit machine.  The gtk library install helped some and got rid of that warning but I still have these logs when I run now...

root@builddragon:/usr/src/zaptel-1.4.12.1# make
make[1]: Entering directory `/usr/src/zaptel-1.4.12.1'
make -C /lib/modules/2.6.28-15-generic/build ARCH=x86_64 SUBDIRS=/usr/src/zaptel-1.4.12.1/kernel HOTPLUG_FIRMWARE=yes KBUILD_OBJ_M="pciradio.o tor2.o torisa.o wcfxo.o wct1xxp.o wctdm.o wcte11xp.o wcusb.o zaptel.o ztd-eth.o ztd-loc.o ztdummy.o ztdynamic.o zttranscode.o wct4xxp/ wctc4xxp/ xpp/ wctdm24xxp/ wcte12xp/" modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /usr/src/zaptel-1.4.12.1/kernel/ztdummy.o
/usr/src/zaptel-1.4.12.1/kernel/ztdummy.c: In function ‘ztdummy_hr_int’:
/usr/src/zaptel-1.4.12.1/kernel/ztdummy.c:202: error: ‘struct hrtimer’ has no member named ‘expires’
make[3]: *** [/usr/src/zaptel-1.4.12.1/kernel/ztdummy.o] Error 1
make[2]: *** [_module_/usr/src/zaptel-1.4.12.1/kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/zaptel-1.4.12.1'
make: *** [all] Error 2
root@builddragon:/usr/src/zaptel-1.4.12.1# ls ..


anyone solve this?
thanks,
Dean

---

### Post by scenarist on 2009-11-14
Did anyone solve this problem so far ?!?

```
root@nedzad-laptop:/usr/src/zaptel-1.4.12.1# make
make[1]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[2]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[2]: `menuselect' is up to date.
make[2]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[1]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[1]: Entering directory `/usr/src/zaptel-1.4.12.1'
make[2]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[3]: Entering directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[3]: `menuselect' is up to date.
make[3]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make[2]: Leaving directory `/usr/src/zaptel-1.4.12.1/menuselect'
make -C /lib/modules/2.6.28-11-generic/build ARCH=i386 SUBDIRS=/usr/src/zaptel-1.4.12.1/kernel HOTPLUG_FIRMWARE=yes KBUILD_OBJ_M="pciradio.o tor2.o torisa.o wcfxo.o wct1xxp.o wctdm.o wcte11xp.o wcusb.o zaptel.o ztd-eth.o ztd-loc.o ztdummy.o ztdynamic.o zttranscode.o wct4xxp/ wctc4xxp/ xpp/ wctdm24xxp/ wcte12xp/" modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/src/zaptel-1.4.12.1/kernel/ztdummy.o
/usr/src/zaptel-1.4.12.1/kernel/ztdummy.c: In function ‘ztdummy_hr_int’:
/usr/src/zaptel-1.4.12.1/kernel/ztdummy.c:202: error: ‘struct hrtimer’ has no member named ‘expires’
make[3]: *** [/usr/src/zaptel-1.4.12.1/kernel/ztdummy.o] Error 1
make[2]: *** [_module_/usr/src/zaptel-1.4.12.1/kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/zaptel-1.4.12.1'
make: *** [all] Error 2

```

---

### Post by 404wanderer on 2009-11-16
I'm having exactly the same problem.

Anyone any ideas? My VoIP network is off-line because of this one.

---

### Post by uzi09 on 2009-12-03
Hi guys,

Here's a solution for those that want to take the easy way out ;)

[http://jan.saell.org/blog/archives/49](http://jan.saell.org/blog/archives/49)

Here are the relevant tid-bits:
> 
The I read about the module-asistance comand in ubuntu. This is actually to start with a debian comand. Remember that ubuntu and kybntu comes from the debian system and a lot of the tings in the system id debian based. Module assistant is a script that helps download and build kernel modules from source. It has a lot of different commands but if you whant to make it all you can use the auto-install command that will just do all the job. There is also a short name for module assistant &#8211; m-a that you can use if you dont what to type that much, and even a short cut for auto-install &#8211; use a-i instead.

If you dont have module assistant installed you do that with:

```
sudo apt-get install module-assistant
```

In my case it was already installed, but if you dont have it installed, install it and ofcourse install all the dependencies also. So I went ahead and installed the zaptel vith this:

```
sudo m-a a-i zaptel
```

This did the job and installed the zaptel driver for me &#8211; and now i have ztdummy running and I can run the meetme application.

If you do need to install the package again you find it under /usr/src, and you can use m-a install to install it also.



However, I've been meaning to learn to do everything from scratch and have been attempting to compile everything.

I'd love to know how to resolve the above issue as well since I'm getting the exact same error the OP posted.

I thought I found someone post a patch somewhere, but I'll have to find it again and edit this post. I was hoping I could find an easier solution :D


EDIT:
I read about this module-assistant in a couple of different places and it seemed promising. However, when I tried it, it failed with the same error as above :@


Edit #2:
Upon more Googling, I've found that people seem to be downloading the latest version from SVN:
[https://www.saruman.biz/wiki/index.php/Installing_and_configuring_Zaptel#Digium_Zaptel_driver_for_your_custom_kernel](https://www.saruman.biz/wiki/index.php/Installing_and_configuring_Zaptel#Digium_Zaptel_driver_for_your_custom_kernel)
Now I just need to figure out how to use SVN :$

Edit #3: Eeek! It worked!! The instructions are right in that link!

---

