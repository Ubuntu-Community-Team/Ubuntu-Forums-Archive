---
title: "How to run NWN?"
date: 2009-03-09
forum: Gaming &amp; Leisure
---

### Post by wolfyking2 on 2009-03-09
Ok, I got the resources, binaries and all for the original NWN.  I want to run it, so in the terminal I type ./nwn.  Well it says there's no such file or directory. Ookk, I guess it's time to chmod it.  Well when I try to cd to the home/user/games...it says there is no file or directory.  What is up with that?  I did it with the documents...same thing.  So I'll just manually run nwn (executable text file) I double click it, press run...and nothing happens.  So I try it in the terminal.  Terminal pops up for a second, and then goes away.  I REALLY wanna play this game, so could someone help

@hikaricore When I asked for the free linux NWN client...I didn't mean it in the piracy sort of way.  I just wanted to know, because everyone was saying it was free.  And I'm talking about the resources too.  It turns out they are free, and they are.  So, I wasn't trying to be 'illegal' or anything :).

I got the cd thing to work, but when I typed in ./nwn this is what I got

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb797c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb797c8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7ae61bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d1353d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d0e78c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d10457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d05f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ce87de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ce88dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ba4450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb797c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb797c81e]
#2 /usr/lib/libX11.so.6 [0xb7ae5518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7adbf70]
#4 ./lib/libSDL-1.2.so.0 [0xb7d0e51a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d0ea30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d10457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d05f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ce87de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ce88dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ba4450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb797c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb797c8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7ae61bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7d19b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d0ec9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d10457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d05f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ce87de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ce88dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ba4450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb797c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb797c81e]
#2 /usr/lib/libX11.so.6 [0xb7ae5518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7abbe76]
#4 ./lib/libSDL-1.2.so.0 [0xb7d10584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d05f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ce87de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ce88dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ba4450]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb797c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb797c8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7ae61bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d1380e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d0ca89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d0cb3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d1060f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d05f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ce87de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ce88dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ba4450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb797c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb797c81e]
#2 /usr/lib/libX11.so.6 [0xb7ae5518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7adc616]
#4 ./lib/libSDL-1.2.so.0 [0xb7d0fff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d10635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d05f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7ce87de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7ce88dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ba4450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
*** glibc detected *** ./nwmain: double free or corruption (!prev): 0x0e0ddb98 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7bf9a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7bfd4f0]
./nwmain(__builtin_delete+0x22)[0x85f2ba6]
./nwmain[0x85a35d8]
./nwmain[0x85986c0]
./nwmain[0x8586769]
./nwmain[0x858ad85]
./nwmain[0x8059108]
./nwmain(SDL_SetVideoMode+0x45f)[0x804fb57]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7ba4450]
./nwmain(AIL_WAV_info+0x39)[0x804f851]
======= Memory map: ========
08048000-0862c000 r-xp 00000000 08:01 417010     /home/user/Documents/nwn/nwmain
0862c000-087ac000 rwxp 005e3000 08:01 417010     /home/user/Documents/nwn/nwmain
087ac000-0e0fb000 rwxp 087ac000 00:00 0          [heap]
b70cc000-b7147000 rwxp b70cc000 00:00 0 
b7147000-b714e000 r-xp 00000000 08:01 53200      /usr/lib/libXrender.so.1.3.0
b714e000-b714f000 rwxp 00007000 08:01 53200      /usr/lib/libXrender.so.1.3.0
b714f000-b7157000 r-xp 00000000 08:01 53237      /usr/lib/libXcursor.so.1.0.2
b7157000-b7158000 rwxp 00007000 08:01 53237      /usr/lib/libXcursor.so.1.0.2
b7158000-b7159000 ---p b7158000 00:00 0 
b7159000-b795b000 rwxp b7159000 00:00 0 
b795b000-b795f000 r-xp 00000000 08:01 52599      /usr/lib/libXdmcp.so.6.0.0
b795f000-b7960000 rwxp 00003000 08:01 52599      /usr/lib/libXdmcp.so.6.0.0
b7960000-b7962000 r-xp 00000000 08:01 52597      /usr/lib/libXau.so.6.0.0
b7962000-b7963000 rwxp 00001000 08:01 52597      /usr/lib/libXau.so.6.0.0
b7963000-b7964000 rwxp b7963000 00:00 0 
b7964000-b797b000 r-xp 00000000 08:01 52601      /usr/lib/libxcb.so.1.0.0
b797b000-b797c000 rwxp 00016000 08:01 52601      /usr/lib/libxcb.so.1.0.0
b797c000-b797d000 r-xp 00000000 08:01 52603      /usr/lib/libxcb-xlib.so.0.0.0
b797d000-b797e000 rwxp 00000000 08:01 52603      /usr/lib/libxcb-xlib.so.0.0.0
b797e000-b7988000 r-xp 00000000 08:01 677319     /lib/libgcc_s.so.1
b7988000-b7989000 rwxp 0000a000 08:01 677319     /lib/libgcc_s.so.1
b7989000-b7a71000 r-xp 00000000 08:01 49931      /usr/lib/libstdc++.so.6.0.9
b7a71000-b7a74000 r-xp 000e8000 08:01 49931      /usr/lib/libstdc++.so.6.0.9
b7a74000-b7a76000 rwxp 000eb000 08:01 49931      /usr/lib/libstdc++.so.6.0.9
b7a76000-b7a7c000 rwxp b7a76000 00:00 0 
b7a7c000-b7a85000 r-xp 00000000 08:01 52651      /usr/lib/libdrm.so.2.3.0
b7a85000-b7a86000 rwxp 00008000 08:01 52651      /usr/lib/libdrm.so.2.3.0
b7a86000-b7a87000 rwxp b7a86000 00:00 0 
b7a87000-b7a89000 r-xp 00000000 08:01 677307     /lib/tls/i686/cmov/libdl-2.7.so
b7a89000-b7a8b000 rwxp 00001000 08:01 677307     /lib/tls/i686/cmov/libdl-2.7.so
b7a8b000-b7a8f000 r-xp 00000000 08:01 53233      /usr/lib/libXfixes.so.3.1.0
b7a8f000-b7a90000 rwxp 00003000 08:01 53233      /usr/lib/libXfixes.so.3.1.0
b7a90000-b7a92000 r-xp 00000000 08:01 53239      /usr/lib/libXdamage.so.1.1.0
b7a92000-b7a93000 rwxp 00001000 08:01 53239      /usr/lib/libXdamage.so.1.1.0
b7a93000-b7a97000 r-xp 00000000 08:01 53472      /usr/lib/libXxf86vm.so.1.0.0
b7a97000-b7a98000 rwxp 00003000 08:01 53472      /usr/lib/libXxf86vm.so.1.0.0
b7a98000-b7aa5000 r-xp 00000000 08:01 52613      /usr/lib/libXext.so.6.4.0
b7aa5000-b7aa6000 rwxp 0000d000 08:01 52613      /usr/lib/libXext.so.6.4.0
b7aa6000-b7b8a000 r-xp 00000000 08:01 52605      /usr/lib/libX11.so.6.2.0
b7b8a000-b7b8d000 rwxp 000e4000 08:01 52605      /usr/lib/libX11.so.6.2.0
b7b8d000-b7b8e000 rwxp b7b8d000 00:00 0 
b7b8e000-b7cd7000 r-xp 00000000 08:01 677304     /lib/tls/i686/cmov/libc-2.7.so
b7cd7000-b7cd8000 r-xp 00149000 08:01 677304     /lib/tls/i686/cmov/libc-2.7.so
b7cd8000-b7cda000 rwxp 0014a000 08:01 677304     /lib/tls/i686/cmov/libc-2.7.so
b7cda000-b7cdd000 rwxp b7cda000 00:00 0 
b7cdd000-b7d31000 r-xp 00000000 08:01 417019     /home/user/Documents/nwn/lib/libSDL-1.2.so.0.0.5
b7d31000-b7d33000 rwxp 00053000 08:01 417019     /home/user/Documents/nwn/lib/libSDL-1.2.so.0.0.5
b7d33000-b7d4e000 rwxp b7d33000 00:00 0 
b7d4e000-b7db3000 r-xp 00000000 08:01 417027     /home/user/Documents/nwn/miles/libmss.so.6.5.2
b7db3000-b7dbe000 rwxp 00064000 08:01 417027     /home/user/Documents/nwn/miles/libmss.so.6.5.2
b7dbe000-b7dc2000 rwxp b7dbe000 00:00 0 
b7dc2000-b7e44000 r-xp 00000000 08:01 55115      /usr/lib/libGLU.so.1.3.070002
b7e44000-b7e45000 rwxp 00081000 08:01 55115      /usr/lib/libGLU.so.1.3.070002
b7e45000-b7ea0000 r-xp 00000000 08:01 53474      /usr/lib/libGL.so.1.2
b7ea0000-b7ea6000 rwxp 0005b000 08:01 53474      /usr/lib/libGL.so.1.2
b7ea6000-b7ea8000 rwxp b7ea6000 00:00 0 
b7ea8000-b7ebc000 r-xp 00000000 08:01 677318     /lib/tls/i686/cmov/libpthread-2.7.so
b7ebc000-b7ebe000 rwxp 00013000 08:01 677318     /lib/tls/i686/cmov/libpthread-2.7.so
b7ebe000-b7ec0000 rwxp b7ebe000 00:00 0 
b7ec0000-b7ee3000 r-xp 00000000 08:01 677308     /lib/tls/i686/cmov/libm-2.7.so
b7ee3000-b7ee5000 rwxp 00023000 08:01 677308     /lib/tls/i686/cmov/libm-2.7.so
b7ef6000-b7ef8000 rwxp b7ef6000 00:00 0 
b7ef8000-b7ef9000 r-xp b7ef8000 00:00 0          [vdso]
b7ef9000-b7f13000 r-xp 00000000 08:01 1126081    /lib/ld-2.7.so
b7f13000-b7f15000 rwxp 00019000 08:01 1126081    /lib/ld-2.7.so
bfd5c000-bfd71000 rw-p bffeb000 00:00 0          [stack]
Aborted
user@ubuntu:~/Documents/nwn$ 

