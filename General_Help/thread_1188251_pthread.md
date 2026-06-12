---
title: "pthread"
date: 2009-06-15
forum: General Help
---

### Post by SpeeDemon92 on 2009-06-15
Hy, I'm new  with ubuntu ...  and I have some problems with installing pthread for some programs in C.
I downloaded pmpthreads-1.8.1. Opened the terminal and wrote:
```

cd /home/speedemon/Desktop/pmpthreads-*
./configure

```I got :
```

loading cache ./config.cache
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking compiler availability and simple error detection... ok
checking how to run the C preprocessor... (cached) gcc -E
checking for ranlib... (cached) ranlib
checking host system type... i686-unknown-linux
checking target system type... i686-unknown-linux
checking build system type... i686-unknown-linux
checking for sys/termio.h... (cached) no
checking for termios.h... (cached) yes
checking for termio.h... (cached) yes
checking for alloc.h... (cached) no
checking for va_list.h... (cached) no
checking for syscall.h... (cached) yes
checking for sys/syscall.h... (cached) yes
checking for sys/filio.h... (cached) no
checking for syscall open... (cached) yes
checking for syscall write... (cached) yes
checking for syscall read... (cached) yes
checking for syscall creat... (cached) yes
checking for syscall close... (cached) yes
checking for syscall fcntl... (cached) yes
checking for syscall lseek... (cached) yes
checking for syscall dup2... (cached) yes
checking for syscall dup... (cached) yes
checking for syscall pipe... (cached) yes
checking for syscall fchmod... (cached) yes
checking for syscall fchown... (cached) yes
checking for syscall execve... (cached) yes
checking for syscall fstat... (cached) yes
checking for syscall lstat... (cached) yes
checking for syscall link... (cached) yes
checking for syscall unlink... (cached) yes
checking for syscall chdir... (cached) yes
checking for syscall chown... (cached) yes
checking for syscall chmod... (cached) yes
checking for syscall stat... (cached) yes
checking for syscall rename... (cached) yes
checking for syscall select... (cached) yes
checking for syscall getdtablesize... (cached) no
checking for syscall ioctl... (cached) yes
checking for syscall ftruncate... (cached) yes
checking for syscall flock... (cached) yes
checking for syscall fstatfs... (cached) yes
checking for syscall sigsuspend... (cached) yes
checking for syscall sigaction... (cached) yes
checking for syscall sigpause... (cached) no
checking for syscall sigprocmask... (cached) yes
checking for syscall ksigaction... (cached) no
checking for syscall getdents... (cached) yes
checking for syscall readdir... (cached) yes
checking for syscall getdirentries... (cached) no
checking for syscall wait4... (cached) yes
checking for syscall wait3... (cached) no
checking for syscall waitpid... (cached) yes
checking for syscall waitsys... (cached) no
checking for syscall socket... (cached) no
checking for syscall bind... (cached) no
checking for syscall connect... (cached) no
checking for syscall accept... (cached) no
checking for syscall listen... (cached) no
checking for syscall getsockopt... (cached) no
checking for syscall setsockopt... (cached) no
checking for syscall socketpair... (cached) no
checking for syscall poll... (cached) yes
checking for syscall putmsg... (cached) no
checking for syscall getmsg... (cached) no
checking for syscall socketcall... (cached) yes
checking for syscall pgrpsys... (cached) no
checking for syscall exit... (cached) yes
checking for syscall readv... (cached) yes
checking for syscall writev... (cached) yes
checking for syscall send... (cached) no
checking for syscall sendto... (cached) no
checking for syscall sendmsg... (cached) no
checking for syscall recv... (cached) no
checking for syscall recvfrom... (cached) no
checking for syscall recvmsg... (cached) no
checking for syscall getpeername... (cached) no
checking for syscall getsockname... (cached) no
checking for syscall shutdown... (cached) no
checking for syscall getpgrp... (cached) yes
checking for syscall fork... (cached) yes
checking for ANSI C header files... (cached) no
checking for off_t... (cached) yes
checking for size_t... (cached) yes
checking return type of signal handlers... (cached) void
checking for ssize_t... (cached) yes
checking for time_t... (cached) yes
checking for sys/time.h... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for struct timespec in sys/time.h... (cached) yes
checking type of size_t... (cached) unsigned int
checking type of ssize_t... (cached) int
checking type of clock_t... (cached) long
checking type of time_t... (cached) long
checking for fpos_t in stdio.h... (cached) yes
checking type of fpos_t... 
checking type of off_t... (cached) long
checking type of va_list... (cached) char *
checking IP address type... (cached) unsigned long
checking IP port type... (cached) unsigned short
checking pathname for terminal devices directory... (cached) /dev/
checking directory name for time zone info... /usr/share/zoneinfo
checking filename for local time zone... /usr/share/zoneinfo/localtime
checking for vfork... (cached) yes
configure: warning: No syscall template file syscall-template-i386-linux-1.0.S found.
creating ./config.status
creating config.flags
creating GNUmakefile
creating Makefile
creating lib/Makefile
creating lib/libpthreadutil/Makefile
creating bin/Makefile
creating bin/finger/Makefile
creating tests/Makefile
creating config.h
config.h is unchanged
linking ./config/../machdep/engine-i386-linux-1.0.h to include/pthread/machdep.h
linking ./config/../machdep/posix-linux-1.0.h to include/pthread/posix.h
linking ./config/../machdep/engine-i386-linux-1.0.c to machdep.c
linking ./config/../machdep/syscall-i386-linux-1.0.S to syscall.S
linking ./config/../machdep/linux-1.0 to include/sys

```How you can see, there are some files missing ...what can I do?
And to continue I wrote
```

make

```and got
```

gcc -I. -Iinclude -I/home/speedemon/Desktop/pmpthreads-1.8.1/include -DPTHREAD_KERNEL -g -O2 -Werror -c /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c -o obj/gethostbyaddr.o
In file included from include/unistd.h:40,
                 from include/pthread/machdep.h:8,
                 from include/pthread.h:49,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/sys/__unistd.h:50:23: error: posix_opt.h: No such file or directory
cc1: warnings being treated as errors
In file included from include/pthread.h:54,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/sleep.h:47: error: ‘struct timespec’ declared inside parameter list
include/pthread/sleep.h: In function ‘machdep_gettimeofday’:
include/pthread/sleep.h:53: error: dereferencing pointer to incomplete type
include/pthread/sleep.h:53: error: dereferencing pointer to incomplete type
include/pthread/sleep.h: At top level:
include/pthread/sleep.h:59: error: ‘struct timespec’ declared inside parameter list
In file included from include/pthread.h:55,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/mutex.h:68: error: conflicting types for ‘pthread_mutex_t’
/usr/include/bits/pthreadtypes.h:104: error: previous declaration of ‘pthread_mutex_t’ was here
include/pthread/mutex.h:73: error: conflicting types for ‘pthread_mutexattr_t’
/usr/include/bits/pthreadtypes.h:110: error: previous declaration of ‘pthread_mutexattr_t’ was here
In file included from include/pthread.h:56,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/cond.h:64: error: conflicting types for ‘pthread_cond_t’
/usr/include/bits/pthreadtypes.h:130: error: previous declaration of ‘pthread_cond_t’ was here
include/pthread/cond.h:69: error: conflicting types for ‘pthread_condattr_t’
/usr/include/bits/pthreadtypes.h:136: error: previous declaration of ‘pthread_condattr_t’ was here
include/pthread/cond.h:92: error: ‘struct timespec’ declared inside parameter list
In file included from include/pthread.h:61,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/specific.h:52: error: conflicting types for ‘pthread_key_t’
/usr/include/bits/pthreadtypes.h:140: error: previous declaration of ‘pthread_key_t’ was here
In file included from include/pthread.h:66,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/pthread_once.h:44: error: conflicting types for ‘pthread_once_t’
/usr/include/bits/pthreadtypes.h:144: error: previous declaration of ‘pthread_once_t’ was here
In file included from include/pthread.h:69,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/pthread_attr.h:96: error: conflicting types for ‘pthread_attr_t’
/usr/include/bits/pthreadtypes.h:57: error: previous declaration of ‘pthread_attr_t’ was here
In file included from /usr/include/asm/signal.h:6,
                 from /usr/include/linux/signal.h:4,
                 from include/sys/__signal.h:2,
                 from include/signal.h:41,
                 from include/pthread.h:71,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from /usr/include/linux/signal.h:4,
                 from include/sys/__signal.h:2,
                 from include/signal.h:41,
                 from include/pthread.h:71,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
/usr/include/asm/signal.h:15: error: conflicting types for ‘sigset_t’
/usr/include/sys/select.h:38: error: previous declaration of ‘sigset_t’ was here
In file included from /usr/include/asm/siginfo.h:8,
                 from /usr/include/linux/signal.h:5,
                 from include/sys/__signal.h:2,
                 from include/signal.h:41,
                 from include/pthread.h:71,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
/usr/include/asm-generic/siginfo.h:56: error: expected specifier-qualifier-list before ‘timer_t’
In file included from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread.h:267: error: conflicting types for ‘pthread_t’
/usr/include/bits/pthreadtypes.h:50: error: previous declaration of ‘pthread_t’ was here
In file included from include/stdio.h:47,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:41:
include/sys/__stdio.h:7: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fpos_t’
In file included from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:41:
include/stdio.h:194: error: expected declaration specifiers or ‘...’ before ‘fpos_t’
include/stdio.h:204: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
In file included from include/netdb.h:42,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:44:
/usr/include/netinet/in.h:227: error: expected specifier-qualifier-list before ‘__SOCKADDR_COMMON’
/usr/include/netinet/in.h:241: error: expected specifier-qualifier-list before ‘__SOCKADDR_COMMON’
/usr/include/netinet/in.h:293: error: field ‘gr_group’ has incomplete type
/usr/include/netinet/in.h:302: error: field ‘gsr_group’ has incomplete type
/usr/include/netinet/in.h:305: error: field ‘gsr_source’ has incomplete type
/usr/include/netinet/in.h:337: error: field ‘gf_group’ has incomplete type
/usr/include/netinet/in.h:345: error: array type has incomplete element type
make: *** [obj/gethostbyaddr.o] Error 1

```And after this I wrote
```

make install

```and got
```

gcc -I. -Iinclude -I/home/speedemon/Desktop/pmpthreads-1.8.1/include -DPTHREAD_KERNEL -g -O2 -Werror -c /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c -o obj/gethostbyaddr.o
In file included from include/unistd.h:40,
                 from include/pthread/machdep.h:8,
                 from include/pthread.h:49,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/sys/__unistd.h:50:23: error: posix_opt.h: No such file or directory
cc1: warnings being treated as errors
In file included from include/pthread.h:54,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/sleep.h:47: error: ‘struct timespec’ declared inside parameter list
include/pthread/sleep.h: In function ‘machdep_gettimeofday’:
include/pthread/sleep.h:53: error: dereferencing pointer to incomplete type
include/pthread/sleep.h:53: error: dereferencing pointer to incomplete type
include/pthread/sleep.h: At top level:
include/pthread/sleep.h:59: error: ‘struct timespec’ declared inside parameter list
In file included from include/pthread.h:55,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/mutex.h:68: error: conflicting types for ‘pthread_mutex_t’
/usr/include/bits/pthreadtypes.h:104: error: previous declaration of ‘pthread_mutex_t’ was here
include/pthread/mutex.h:73: error: conflicting types for ‘pthread_mutexattr_t’
/usr/include/bits/pthreadtypes.h:110: error: previous declaration of ‘pthread_mutexattr_t’ was here
In file included from include/pthread.h:56,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/cond.h:64: error: conflicting types for ‘pthread_cond_t’
/usr/include/bits/pthreadtypes.h:130: error: previous declaration of ‘pthread_cond_t’ was here
include/pthread/cond.h:69: error: conflicting types for ‘pthread_condattr_t’
/usr/include/bits/pthreadtypes.h:136: error: previous declaration of ‘pthread_condattr_t’ was here
include/pthread/cond.h:92: error: ‘struct timespec’ declared inside parameter list
In file included from include/pthread.h:61,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/specific.h:52: error: conflicting types for ‘pthread_key_t’
/usr/include/bits/pthreadtypes.h:140: error: previous declaration of ‘pthread_key_t’ was here
In file included from include/pthread.h:66,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/pthread_once.h:44: error: conflicting types for ‘pthread_once_t’
/usr/include/bits/pthreadtypes.h:144: error: previous declaration of ‘pthread_once_t’ was here
In file included from include/pthread.h:69,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread/pthread_attr.h:96: error: conflicting types for ‘pthread_attr_t’
/usr/include/bits/pthreadtypes.h:57: error: previous declaration of ‘pthread_attr_t’ was here
In file included from /usr/include/asm/signal.h:6,
                 from /usr/include/linux/signal.h:4,
                 from include/sys/__signal.h:2,
                 from include/signal.h:41,
                 from include/pthread.h:71,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from /usr/include/linux/signal.h:4,
                 from include/sys/__signal.h:2,
                 from include/signal.h:41,
                 from include/pthread.h:71,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
/usr/include/asm/signal.h:15: error: conflicting types for ‘sigset_t’
/usr/include/sys/select.h:38: error: previous declaration of ‘sigset_t’ was here
In file included from /usr/include/asm/siginfo.h:8,
                 from /usr/include/linux/signal.h:5,
                 from include/sys/__signal.h:2,
                 from include/signal.h:41,
                 from include/pthread.h:71,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
/usr/include/asm-generic/siginfo.h:56: error: expected specifier-qualifier-list before ‘timer_t’
In file included from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:40:
include/pthread.h:267: error: conflicting types for ‘pthread_t’
/usr/include/bits/pthreadtypes.h:50: error: previous declaration of ‘pthread_t’ was here
In file included from include/stdio.h:47,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:41:
include/sys/__stdio.h:7: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fpos_t’
In file included from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:41:
include/stdio.h:194: error: expected declaration specifiers or ‘...’ before ‘fpos_t’
include/stdio.h:204: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
In file included from include/netdb.h:42,
                 from /home/speedemon/Desktop/pmpthreads-1.8.1/net/gethostbyaddr.c:44:
/usr/include/netinet/in.h:227: error: expected specifier-qualifier-list before ‘__SOCKADDR_COMMON’
/usr/include/netinet/in.h:241: error: expected specifier-qualifier-list before ‘__SOCKADDR_COMMON’
/usr/include/netinet/in.h:293: error: field ‘gr_group’ has incomplete type
/usr/include/netinet/in.h:302: error: field ‘gsr_group’ has incomplete type
/usr/include/netinet/in.h:305: error: field ‘gsr_source’ has incomplete type
/usr/include/netinet/in.h:337: error: field ‘gf_group’ has incomplete type
/usr/include/netinet/in.h:345: error: array type has incomplete element type
make: *** [obj/gethostbyaddr.o] Error 1

```Can you help me please ?
ps:  I'm using ubuntu 9.04 on 32b

---

### Post by Yellow Pasque on 2009-06-15
First, make sure you have libc6-dev installed
Also, you may need to use:
```
NO_WARNING_CHECKS=yes configure
```
to prevent *cc1: warnings being treated as errors*

---

### Post by SpeeDemon92 on 2009-06-16
> libc6-dev installed Yes, it's installend. :(
[later] I did , it works  :D 
Thanks for your help :)

---

