---
title: "neverwinter nights will not run!"
date: 2009-01-31
forum: Gaming &amp; Leisure
---

### Post by dorhead on 2009-01-31
so im a totally new to ubuntu and gaming on my comp, and my comp in general.ive installed neverwinter nights the linux client and i cant get it to run. i dowloaded the three things i was told to did everything as it said,but when i go to run the ./nwn. it goes full screen for a sec then cuts back to the desktop. please i need help.never played nwn before but i heard it was off the hook.and im i big fan of rpgs and dont want to give up......... also i was having problems installing the eler scrolls: arena. please help!!!!!!!

---

### Post by Naiki Muliaina on 2009-01-31
For 64 bit NWN try this :

[http://gaming.gwos.org/doku.php/guides:64bit:nwn]("http://gaming.gwos.org/doku.php/guides:64bit:nwn")

The top 2 lines of adding a 32 bit layer wont be necessary if you have a 32 bit machine, the rest of the guide should be the same.

---

### Post by dorhead on 2009-01-31
yea i dont know what that means.i  have tried every thing in every forum whatever i could find and it still doesnt work maybe im doin something wrong. wut should i do?

---

### Post by hikaricore on 2009-01-31
So i can't tell if you actually read the info on the link that was posted OR...
You just ignored it cos you didn't want to be bothered to do something complex.

When someone offers you assistance please try out their suggestions in the future.
If you don't wish to do this then no one will be able to help you.

---

### Post by Naiki Muliaina on 2009-01-31
Felt like a quick go on NWN (been a while) and followed the guide. I download it and extract it. I try to run it, i get the window pop with NWN in then it closes. Maybe the same problem?

I ran it from terminal and got the following output. 

Xubuntu 8.10 64 bit, Nvidia 9800GTX, 177 Driver

```
nai@PawsXubucd ~/.Games/nwn   
nai@PawsXubu:~/.Games/nwn$ ./nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6c56891]
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf6da1494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xf7d6b53d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xf7d6678c]
#5 ./lib/libSDL-1.2.so.0 [0xf7d68457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5df66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d407de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d408dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6c5696e]
#2 /usr/lib32/libX11.so.6 [0xf6da0619]
#3 /usr/lib32/libX11.so.6(XMatchVisualInfo+0x40) [0xf6d96530]
#4 ./lib/libSDL-1.2.so.0 [0xf7d6651a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xf7d66a30]
#6 ./lib/libSDL-1.2.so.0 [0xf7d68457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5df66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d407de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d408dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6c56891]
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf6da1494]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xf7d71b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xf7d66c9b]
#5 ./lib/libSDL-1.2.so.0 [0xf7d68457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5df66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d407de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d408dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6c5696e]
#2 /usr/lib32/libX11.so.6 [0xf6da0619]
#3 /usr/lib32/libX11.so.6(XCreateColormap+0x26) [0xf6d751d6]
#4 ./lib/libSDL-1.2.so.0 [0xf7d68584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5df66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d407de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d408dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6c56891]
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf6da1494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xf7d6b80e]
#4 ./lib/libSDL-1.2.so.0 [0xf7d64a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xf7d64b3a]
#6 ./lib/libSDL-1.2.so.0 [0xf7d6860f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5df66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d407de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d408dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6c5696e]
#2 /usr/lib32/libX11.so.6 [0xf6da0619]
#3 /usr/lib32/libX11.so.6(XCreateWindow+0x26) [0xf6d96bc6]
#4 ./lib/libSDL-1.2.so.0 [0xf7d67ff3]
#5 ./lib/libSDL-1.2.so.0 [0xf7d68635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xf7d5df66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xf7d407de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xf7d408dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6c56891]
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf6da1494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xf7d6b53d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xf7d6b8e7]
#5 ./lib/libSDL-1.2.so.0 [0xf7d66368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xf7d67092]
#7 ./lib/libSDL-1.2.so.0 [0xf7d69375]
#8 ./lib/libSDL-1.2.so.0 [0xf7d6952b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xf7d5e7df]
#10 ./nwmain [0x84d1b4d]
#11 ./nwmain(strftime+0x1dfd) [0x80508b5]
#12 ./nwmain [0x805d896]
#13 ./nwmain [0x805adc0]
#14 ./nwmain [0x8059ae5]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6c567c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6c5696e]
#2 /usr/lib32/libX11.so.6 [0xf6da0619]
#3 /usr/lib32/libX11.so.6(XMoveResizeWindow+0x25) [0xf6d74435]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xf7d670f4]
#5 ./lib/libSDL-1.2.so.0 [0xf7d69375]
#6 ./lib/libSDL-1.2.so.0 [0xf7d6952b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xf7d5e7df]
#8 ./nwmain [0x84d1b4d]
#9 ./nwmain(strftime+0x1dfd) [0x80508b5]
#10 ./nwmain [0x805d896]
#11 ./nwmain [0x805adc0]
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7bec685]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
nai@PawsXubu:~/.Games/nwn$ 
```

---

### Post by hikaricore on 2009-01-31
You error output may be related to this problem/fix:

[http://ubuntuforums.org/showpost.php?p=6542863&postcount=2](http://ubuntuforums.org/showpost.php?p=6542863&postcount=2)

---

### Post by Naiki Muliaina on 2009-01-31
I now get a full black screen and the following in terminal ^^

```
nai@PawsXubu:~$ cd ~/.Games/nwn   
nai@PawsXubu:~/.Games/nwn$ ./nwn
Segmentation fault
nai@PawsXubu:~/.Games/nwn$ 
```

[I]Edit

Possible solution : **[http://nwn.bioware.com/forums/viewtopic.html?topic=661884&forum=72]("http://nwn.bioware.com/forums/viewtopic.html?topic=661884&forum=72")**[/I]

---

### Post by oldrocker99 on 2009-01-31
A segmentation fault sometimes means that the OpenGL drivers are not installed. Do other 3D games work?

:guitar:

---

### Post by Naiki Muliaina on 2009-01-31
Yep, Nexuiz, Savage 1 & 2, Second life and Quake are all working on max settings ^^

Lil bit baffled here ^^

---

### Post by oldrocker99 on 2009-01-31
A search of the BioWare forums shows that in most cases, a re-installation of your graphics drivers may solve the problem.

Use lspci to find the brand of your graphics card or chip, and get the latest drivers. Or you can use the somewhat limited 8.10 version of EnvyNG, which does in fact work.

:guitar:

---

### Post by regor210 on 2009-01-31
I tried  Neverwinter Nights Gold using both the Linux client & Wine and we are using Wine. Every thing works fine except the Toolset to make your own modules is a bit buggy.

---

### Post by p_lucio2000 on 2010-07-15
Hi
I'm having the same segmentation fault issue. (yeah, not the SDL parachute one)
But to add strangeness to it, the game works fine when i log in Ravenloft: Prisoners of the Mist, but i can't get past character creation in MZS: Outbreak.
Can anyone help me with it?
Thanks!

---

### Post by p_lucio2000 on 2010-07-16
Yeah... i feel silly.
I missed one of their files. Its alright now.

---