I have no idea what it means.  I mean, I got the demo working in wine, the game wasn't laggy at all.  Now the game wont even start?  I need help :(

---

### Post by Monkey_Magic on 2009-03-09
So when you're in terminal, and you cd into the directory where you installed nwn, and run ./nwn what does it say exactly? What happens when you run ./fixinstall? Does it say anything?

I installed nwn today by following ['this guide',](http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72) except using the ['latest patch'](http://nwn.bioware.com/support/patch_linuxhotu169.html) instad of the 165 one. It should be the same for you, just substitude extracting the dvd stuff to just using the downloaded files. I then had to do this fix because of a crash:

[quote="hikaricore"]
Easy fix:

Open nwn (in the NWN folder) in a text editor and change:

Code:

export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

to

Code:

export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

source - [http://www.linuxgrotto.com/2008/11/neverwinter-nights-diamond-on-xubuntu.html](http://www.linuxgrotto.com/2008/11/neverwinter-nights-diamond-on-xubuntu.html)[/quote]

Try follow the guide and also see what it says when you do ./fixinstall

---

### Post by wolfyking2 on 2009-03-09
Ok, ./fixinstall said

Checking for required files

PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
PASSED: override directory exists
PASSED: miles directory exists
PASSED: nwm directory exists
PASSED: chitin.key exists
PASSED: dialog.tlk exists
PASSED: nwmain exists
PASSED: patch.key exists

Fixing case

ambient
.........
data
.............................
dmvault
..
hak
.
localvault
.......................
music
...............................................................................
override
..
portraits
.

Checking for problem files


Checking for permissions

PASSED: nwn.ini is writable
PASSED: saves is writable
PASSED: localvault is writable
PASSED: tempclient is writable
PASSED: dmvault is writable
PASSED: /home/user/Documents/nwn is writable

You are ready to run Neverwinter Nights.

but when I run ./nwn it gives me the same error!  But how would I open the nwn folder with a text editor (sorry, I don't know how >.<) because I haven't done that part yet.

---

### Post by wolfyking2 on 2009-03-09
(sorry I'm posting so much in a little time) Ok, I got nwn to open in a text editor, changed the SDL_library thing to the one it says in the quote, and I got a new error this time!  A very short one too, this is what it said:

segmentation fault

So how would I fix this?

---

### Post by wolfyking2 on 2009-03-09
(bump) please help D:

---

### Post by hikaricore on 2009-03-09
You really need to wait 24-48 hours before bumping..
I don't think this is the first time you've been warned.

---

### Post by wolfyking2 on 2009-03-09
aye, didn't know that sorry.

---

### Post by wolfyking2 on 2009-03-10
Bump...

---

### Post by wolfyking2 on 2009-03-15
bump!

---

### Post by Perfect Storm on 2009-03-15
I don't know if this can help you; [http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

---

### Post by wolfyking2 on 2009-03-15
I'll check it out, had to remove the client for a while because it was taking up space and wasn't getting any help on it.  

P.S. is your avatar a person from ant bully?

---

### Post by myrtle1908 on 2009-03-17
Could be a problem with the libSDL that ships with NWN.  Have you tried editing the nwn startup script ie. do what it suggests re. remove './lib'?

Here is mine which works fine...

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@
```

---

### Post by wolfyking2 on 2009-03-17
nvm about this, I'll just wait till I get a windoze box :(

---

### Post by eragon100 on 2009-03-17
It's actually very, very simple, or atleast it was for me. Open the "nwn" folder, and simply delete the "lib" (or "libs") directory from it. 
Now just run the game by double-clicking on nwn as you would do normally, and it will run. :wink:

---

### Post by hikaricore on 2009-03-17
Either wolfy has a different problem than we all believe or is not following instuctions.

Best to just let this thread die.

---

### Post by ToniMG on 2009-03-27
Hi, If you haven't checked the NWN Linux forums, there are lots of answers.
Here's the link to the latest install directions:

[http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72)

Hope it helps.
Toni

ps I got the game to boot but the video is totally distorted. *sigh  Still haven't figured that one out so if you run into a fix for it, let me know.

---

### Post by wolfyking2 on 2009-03-27
heh, I feel stupid.  I fixed it, i just got more space on my hard disk (deleted things) then downloaded the client again and updated it.  It was a problem in that script taking out the .lib thing.  There was 2 periods instead of 1... =.=  1 period was blocking me from playing NWN >.< oh well, you live and ya learn.  

P.S. this game is fun :D

---

