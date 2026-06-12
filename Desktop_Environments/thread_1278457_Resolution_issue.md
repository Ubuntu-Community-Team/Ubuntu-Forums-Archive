---
title: "Resolution issue"
date: 2009-09-29
forum: Desktop Environments
---

### Post by S1nbad on 2009-09-29
Hi,
 
First off I am a complete newbie. I have been a Windows user for years and am only now trying my hand at Linux properly.
 
I have an Acer D150 netbook with Windows XP running. Installed Sun xVM Virtualbox, under which I have created a Ubuntu 9.04 desktop. The install went smothly and I am starting to get to grips with some of the core apps. However I have a very annoying problem. The resolution is stuck at 800x600 but the native resolution of the netbook is 1024x600. I have searched various forums for an answer which all suggest editing the xorg file. I have done this with various settings but never seem to be able to get the one I need. The nearest I have acheive is 1024x768, which causes it's own problems.
 
Can anyone out there offer any suggestions for the correct entry to enter into the xorg file, or any other possible solution.
 
Thanks in advance
 
S1nbad

---

### Post by linux4life88 on 2009-09-29
What graphics card do you have?

---

### Post by S1nbad on 2009-09-30
Under Display adaptors, there are two identical entries as below
 
Mobile Intel(R) 945 Express Chipset Family

---

### Post by Claus7 on 2009-09-30
Hello,

searching a little bit I found this:
[http://ubuntuforums.org/showthread.php?t=545821](http://ubuntuforums.org/showthread.php?t=545821)

Doing exactly the same in a 8.04 box, I got the package in question. So first of all I would suggest you try and follow this thread.

Regards!

---

### Post by S1nbad on 2009-09-30
Hi Claus7

Thanks for the suggestion. I followed the advice in the linked stream but could not find any entries when searching fro 945. I did find the two entries below though that mention i945 in their description. I set both of these to re-install. But still the monitor is 'Unknown' and the resolution is stuck at 800x600.

xserver-corg-video-intel
xserver-xorg-video-intel-dbg

Any other suggestions would be gratefully received.

Regards

---

### Post by Claus7 on 2009-10-01
Hello,

first of, we have to identify whether ubuntu has the graphics driver of your card. In order to verify this, you will have to run the command:

```
lspci
```

this will show all your pci devices in your computer. Now, in case you do not see anything (it would be nice to post the output of the command here), then you have to find the drivers and install them yourself. I think, with a quick glance that you can download them from here:
[http://www.intel.com/support/chipsets/sb/CS-020683.htm#b](http://www.intel.com/support/chipsets/sb/CS-020683.htm#b)

Now, in case you do have the drivers, then what you have to do, as others have told you is to edit manually, your xorg.conf file.
This is not easy, and not straightforward. From what you say, you have to do a lot of tweaking, yet if you do so, it will work. 

So, in order to recapitulate: 1)find if ubu has the driver and post the output and 2)edit xorg.

For xorg to work basically what you have to do is to give the type of the graphics card you have (write all the necessary information) and give the resolution of the graphics card. It would be nice to see an example of a xorg file. This would be a nice place to start:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Regards!

---

### Post by S1nbad on 2009-10-01
Hi Claus7,

Below is the output from lspci. To my untrained eye it looks like I do not have the driver installed. I went to the Intel page linked and was unable to download a driver. But was directed to [http://xorg.freedesktop.org/archive/individual/driver/](http://xorg.freedesktop.org/archive/individual/driver/) where I have downloaded [xf86-video-intel-2.9.0.tar.gz]("http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.9.0.tar.gz"). Now I am stumped. I have no idea how I would install this. I tried through Synaptic Package Manager, but with no luck.

Thanks


00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0b.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller

---

### Post by realzippy on 2009-10-01
forget this one.

---

### Post by realzippy on 2009-10-01
I just see that you are under windows virtualbox.You have to install the 
"Linux Guest Additions" and run "VBoxLinuxAdditions-x86.run" first:

**sudo sh VBoxLinuxAdditions-x86.run**

---

### Post by S1nbad on 2009-10-01
Hi Realzippy

I have run "VBoxLinuxAdditions-x86.run" and rebooted. I then tried the driver install. The ./configure runs ok. But when I try to do make or make && make install I get the following returns.

make: *** No targets specified and no makefile found. Stop.

Below is a list of the contents of the extracted zip.

aclocal.m4    config.log    depcomp     ltmain.sh    missing        src
AUTHORS       config.sub    doltcompile  m4          NEWS        uxa
compile       configure     doltlibtool  Makefile.am  README
config.guess  configure.ac  install.php  Makefile.in  shave.in
config.h.in   COPYING        install-sh     man          shave-libtool.in

Thanks


Just in case here is the return of running ./configure

phil@linux2:~/Desktop/xf86-video-intel-2.9.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for bash... /bin/bash
checking if dolt supports this host... yes, replacing libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GEN4ASM... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mprotect... yes
checking if XINERAMA is defined... no
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XF86DRI is defined... no
checking if DPMSExtension is defined... no
checking for XORG... configure: error: Package requirements (xorg-server >= 1.6 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by realzippy on 2009-10-02
*00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter*

...is your virtual graphics adapter.

AFAIK you cannot install the driver you selected for it.After you enabled
the LinuxGuestAdditions in VirtualBox in your host system,you should be able
to enlarge the Guest Ubuntu Window simply by dragging it,if you had run:

[B]mount /dev/cdrom
cd /media/cdrom
sudo sh ./VBoxLinuxAdditions.run[/B]

in a Ubuntu terminal.....

---

### Post by S1nbad on 2009-10-02
Cheers Realzippy.

As you said, once the VBox Additions were installed I had the extra options within the Sun Virtual environment to adjust the screen. So easy when you know how...

Many thanks for all your assistance and patience with such a newbie

Cheers

:)

---

