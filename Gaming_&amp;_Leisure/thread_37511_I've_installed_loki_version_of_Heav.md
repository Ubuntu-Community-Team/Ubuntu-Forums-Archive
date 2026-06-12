---
title: "I've installed loki version of Heav"
date: 2005-05-27
forum: Gaming &amp; Leisure
---

### Post by Poul on 2005-05-27
I've installed loki version of heavy metal fakk 2 but it doesn't want to start. 
Other games like quake3, heroes 3 (fullscreen doesnt work), tux racer or soldier of fortune work perfectly.]
It gives me this output in the console

```
paul@paul:~$ fakk2
Heavy Metal: FAKK2 1.02 linux-i386 Oct  9 2001
----- FS_Startup -----
Current search path:
/home/paul/.loki/fakk2/fakk
/usr/local/games/fakk2/fakk/pak3.pk3 (21 files)
/usr/local/games/fakk2/fakk/pak2.pk3 (13 files)
/usr/local/games/fakk2/fakk/pak1.pk3 (2532 files)
/usr/local/games/fakk2/fakk/pak0.pk3 (9610 files)
/usr/local/games/fakk2/fakk
/usr/local/games/fakk2/fakk/pak3.pk3 (21 files)
/usr/local/games/fakk2/fakk/pak2.pk3 (13 files)
/usr/local/games/fakk2/fakk/pak1.pk3 (2532 files)
/usr/local/games/fakk2/fakk/pak0.pk3 (9610 files)
/usr/local/games/fakk2/fakk

----------------------
----- CL_Shutdown -----
-----------------------

BUG! (Segmentation Fault)  Going down hard...
Heavy Metal: FAKK2
Built with glibc-2.1 on x86
Stack dump:
{
fakk2(loki_printstack+0x3f)[0x8181443]
fakk2[0x818162b]
fakk2[0x81060a4]
[0xffffe420]
/usr/lib/libz.so.1(inflate+0x122f)[0x4d64b1fd]
fakk2(unzReadCurrentFile+0x15c)[0x80e72f4]
fakk2(FS_Read+0xfa)[0x80d4a42]
fakk2(FS_ReadFileEx+0x1e7)[0x80d4fab]
fakk2(FS_ReadFile+0x18)[0x80d5044]
fakk2[0x80d6460]
fakk2(FS_InitFilesystem+0x62)[0x80d65ca]
fakk2(Com_Init+0x48)[0x80d1b6c]
fakk2(main+0x25a)[0x8106416]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xf8)[0x4d42a8c8]
fakk2(XMapRaised+0x35)[0x808e5e1]
}
Please send a full bug report,
along with the contents of autosave to: support@lokigames.com
Unable to execute loki_qagent - exiting
```

BTW: Help ;-)

---

