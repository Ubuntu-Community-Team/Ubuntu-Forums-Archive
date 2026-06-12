---
title: "How to install KDE 4 in Kubuntu 7.04"
date: 2007-06-24
forum: Desktop Environments
---

### Post by solarwind on 2007-06-24
How do I install KDE 4 in Kubuntu 7.04?

---

### Post by atlfalcons866 on 2007-06-24
[http://techbase.kde.org/Getting_Started/Build/KDE4#Kubuntu](http://techbase.kde.org/Getting_Started/Build/KDE4#Kubuntu)

Be aware that kde4 is in alpha testing and could break your system

---

### Post by solarwind on 2007-06-24
> **atlfalcons866 said:**
> [http://techbase.kde.org/Getting_Started/Build/KDE4#Kubuntu](http://techbase.kde.org/Getting_Started/Build/KDE4#Kubuntu)

Be aware that kde4 is in alpha testing and could break your system

Thanks.

---

### Post by solarwind on 2007-06-25
MMM, lot of source building here, are there any pre-compiled packages that I could use?

---

### Post by iamhugeinjapan on 2007-06-25
[http://kubuntu.org/announcements/kde4-alpha1.php](http://kubuntu.org/announcements/kde4-alpha1.php)

Kubuntu.org provides a repository for the Alpha 1 release.There's still a tiny bit of manual tweaking to be done though.

---

### Post by solarwind on 2007-06-26
> **iamhugeinjapan said:**
> [http://kubuntu.org/announcements/kde4-alpha1.php](http://kubuntu.org/announcements/kde4-alpha1.php)

Kubuntu.org provides a repository for the Alpha 1 release.There's still a tiny bit of manual tweaking to be done though.

I tried that, but I get errors when I try to launch a session.

---

### Post by rcmn on 2007-06-26
i don't mean to be rude but you have the pretension  of trying an alpha release of an application that require tweaking/manual reading and you can't even find the first step...Google: kde4 kubuntu....i don't think you should keep asking questions before more reading or more precise/detailed post.
good luck.

---

### Post by solarwind on 2007-06-26
> **rcmn said:**
> i don't mean to be rude but you have the pretension  of trying an alpha release of an application that require tweaking/manual reading and you can't even find the first step...Google: kde4 kubuntu....i don't think you should keep asking questions before more reading or more precise/detailed post.
good luck.

Here's a question for ya bro, did YOU get KDE4 working?

---

### Post by rcmn on 2007-06-26
hum... no i don't have time for kde4 alpha or any other dev thing . it's partly why I'm using ubuntu , to be a user with almost clean hands.
It's summer ,go outside play with your friends!!! It will be ready by the first snow and you'll be able to click around in the new kde. Fun project for winter !!! 
But if you still want play in front of your screen i would suggest to go play in this [world]("http://gentoo.org") with [this project]("http://overlays.gentoo.org/proj/kde") 
It's a dirty hands distrib so more chance to get answered from them.
[here]("http://forums.gentoo.org/") .

have fun

---

### Post by solarwind on 2007-06-27
> **rcmn said:**
> hum... no i don't have time for kde4 alpha or any other dev thing . it's partly why I'm using ubuntu , to be a user with almost clean hands.
It's summer ,go outside play with your friends!!! It will be ready by the first snow and you'll be able to click around in the new kde. Fun project for winter !!! 
But if you still want play in front of your screen i would suggest to go play in this [world]("http://gentoo.org") with [this project]("http://overlays.gentoo.org/proj/kde") 
It's a dirty hands distrib so more chance to get answered from them.
[here]("http://forums.gentoo.org/") .

have fun

Boy, you're quite arrogant.

---

### Post by rcmn on 2007-06-27
=>[exit]

---

### Post by Erunno on 2007-06-27
> **solarwind said:**
> Boy, you're quite arrogant.

I don't condone the tone but basically I'm also wondering what you expect from an alpha version of KDE4. It's highly unstable and feature-incomplete and generally more geared towards people with a bit more experience with computers to help with the devopment in form of bug reports and suggestions.

Either way, follow the guide on the kubuntu.org website. I had the crashing problem as well so I created a new user and it worked after that. Never did any research about the failure to log in as it suits me better to experiment with an account which I don't use daily.

---

### Post by solarwind on 2007-06-28
> **Erunno said:**
> I don't condone the tone but basically I'm also wondering what you expect from an alpha version of KDE4. It's highly unstable and feature-incomplete and generally more geared towards people with a bit more experience with computers to help with the devopment in form of bug reports and suggestions.

Either way, follow the guide on the kubuntu.org website. I had the crashing problem as well so I created a new user and it worked after that. Never did any research about the failure to log in as it suits me better to experiment with an account which I don't use daily.


Lol, I know computers QUITE well: assembler, C, C++, PHP, Python, Java, and can mod KDE, but I must be cranky atm, sorry lol...

---

### Post by LuisAugusto on 2007-07-02
I tried to use kdesvn-build. It needs some tweaks of course. I successfully compiled Qt-copy and kdesupport, but kde-libs didn't compile and the log didn't mark any kind of error (it said something aboutu optional package, but, that's OPTIONAL)

```
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.3.0
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
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Building kdelibs...
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_NO_THREADSAFE_STATICS
-- Performing Test __KDE_HAVE_NO_THREADSAFE_STATICS - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE4 kconfig_compiler preprocessor: /home/augusto/kdesvn/build/kdelibs/bin/./kconfig_compiler.shell
-- Found ZLIB: /usr/lib/libz.so
-- Found Strigi: /home/augusto/kde/lib/libstreamanalyzer.so
-- Found Strigi: /home/augusto/kde/lib/libstreams.so
-- Make sure Strigi is a recent SVN version!
-- ** svn://anonsvn.kde.org/home/kde/trunk/kdesupport/strigi
-- Could not find Soprano includes.
-- Could not find Soprano library.
-- Looking for BZ2_bzCompressInit in /usr/lib/libbz2.so
-- Looking for BZ2_bzCompressInit in /usr/lib/libbz2.so - found
-- Found BZip2: /usr/lib/libbz2.so
-- Looking for include files HAVE_LIBINTL_H
-- Looking for include files HAVE_LIBINTL_H - found
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
-- Looking for include files HAVE_ATTR_LIBATTR_H
-- Looking for include files HAVE_ATTR_LIBATTR_H - not found.
-- Looking for include files HAVE_SYS_XATTR_H
-- Looking for include files HAVE_SYS_XATTR_H - found
-- Looking for include files HAVE_SYS_ACL_H
-- Looking for include files HAVE_SYS_ACL_H - not found.
-- Looking for include files HAVE_ACL_LIBACL_H
-- Looking for include files HAVE_ACL_LIBACL_H - not found.
-- Looking for include files HAVE_STDIO_H
-- Looking for include files HAVE_STDIO_H - found
-- Looking for include files HAVE_STDLIB_H
-- Looking for include files HAVE_STDLIB_H - found
-- Looking for include files HAVE_STRING_H
-- Looking for include files HAVE_STRING_H - found
-- Looking for include files HAVE_STRINGS_H
-- Looking for include files HAVE_STRINGS_H - found
-- Looking for include files HAVE_MALLOC_H
-- Looking for include files HAVE_MALLOC_H - found
-- Looking for include files HAVE_DLFCN_H
-- Looking for include files HAVE_DLFCN_H - found
-- Looking for include files TIME_WITH_SYS_TIME
-- Looking for include files TIME_WITH_SYS_TIME - found
-- Looking for include files HAVE_CRT_EXTERNS_H
-- Looking for include files HAVE_CRT_EXTERNS_H - not found.
-- Looking for include files HAVE_ALLOCA_H
-- Looking for include files HAVE_ALLOCA_H - found
-- Looking for include files HAVE_FSTAB_H
-- Looking for include files HAVE_FSTAB_H - found
-- Looking for include files HAVE_LIMITS_H
-- Looking for include files HAVE_LIMITS_H - found
-- Looking for include files HAVE_MNTENT_H
-- Looking for include files HAVE_MNTENT_H - found
-- Looking for include files HAVE_SYSENT_H
-- Looking for include files HAVE_SYSENT_H - not found.
-- Looking for include files HAVE_SYS_BITYPES_H
-- Looking for include files HAVE_SYS_BITYPES_H - found
-- Looking for include files HAVE_SYS_MMAN_H
-- Looking for include files HAVE_SYS_MMAN_H - found
-- Looking for include files HAVE_SYS_STAT_H
-- Looking for include files HAVE_SYS_STAT_H - found
-- Looking for include files HAVE_SYS_UCRED_H
-- Looking for include files HAVE_SYS_UCRED_H - not found.
-- Looking for include files HAVE_SYS_TYPES_H
-- Looking for include files HAVE_SYS_TYPES_H - found
-- Looking for include files HAVE_SYS_SELECT_H
-- Looking for include files HAVE_SYS_SELECT_H - found
-- Looking for include files HAVE_SYS_PARAM_H
-- Looking for include files HAVE_SYS_PARAM_H - found
-- Looking for include files HAVE_SYS_MNTTAB_H
-- Looking for include files HAVE_SYS_MNTTAB_H - not found.
-- Looking for include files HAVE_SYS_MNTENT_H
-- Looking for include files HAVE_SYS_MNTENT_H - not found.
-- Looking for include files HAVE_SYS_MOUNT_H
-- Looking for include files HAVE_SYS_MOUNT_H - found
-- Looking for include files HAVE_UNISTD_H
-- Looking for include files HAVE_UNISTD_H - found
-- Looking for include files HAVE_STDINT_H
-- Looking for include files HAVE_STDINT_H - found
-- Looking for include files HAVE_NETINET_IN_H
-- Looking for include files HAVE_NETINET_IN_H - found
-- Looking for include files HAVE_PATHS_H
-- Looking for include files HAVE_PATHS_H - found
-- Looking for include files HAVE_ERRNO_H
-- Looking for include files HAVE_ERRNO_H - found
-- Looking for include files HAVE_SYS_TIME_H
-- Looking for include files HAVE_SYS_TIME_H - found
-- Looking for include files HAVE_VALGRIND_MEMCHECK_H
-- Looking for include files HAVE_VALGRIND_MEMCHECK_H - not found.
-- Looking for include files HAVE_CRTDBG_H
-- Looking for include files HAVE_CRTDBG_H - not found.
-- Looking for include files HAVE_ARPA_NAMESER8_COMPAT_H
-- Looking for include files HAVE_ARPA_NAMESER8_COMPAT_H - not found.
-- Looking for strcmp
-- Looking for strcmp - found
-- Looking for strrchr
-- Looking for strrchr - found
-- Looking for strtoll
-- Looking for strtoll - found
-- Looking for S_ISSOCK
-- Looking for S_ISSOCK - found
-- Looking for vsnprintf
-- Looking for vsnprintf - found
-- Looking for posix_fadvise
-- Looking for posix_fadvise - found
-- Looking for backtrace
-- Looking for backtrace - found
-- Looking for getpagesize
-- Looking for getpagesize - found
-- Looking for getpeereid
-- Looking for getpeereid - not found
-- Looking for madvise
-- Looking for madvise - found
-- Looking for mmap
-- Looking for mmap - found
-- Looking for readdir_r
-- Looking for readdir_r - found
-- Looking for sendfile
-- Looking for sendfile - found
-- Looking for setlocale
-- Looking for setlocale - found
-- Looking for srandom
-- Looking for srandom - found
-- Looking for _NSGetEnviron
-- Looking for _NSGetEnviron - not found
-- Looking for gettimeofday
-- Looking for gettimeofday - found
-- Looking for volmgt_running in volmgt
-- Looking for volmgt_running in volmgt - not found
-- Looking for res_init in resolv
-- Looking for res_init in resolv - not found
-- Looking for __res_init in resolv
-- Looking for __res_init in resolv - found
-- Looking for include files HAVE_LIBUTIL_H
-- Looking for include files HAVE_LIBUTIL_H - not found.
-- Looking for include files HAVE_UTIL_H
-- Looking for include files HAVE_UTIL_H - not found.
-- Looking for include files HAVE_TERMIOS_H
-- Looking for include files HAVE_TERMIOS_H - found
-- Looking for include files HAVE_TERMIO_H
-- Looking for include files HAVE_TERMIO_H - found
-- Looking for include files HAVE_PTY_H
-- Looking for include files HAVE_PTY_H - found
-- Looking for include files HAVE_SYS_STROPTS_H
-- Looking for include files HAVE_SYS_STROPTS_H - found
-- Looking for include files HAVE_SYS_FILIO_H
-- Looking for include files HAVE_SYS_FILIO_H - not found.
-- Looking for ptsname
-- Looking for ptsname - found
-- Looking for revoke
-- Looking for revoke - found
-- Looking for _getpty
-- Looking for _getpty - not found
-- Looking for getpt
-- Looking for getpt - found
-- Looking for grantpt
-- Looking for grantpt - found
-- Looking for unlockpt
-- Looking for unlockpt - found
-- Looking for addToUtmp in utempter
-- Looking for addToUtmp in utempter - not found
-- Looking for openpty in util
-- Looking for openpty in util - found
-- PTY uses openpty(3)
-- PTY multiplexer: /dev/ptmx
-- Looking for getmntinfo
-- Looking for getmntinfo - not found
-- Looking for initgroups
-- Looking for initgroups - found
-- Looking for mkstemps
-- Looking for mkstemps - not found
-- Looking for mkstemp
-- Looking for mkstemp - found
-- Looking for mkdtemp
-- Looking for mkdtemp - found
-- Looking for random
-- Looking for random - found
-- Looking for strlcpy
-- Looking for strlcpy - not found
-- Looking for strlcat
-- Looking for strlcat - not found
-- Looking for strcasestr
-- Looking for strcasestr - found
-- Looking for setenv
-- Looking for setenv - found
-- Looking for seteuid
-- Looking for seteuid - found
-- Looking for setmntent
-- Looking for setmntent - found
-- Looking for unsetenv
-- Looking for unsetenv - found
-- Looking for usleep
-- Looking for usleep - found
-- Performing Test HAVE_MKSTEMPS_PROTO
-- Performing Test HAVE_MKSTEMPS_PROTO - Failed
-- Performing Test HAVE_MKDTEMP_PROTO
-- Performing Test HAVE_MKDTEMP_PROTO - Success
-- Performing Test HAVE_MKSTEMP_PROTO
-- Performing Test HAVE_MKSTEMP_PROTO - Success
-- Performing Test HAVE_STRLCAT_PROTO
-- Performing Test HAVE_STRLCAT_PROTO - Failed
-- Performing Test HAVE_STRCASESTR_PROTO
-- Performing Test HAVE_STRCASESTR_PROTO - Success
-- Performing Test HAVE_STRLCPY_PROTO
-- Performing Test HAVE_STRLCPY_PROTO - Failed
-- Performing Test HAVE_RANDOM_PROTO
-- Performing Test HAVE_RANDOM_PROTO - Success
-- Performing Test HAVE_RES_INIT_PROTO
-- Performing Test HAVE_RES_INIT_PROTO - Success
-- Performing Test HAVE_SETENV_PROTO
-- Performing Test HAVE_SETENV_PROTO - Success
-- Performing Test HAVE_SRANDOM_PROTO
-- Performing Test HAVE_SRANDOM_PROTO - Success
-- Performing Test HAVE_UNSETENV_PROTO
-- Performing Test HAVE_UNSETENV_PROTO - Success
-- Performing Test HAVE_USLEEP_PROTO
-- Performing Test HAVE_USLEEP_PROTO - Success
-- Performing Test HAVE_INITGROUPS_PROTO
-- Performing Test HAVE_INITGROUPS_PROTO - Success
-- Performing Test HAVE_SETREUID_PROTO
-- Performing Test HAVE_SETREUID_PROTO - Success
-- Performing Test HAVE_SETEUID_PROTO
-- Performing Test HAVE_SETEUID_PROTO - Success
-- Performing Test HAVE_TRUNC
-- Performing Test HAVE_TRUNC - Success
-- Check size of struct ucred
-- Check size of struct ucred - done
-- Check size of time_t
-- Check size of time_t - done
-- Performing Test GETMNTINFO_USES_STATVFS
-- Performing Test GETMNTINFO_USES_STATVFS - Failed
-- Performing Test HAVE_STRUCT_TM_TM_ZONE
-- Performing Test HAVE_STRUCT_TM_TM_ZONE - Success
-- Performing Test HAVE_TM_GMTOFF
-- Performing Test HAVE_TM_GMTOFF - Success
-- Performing Test HAVE_DIRENT_D_TYPE
-- Performing Test HAVE_DIRENT_D_TYPE - Success
-- Check if the system is big endian
-- Check if the system is big endian - little endian
-- Performing Test HAVE_X86_MMX
-- Performing Test HAVE_X86_MMX - Success
-- Performing Test HAVE_X86_SSE
-- Performing Test HAVE_X86_SSE - Success
-- Performing Test HAVE_X86_SSE2
-- Performing Test HAVE_X86_SSE2 - Success
-- Performing Test HAVE_X86_3DNOW
-- Performing Test HAVE_X86_3DNOW - Success
-- Performing Test HAVE_PPC_ALTIVEC
-- Performing Test HAVE_PPC_ALTIVEC - Failed
-- Performing Test HAVE_QSSLSOCKET
-- Performing Test HAVE_QSSLSOCKET - Failed
CMake Error: KDE Requires Qt to be built with SSL support
-- Looking for include files HAVE_NET_IF_H
-- Looking for include files HAVE_NET_IF_H - found
-- Looking for include files HAVE_STROPTS_H
-- Looking for include files HAVE_STROPTS_H - found
-- Looking for inet_pton
-- Looking for inet_pton - found
-- Looking for inet_ntop
-- Looking for inet_ntop - found
-- Looking for getprotobyname_r
-- Looking for getprotobyname_r - found
-- Looking for poll
-- Looking for poll - found
-- Looking for getservbyname_r
-- Looking for getservbyname_r - found
-- Looking for getservbyport_r
-- Looking for getservbyport_r - found
-- Looking for gethostbyname2
-- Looking for gethostbyname2 - found
-- Looking for gethostbyname2_r
-- Looking for gethostbyname2_r - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for gethostbyname_r
-- Looking for gethostbyname_r - found
-- Looking for if_nametoindex
-- Looking for if_nametoindex - found
-- Performing Test HAVE_GETSERVBYNAME_R_PROTO
-- Performing Test HAVE_GETSERVBYNAME_R_PROTO - Success
-- Looking for freeaddrinfo
-- Looking for freeaddrinfo - found
-- Looking for getnameinfo
-- Looking for getnameinfo - found
-- Looking for getaddrinfo
-- Looking for getaddrinfo - found
-- Looking for res_init
-- Looking for res_init - found
-- Performing Test HAVE_STRUCT_SOCKADDR_SA_LEN
-- Performing Test HAVE_STRUCT_SOCKADDR_SA_LEN - Failed
-- Check size of struct addrinfo
-- Check size of struct addrinfo - done
-- Check size of struct sockaddr_in6
-- Check size of struct sockaddr_in6 - done
-- Looking for pthread_attr_get_np in pthread
-- Looking for pthread_attr_get_np in pthread - not found
-- Looking for pthread_getattr_np in pthread
-- Looking for pthread_getattr_np in pthread - found
-- Looking for include files HAVE_FLOAT_H
-- Looking for include files HAVE_FLOAT_H - found
-- Looking for include files HAVE_SYS_TIMEB_H
-- Looking for include files HAVE_SYS_TIMEB_H - found
-- Looking for include files HAVE_IEEEFP_H
-- Looking for include files HAVE_IEEEFP_H - not found.
-- Looking for include files HAVE_PTHREAD_NP_H
-- Looking for include files HAVE_PTHREAD_NP_H - not found.
-- Looking for include files HAVE_MEMCHECK_H
-- Looking for include files HAVE_MEMCHECK_H - not found.
-- Looking for _finite
-- Looking for _finite - not found
-- Looking for finite
-- Looking for finite - found
-- Looking for isnan
-- Looking for isnan - found
-- Looking for isinf
-- Looking for isinf - found
-- Looking for include files HAVE_REGEX_H
-- Looking for include files HAVE_REGEX_H - found
-- Looking for include files SYS_INOTIFY_H_FOUND
-- Looking for include files SYS_INOTIFY_H_FOUND - found
-- Looking for snd_seq_create_simple_port in asound
-- Looking for snd_seq_create_simple_port in asound - not found
-- ALSA not found
-- Looking for include files HAVE_SYS_SOUNDCARD_H
-- Looking for include files HAVE_SYS_SOUNDCARD_H - found
-- Looking for include files HAVE_MACHINE_SOUNDCARD_H
-- Looking for include files HAVE_MACHINE_SOUNDCARD_H - not found.
-- Looking for include files HAVE_LINUX_AWE_VOICE_H
-- Looking for include files HAVE_LINUX_AWE_VOICE_H - found
-- Looking for include files HAVE_AWE_VOICE_H
-- Looking for include files HAVE_AWE_VOICE_H - not found.
-- Looking for include files HAVE__USR_SRC_SYS_I386_ISA_SOUND_AWE_VOICE_H
-- Looking for include files HAVE__USR_SRC_SYS_I386_ISA_SOUND_AWE_VOICE_H - not found.
-- Looking for include files HAVE__USR_SRC_SYS_GNU_I386_ISA_SOUND_AWE_VOICE_H
-- Looking for include files HAVE__USR_SRC_SYS_GNU_I386_ISA_SOUND_AWE_VOICE_H - not found.
-- Looking for C++ include sys/asoundlib.h
-- Looking for C++ include sys/asoundlib.h - not found
-- Looking for C++ include alsa/asoundlib.h
-- Looking for C++ include alsa/asoundlib.h - not found
-- Looking for snd_pcm_resume in asound
-- Looking for snd_pcm_resume in asound - not found
-- ALSA not found
-- ALSA version not known. ALSA output will probably not work correctly.
-- Found LibXml2: /usr/lib/libxml2.so
-- Found LibXslt: /usr/lib/libxslt.so
-- Found shared-mime-info version: 0.20
-- Looking for __progname,
-- Looking for __progname, - not found
-- Looking for include files HAVE_SYS_PSTAT_H
-- Looking for include files HAVE_SYS_PSTAT_H - not found.
-- Looking for pstat,
-- Looking for pstat, - not found
-- Looking for setproctitle,
-- Looking for setproctitle, - not found
-- Looking for ippDeleteAttribute in cups
-- Looking for ippDeleteAttribute in cups - found
-- Found Cups: /usr/lib/libcups.so
-- Found JPEG: /usr/lib/libjpeg.so
-- Performing Test GIF_FOUND
-- Performing Test GIF_FOUND - Success
-- Found GIF: /usr/lib/libgif.so
-- Found PNG: /usr/lib/libpng.so
-- Found JPEG: /usr/lib/libjpeg.so
-- 
----------------------------------------------------------------------------------
-- The following list of OPTIONAL packages were located on your system.         --
-- You will have all the following features available from this software.       --
----------------------------------------------------------------------------------
+ CUPS
----------------------------------------------------------------------------------
-- The following list of OPTIONAL packages could NOT be located on your system. --
-- Consider installing them to enable more features from this software.         --
----------------------------------------------------------------------------------
+ Soprano: Soprano Libraries <kdesupport>
Provide metadata support (for semantic desktop).

-- Configuring done
```

---

### Post by solarwind on 2007-07-02
Hmm. I used the binary repository. I have a problem with RUNNING it, lol. Try using the repository for KDE 4 Alpha 1 I believe.

---

### Post by Traceur-UK on 2007-07-03
rcmn, that's fairly innappropriate. The guy wanted some genuine advice. solarwind, I doubt there'll be any pre-compiled sources for an alpha-release. But try compiling the sources and whatnot, you might just learn something. But as atlfalcons noted, it's in alpha release so definitely don't expect it to be bug-free.

---

