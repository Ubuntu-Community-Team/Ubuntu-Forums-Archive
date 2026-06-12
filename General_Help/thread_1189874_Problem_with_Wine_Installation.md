---
title: "Problem with Wine Installation"
date: 2009-06-17
forum: General Help
---

### Post by StOlEnDeStInY on 2009-06-17
While trying to install Wine through .tar.gz file available from winehq.com on my old office computer running Intrepid, I had a problem with the X development files or something.. Below is the complete installation sequence shown:

```
aditya@ubuntu:~/Desktop/wine-1.0.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for cpp... cpp
checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for flex... flex
checking for bison... bison
checking for gas... no
checking for as... as
checking for ld... ld
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for windres... no
checking whether ln -s works... yes
checking whether ln works... yes
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ldconfig... /sbin/ldconfig
checking for a BSD-compatible install... /usr/bin/install -c
checking for lclint... no
checking for lint... no
checking for fontforge... no
checking for pkg-config... pkg-config
checking for rsvg... no
checking for icotool... no
checking for prelink... false
checking for i386_set_ldt in -li386... no
checking for _oss_ioctl in -lossaudio... no
checking for pthread_create in -lpthread... yes
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
checking AudioUnit/AudioUnit.h usability... no
checking AudioUnit/AudioUnit.h presence... no
checking for AudioUnit/AudioUnit.h... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking DiskArbitration/DiskArbitration.h usability... no
checking DiskArbitration/DiskArbitration.h presence... no
checking for DiskArbitration/DiskArbitration.h... no
checking IOKit/IOKitLib.h usability... no
checking IOKit/IOKitLib.h presence... no
checking for IOKit/IOKitLib.h... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking arpa/nameser.h usability... yes
checking arpa/nameser.h presence... yes
checking for arpa/nameser.h... yes
checking asm/types.h usability... yes
checking asm/types.h presence... yes
checking for asm/types.h... yes
checking capi20.h usability... no
checking capi20.h presence... no
checking for capi20.h... no
checking cups/cups.h usability... no
checking cups/cups.h presence... no
checking for cups/cups.h... no
checking curses.h usability... no
checking curses.h presence... no
checking for curses.h... no
checking direct.h usability... no
checking direct.h presence... no
checking for direct.h... no
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking elf.h usability... yes
checking elf.h presence... yes
checking for elf.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking fontconfig/fontconfig.h usability... no
checking fontconfig/fontconfig.h presence... no
checking for fontconfig/fontconfig.h... no
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking jack/jack.h usability... no
checking jack/jack.h presence... no
checking for jack/jack.h... no
checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no
checking lber.h usability... no
checking lber.h presence... no
checking for lber.h... no
checking lcms.h usability... no
checking lcms.h presence... no
checking for lcms.h... no
checking lcms/lcms.h usability... no
checking lcms/lcms.h presence... no
checking for lcms/lcms.h... no
checking ldap.h usability... no
checking ldap.h presence... no
checking for ldap.h... no
checking libaudioio.h usability... no
checking libaudioio.h presence... no
checking for libaudioio.h... no
checking link.h usability... yes
checking link.h presence... yes
checking for link.h... yes
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking linux/compiler.h usability... no
checking linux/compiler.h presence... no
checking for linux/compiler.h... no
checking linux/hdreg.h usability... yes
checking linux/hdreg.h presence... yes
checking for linux/hdreg.h... yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking linux/ioctl.h usability... yes
checking linux/ioctl.h presence... yes
checking for linux/ioctl.h... yes
checking linux/joystick.h usability... yes
checking linux/joystick.h presence... yes
checking for linux/joystick.h... yes
checking linux/major.h usability... yes
checking linux/major.h presence... yes
checking for linux/major.h... yes
checking linux/param.h usability... yes
checking linux/param.h presence... yes
checking for linux/param.h... yes
checking linux/serial.h usability... yes
checking linux/serial.h presence... yes
checking for linux/serial.h... yes
checking linux/ucdrom.h usability... no
checking linux/ucdrom.h presence... no
checking for linux/ucdrom.h... no
checking mach/mach.h usability... no
checking mach/mach.h presence... no
checking for mach/mach.h... no
checking mach/machine.h usability... no
checking mach/machine.h presence... no
checking for mach/machine.h... no
checking machine/cpu.h usability... no
checking machine/cpu.h presence... no
checking for machine/cpu.h... no
checking machine/limits.h usability... no
checking machine/limits.h presence... no
checking for machine/limits.h... no
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking netinet/tcp_fsm.h usability... no
checking netinet/tcp_fsm.h presence... no
checking for netinet/tcp_fsm.h... no
checking openssl/err.h usability... no
checking openssl/err.h presence... no
checking for openssl/err.h... no
checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
checking png.h usability... no
checking png.h presence... no
checking for png.h... no
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking process.h usability... no
checking process.h presence... no
checking for process.h... no
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking scsi/scsi_ioctl.h usability... yes
checking scsi/scsi_ioctl.h presence... yes
checking for scsi/scsi_ioctl.h... yes
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking soundcard.h usability... no
checking soundcard.h presence... no
checking for soundcard.h... no
checking for stdint.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/asoundlib.h usability... no
checking sys/asoundlib.h presence... no
checking for sys/asoundlib.h... no
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking sys/elf32.h usability... no
checking sys/elf32.h presence... no
checking for sys/elf32.h... no
checking sys/epoll.h usability... yes
checking sys/epoll.h presence... yes
checking for sys/epoll.h... yes
checking sys/errno.h usability... yes
checking sys/errno.h presence... yes
checking for sys/errno.h... yes
checking sys/event.h usability... no
checking sys/event.h presence... no
checking for sys/event.h... no
checking sys/exec_elf.h usability... no
checking sys/exec_elf.h presence... no
checking for sys/exec_elf.h... no
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/limits.h usability... no
checking sys/limits.h presence... no
checking for sys/limits.h... no
checking sys/link.h usability... no
checking sys/link.h presence... no
checking for sys/link.h... no
checking sys/lwp.h usability... no
checking sys/lwp.h presence... no
checking for sys/lwp.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/modem.h usability... no
checking sys/modem.h presence... no
checking for sys/modem.h... no
checking sys/msg.h usability... yes
checking sys/msg.h presence... yes
checking for sys/msg.h... yes
checking sys/mtio.h usability... yes
checking sys/mtio.h presence... yes
checking for sys/mtio.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/prctl.h usability... yes
checking sys/prctl.h presence... yes
checking for sys/prctl.h... yes
checking sys/ptrace.h usability... yes
checking sys/ptrace.h presence... yes
checking for sys/ptrace.h... yes
checking sys/reg.h usability... yes
checking sys/reg.h presence... yes
checking for sys/reg.h... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/scsiio.h usability... no
checking sys/scsiio.h presence... no
checking for sys/scsiio.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking sys/signal.h usability... yes
checking sys/signal.h presence... yes
checking for sys/signal.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/socketvar.h usability... yes
checking sys/socketvar.h presence... yes
checking for sys/socketvar.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/strtio.h usability... no
checking sys/strtio.h presence... no
checking for sys/strtio.h... no
checking sys/syscall.h usability... yes
checking sys/syscall.h presence... yes
checking for sys/syscall.h... yes
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking sys/vm86.h usability... yes
checking sys/vm86.h presence... yes
checking for sys/vm86.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking syscall.h usability... yes
checking syscall.h presence... yes
checking for syscall.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking valgrind/memcheck.h usability... no
checking valgrind/memcheck.h presence... no
checking for valgrind/memcheck.h... no
checking whether stat file-mode macros are broken... no
checking for sys/mount.h... yes
checking for sys/statfs.h... yes
checking for sys/user.h... yes
checking for sys/vfs.h... yes
checking for netinet/in_pcb.h... no
checking for netinet/ip_var.h... no
checking for net/if.h... yes
checking for net/if_arp.h... yes
checking for net/if_dl.h... no
checking for net/if_types.h... no
checking for net/route.h... yes
checking for netipx/ipx.h... yes
checking for netinet/tcp_var.h... no
checking for linux/ipx.h... no
checking for resolv.h... yes
checking for ucontext.h... yes
checking for sys/thr.h... no
checking for pthread_np.h... no
checking for linux/videodev.h... yes
checking for linux/capi.h... yes
checking for ldd... /usr/bin/ldd
checking whether we can build a GNU style ELF dll... yes
checking whether the compiler supports -fPIC -shared -Wl,-soname,confest.so.1... yes
checking whether the compiler supports -fPIC -shared -Wl,-Bsymbolic,-z,defs... yes
checking whether the compiler supports -fPIC -shared -Wl,-Bsymbolic,-init,__wine_spec_init,-fini,__wine_spec_fini... yes
checking whether the compiler supports -fPIC -shared -Wl,--version-script=conftest.map... yes
checking whether the compiler supports -fPIC -Wl,--export-dynamic... yes
checking whether the compiler supports -fPIC -Wl,--rpath,$ORIGIN/../lib... yes
checking whether the compiler supports -Wl,--enable-new-dtags... yes
checking whether the compiler supports -Wl,--section-start,.interp=0x7bf00400... yes
checking for i586-mingw32msvc-gcc... no
checking for i386-mingw32msvc-gcc... no
checking for i686-mingw32-gcc... no
checking for i586-mingw32-gcc... no
checking for i386-mingw32-gcc... no
checking for mingw32-gcc... no
checking for mingw-gcc... no
checking for i586-mingw32msvc-dlltool... no
checking for i386-mingw32msvc-dlltool... no
checking for i686-mingw32-dlltool... no
checking for i586-mingw32-dlltool... no
checking for i386-mingw32-dlltool... no
checking for mingw32-dlltool... no
checking for mingw-dlltool... no
checking for i586-mingw32msvc-windres... no
checking for i386-mingw32msvc-windres... no
checking for i686-mingw32-windres... no
checking for i586-mingw32-windres... no
checking for i386-mingw32-windres... no
checking for mingw32-windres... no
checking for mingw-windres... no
checking for i586-mingw32msvc-ar... no
checking for i386-mingw32msvc-ar... no
checking for i686-mingw32-ar... no
checking for i586-mingw32-ar... no
checking for i386-mingw32-ar... no
checking for mingw32-ar... no
checking for mingw-ar... no
configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.

```

Xorg and other Xserver files are installed in synaptic.. Any ideas anyone?

---

### Post by m4tic on 2009-06-17
get a debi installer

---

### Post by StOlEnDeStInY on 2009-06-19
What if I am obstinate and say I want to do it using source file only?Any ideas then?

---

### Post by dmizer on 2009-06-19
Try this: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Really, you should stick to debian packages if at all humanly possible, because you're likely to run into much and frequent breakage after installing from source. This should be an absolute last resort for when there is no other option at all.

Here is a PPA with current Wine source packaged for ubuntu: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by t0p on 2009-06-19
> **StOlEnDeStInY said:**
> What if I am obstinate and say I want to do it using source file only?Any ideas then?

The error message you got when running ./configure said that you need to get the *development* packages of Xlib/Xfree86.  So I suggest you install the development packages of Xlib/Xfree86.  Then run ./configure again, and see what other dependencies you need.  That's what running ./configure is all about: it tells you what dependencies you need to build the software you want.

As dmizer suggested, go look at the [CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo").  If you want to compile software yourself, it'll help if you actually understand what you're doing.  But I would advise anyone to install .debs if they are available.

---

