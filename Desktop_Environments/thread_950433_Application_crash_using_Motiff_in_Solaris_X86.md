---
title: "Application crash using Motiff in Solaris X86"
date: 2008-10-17
forum: Desktop Environments
---

### Post by gsb@123 on 2008-10-17
Hi,

 OS : Solaris X86 32 bit
 Motif , X11 are installed 

  I am using uil files for GUI. My application crashes unexpectedly and generated core. I am not able to open the widgets. 

I tried debugging the core. But it's pointing to libxm.so.4
I took the truss output also. It's showing like Incurred fault #6, FLTBOUNDS  %pc = 0xFE8A72D8
      siginfo: SIGSEGV SEGV_MAPERR addr=0x00000000
    Received signal #11, SIGSEGV [default]
      siginfo: SIGSEGV SEGV_MAPERR addr=0x00000000

Here is the call stack

#0  0xfe8a72d8 in _render () from /usr/MOTIF_LINK/lib/libXm.so.4
#1  0xfe94cd06 in _XmStringRender () from /usr/MOTIF_LINK/lib/libXm.so.4
#2  0xfe8b4545 in DrawItems () from /usr/MOTIF_LINK/lib/libXm.so.4
#3  0xfe8b1924 in DrawList () from /usr/MOTIF_LINK/lib/libXm.so.4
#4  0xfe8b1807 in Redisplay () from /usr/MOTIF_LINK/lib/libXm.so.4
#5  0xfe7f5d8e in SendExposureEvent () from /usr/X11_LINK/lib/libXt.so.4
#6  0xfe7f5c38 in CompressExposures () from /usr/X11_LINK/lib/libXt.so.4
#7  0xfe7f4cad in XtDispatchEventToWidget () from /usr/X11_LINK/lib/libXt.so.4
#8  0xfe7f4959 in _XtDefaultDispatcher () from /usr/X11_LINK/lib/libXt.so.4
#9  0xfe7f4597 in XtDispatchEvent () from /usr/X11_LINK/lib/libXt.so.4
#10 0xfef06b2a in MainEventLoop (EventInfoPtr=0x8081f10) at comAPIs.c:2484
#11 0x0805c58c in main (argc=19, argv=0x8044598) at main.c:2503

Here is the truss output for this application:

pollsys(0x08042EF0, 1, 0x08042F68, 0x00000000) (sleeping...)
pollsys(0x08042EF0, 1, 0x08042F68, 0x00000000)  = 1
ioctl(3, I_NREAD, 0x08042EA0)                   = 1
read(3, "\f02 A\b h\0C0\0\0\0  \0".., 2048)     = 2048
ioctl(3, I_NREAD, 0x080430B0)                   = 1
read(3, "\f01 A\b k\0C0\0C9\0\0\0".., 96)       = 96
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " B\007\0 h\0C0\0\r\0C0\0".., 56)      = 56
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " B\0\v\0BC\0C0\0\r\0C0\0".., 88)      = 88
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 8\004\013\0C0\0\0\0\b\0".., 60)      = 60
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 8\004\013\0C0\0\0\0\b\0".., 64)      = 64
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 8\004\013\0C0\0\0\0\b\0".., 60)      = 60
ioctl(3, I_NREAD, 0x080430B0)                   = 0
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 8\004\013\0C0\0\0\0\b\0".., 100)     = 100
ioctl(3, I_NREAD, 0x080430B0)                   = 0
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " F\005\0B9\0C0\019\0C0\0".., 236)     = 236
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " F\005\0B8\0C0\019\0C0\0".., 236)     = 236
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " F\005\0B7\0C0\019\0C0\0".., 240)     = 240
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " F\005\0B6\0C0\019\0C0\0".., 236)     = 236
ioctl(3, I_NREAD, 0x080430B0)                   = 0
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " ;\005\01F\0C0\0\0\0\0\0".., 540)     = 540
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 8\004\013\0C0\0\0\0\b\0".., 56)      = 56
ioctl(3, I_NREAD, 0x080430B0)                   = 0
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 8\004\013\0C0\0\0\0\b\0".., 44)      = 44
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " ;\005\01F\0C0\0\0\0\0\0".., 540)     = 540
ioctl(3, I_NREAD, 0x080430B0)                   = 0
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 8\004\013\0C0\0\0\0\b\0".., 40)      = 40
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " F\005\0A7\0C0\019\0C0\0".., 236)     = 236
"satish.log" 442 lines, 19296 characters
ioctl(3, I_NREAD, 0x080430B0)                   = 0
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\013\0C0\0\0\0\b\0".., 40)      = 40
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\01D\0C0\004\0\0\0".., 432)     = 432
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\013\0C0\0\0\0\b\0".., 40)      = 40
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\01D\0C0\004\0\0\0".., 432)     = 432
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\013\0C0\0\0\0\b\0".., 40)      = 40
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\01D\0C0\004\0\0\0".., 432)     = 432
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\013\0C0\0\0\0\b\0".., 44)      = 44
ioctl(3, I_NREAD, 0x080430B0)                   = 0
write(3, " 80104\013\0C0\0\0\0\b\0".., 304)     = 304
    Incurred fault #6, FLTBOUNDS  %pc = 0xFE8A72D8
      siginfo: SIGSEGV SEGV_MAPERR addr=0x00000000
    Received signal #11, SIGSEGV [default]
      siginfo: SIGSEGV SEGV_MAPERR addr=0x00000000
~

what could be the problem

---

