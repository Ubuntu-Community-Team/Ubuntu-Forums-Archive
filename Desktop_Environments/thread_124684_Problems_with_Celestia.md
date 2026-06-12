---
title: "Problems with Celestia"
date: 2006-02-02
forum: Desktop Environments
---

### Post by BluenoseJake on 2006-02-02
I am seriously grooving on Kubuntu, but I had a problem with Celestia, it was working fine until I updated to the latest ATI drivers, and now Celestia crashes after displaying the splash screen, I just see the barest flash of the window frame and then poof!, gone.  This continued to occur after reverting back to the radeon drivers that come with Kubuntu, and after uninstalling Breezy's 1.3.2 version and installing 1.4.0 from source.  I have since reinstalled the ATI drivers.  it also occured under KDE 3.4.2, 3.5.0 and 3.5.1, so I am at total loss how to fix it, any ideas would be greatly appreciated.  The system I am using is an Athlon XP 2800+

---

### Post by Rev. Nathan on 2006-02-03
I too am having this problem, although this happened to me out-of-the-box. And I've never install graphic drivers (why would I need to? Running a Radeon 9200... any advantages?)

It stays on for about... 3 seconds? Then the splashscreen I supose fades out, and never returns.

In celestia-gnome, it shows a crash dialog. In Celestia (KDE), it launches KNotify (I ran both in Gnome), so its safe to assume it is something with the celestia-common files.

Output:
The application crashed and caused the signal 6 (SIGBRT)


```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232226624 (LWP 19025)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb693d9b1 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb693f2c9 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb6936f51 in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#8  0xb64a7483 in r200TclFallback () from /usr/lib/dri/r200_dri.so
#9  0xb6540a9c in _tnl_RenderClippedLine () from /usr/lib/dri/r200_dri.so
#10 0xb6535ef6 in _tnl_run_pipeline () from /usr/lib/dri/r200_dri.so
#11 0xb649a7cc in r200ValidateState () from /usr/lib/dri/r200_dri.so
#12 0xb65e9d75 in _mesa_vector4f_print () from /usr/lib/dri/r200_dri.so
#13 0xb652f103 in _mesa_init_varray () from /usr/lib/dri/r200_dri.so
#14 0xb64b98ed in r200VtxfmtInvalidate () from /usr/lib/dri/r200_dri.so
#15 0xb652f103 in _mesa_init_varray () from /usr/lib/dri/r200_dri.so
#16 0xb6b7cb41 in glDrawElements () from /usr/lib/libGL.so.1
#17 0x0819b7fb in Observer::Observer ()
#18 0x00001403 in ?? ()
#19 0x08f61e88 in ?? ()
#20 0x00000000 in ?? ()
#21 0x00000000 in ?? ()
#22 0x00000000 in ?? ()
#23 0x00000000 in ?? ()
#24 0x00000000 in ?? ()
#25 0x00000000 in ?? ()
#26 0x00000001 in ?? ()
#27 0x00000001 in ?? ()
#28 0x00000000 in ?? ()
#29 0x3ff00000 in ?? ()
#30 0x00000001 in ?? ()
#31 0x00000009 in ?? ()
#32 0x00000200 in ?? ()
#33 0x00000004 in ?? ()
#34 0x00000000 in ?? ()
#35 0xbff8e918 in ?? ()
#36 0x00000000 in ?? ()
#37 0xbff8e974 in ?? ()
#38 0xbff8e984 in ?? ()
#39 0xbff8e994 in ?? ()
#40 0xbff8e9a4 in ?? ()
#41 0x00000800 in ?? ()
#42 0xbff8ea64 in ?? ()
#43 0x00001000 in ?? ()
#44 0x00000000 in ?? ()
#45 0x00000000 in ?? ()
#46 0x08f25a08 in ?? ()
#47 0x39800000 in ?? ()
#48 0x3a000000 in ?? ()
#49 0x39800000 in ?? ()
#50 0x3a000000 in ?? ()
#51 0x3f800000 in ?? ()
#52 0x3f800000 in ?? ()
#53 0x08f56978 in ?? ()
#54 0x08f75270 in ?? ()
#55 0x08f52970 in ?? ()
#56 0x08f4e968 in ?? ()
#57 0x00001000 in ?? ()
#58 0x00000800 in ?? ()
#59 0x00000a00 in ?? ()
#60 0x240d3000 in ?? ()
#61 0x00001200 in ?? ()
#62 0x00000002 in ?? ()
#63 0xbff8ea68 in ?? ()
#64 0x00000000 in ?? ()
#65 0x00000000 in ?? ()
#66 0x3f800000 in ?? ()
#67 0x3f800000 in ?? ()
#68 0x00000010 in ?? ()
#69 0x0a1bbbd2 in ?? ()
#70 0x248d3000 in ?? ()
#71 0x3f800000 in ?? ()
#72 0x8a9bbbd2 in ?? ()
#73 0x3f800000 in ?? ()
#74 0x00000000 in ?? ()
#75 0x00000000 in ?? ()
#76 0x00000000 in ?? ()
#77 0x3f800000 in ?? ()
#78 0x3f800000 in ?? ()
#79 0x00000010 in ?? ()
#80 0x3f800000 in ?? ()
#81 0x00000001 in ?? ()
#82 0xbff8e9b8 in ?? ()
#83 0xb65c5bce in _mesa_Bitmap () from /usr/lib/dri/r200_dri.so

```

---

