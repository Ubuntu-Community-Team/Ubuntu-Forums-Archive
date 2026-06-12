---
title: "build quake 1 from source"
date: 2010-07-27
forum: Gaming &amp; Leisure
---

### Post by darkcodemonkey on 2010-07-27
I'm trying to build the Quake 1 engine from the source code, but can not get it to work. #1 the reason I'm doing this is so I can edit the source for my need. #2 this is what I do and what comes up.

```

ethan@ethan-desktop:~$ cd '/home/ethan/Desktop/WinQuake' 
ethan@ethan-desktop:~/Desktop/WinQuake$ make
make targets BUILDDIR=debugi386-glibc CFLAGS="-Dstricmp=strcasecmp -g"
make[1]: Entering directory `/home/ethan/Desktop/WinQuake'
make[1]: *** No rule to make target `/grog/Projects/WinQuake/cl_demo.c', needed by `debugi386-glibc/squake/cl_demo.o'.  Stop.
make[1]: Leaving directory `/home/ethan/Desktop/WinQuake'
make: *** [build_debug] Error 2
ethan@ethan-desktop:~/Desktop/WinQuake$ 

```

If anyone could help me it would be most appreciated. Thanks in advanced.

BTW: I'm on Ubuntu Jaunty 9.04

---

### Post by 2Karl on 2010-07-28
First thing to check is that you have all the required dependencies installed. Also, there's usually (but not always) a configure script that should be run prior to the make command (try ./configure). Presently it seems the makefile is pointing at the wrong place (/grog/Projects/WinQuake/ instead of /home/ethan/Desktop/WinQuake/)

The fact that it's called "winquake" doesn't fill me with hope that it will work on linux, mind you.

---

### Post by darkcodemonkey on 2010-07-28
Well, it is called winquake, but there is a makefile for linux in the folder. also, there is no configure file, I tried that before I saw the makefile. After seeing your post, I changed the makefile so that it would go to the right dir and it looks to be compiling correctly... until this appears.

```

/usr/bin/gcc -O -Dstricmp=strcasecmp -g -o debugi386-glibc/squake/vid_svgalib.o -c /home/ethan/Desktop/WinQuake/vid_svgalib.c
/home/ethan/Desktop/WinQuake/vid_svgalib.c:28:20: error: asm/io.h: No such file or directory
/home/ethan/Desktop/WinQuake/vid_svgalib.c:30:17: error: vga.h: No such file or directory
/home/ethan/Desktop/WinQuake/vid_svgalib.c:31:25: error: vgakeyboard.h: No such file or directory
/home/ethan/Desktop/WinQuake/vid_svgalib.c:32:22: error: vgamouse.h: No such file or directory
/home/ethan/Desktop/WinQuake/vid_svgalib.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/ethan/Desktop/WinQuake/vid_svgalib.c:55: error: ‘MOUSE_MICROSOFT’ undeclared here (not in a function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:56: error: ‘MOUSE_MOUSESYSTEMS’ undeclared here (not in a function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:57: error: ‘MOUSE_MMSERIES’ undeclared here (not in a function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:58: error: ‘MOUSE_LOGITECH’ undeclared here (not in a function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:59: error: ‘MOUSE_BUSMOUSE’ undeclared here (not in a function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:60: error: ‘MOUSE_PS2’ undeclared here (not in a function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:75: error: ‘MOUSE_DEFAULTSAMPLERATE’ undeclared here (not in a function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:75: warning: initialization makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:75: error: initializer element is not constant
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_DescribeMode_f’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:268: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:268: error: (Each undeclared identifier is reported only once
/home/ethan/Desktop/WinQuake/vid_svgalib.c:268: error: for each function it appears in.)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:268: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:270: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:270: error: ‘struct <anonymous>’ has no member named ‘height’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:271: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:274: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:274: error: invalid operands to binary << (have ‘struct <anonymous> *’ and ‘int’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_DescribeModes_f’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:282: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:282: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:283: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:283: error: ‘struct <anonymous>’ has no member named ‘height’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:284: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:287: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:287: error: invalid operands to binary << (have ‘struct <anonymous> *’ and ‘int’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_NumModes’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:301: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:301: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_Debug_f’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:314: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:314: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:314: error: invalid operands to binary * (have ‘struct <anonymous> *’ and ‘int’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_InitModes’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:328: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:328: error: ‘vga_modeinfo’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:328: error: invalid operands to binary * (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:328: warning: passing argument 1 of ‘Z_Malloc’ makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:332: warning: passing argument 2 of ‘Q_memcpy’ makes pointer from integer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:332: warning: passing argument 3 of ‘Q_memcpy’ makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:334: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:341: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:341: warning: comparison between pointer and integer
/home/ethan/Desktop/WinQuake/vid_svgalib.c:341: error: ‘struct <anonymous>’ has no member named ‘colors’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:341: warning: comparison between pointer and integer
/home/ethan/Desktop/WinQuake/vid_svgalib.c:342: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘get_mode’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:358: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:358: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:361: error: ‘G320x200x256’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:361: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:367: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:369: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:369: warning: comparison between pointer and integer
/home/ethan/Desktop/WinQuake/vid_svgalib.c:370: error: ‘struct <anonymous>’ has no member named ‘height’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:370: warning: comparison between pointer and integer
/home/ethan/Desktop/WinQuake/vid_svgalib.c:371: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:371: warning: comparison between pointer and integer
/home/ethan/Desktop/WinQuake/vid_svgalib.c:379: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘keyhandler’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:422: error: ‘KEY_EVENTPRESS’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:422: warning: comparison between pointer and integer
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_Shutdown’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:435: error: ‘TEXT’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_SetMode’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:476: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:476: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:489: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:489: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:490: error: ‘struct <anonymous>’ has no member named ‘height’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:490: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:492: error: ‘struct <anonymous>’ has no member named ‘width’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:492: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:493: error: ‘struct <anonymous>’ has no member named ‘height’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:493: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:494: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:495: error: ‘struct <anonymous>’ has no member named ‘linewidth’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:495: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:496: error: ‘struct <anonymous>’ has no member named ‘linewidth’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:496: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:498: error: ‘struct <anonymous>’ has no member named ‘linewidth’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:498: error: invalid operands to binary * (have ‘struct <anonymous> *’ and ‘int’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:498: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c:499: error: ‘struct <anonymous>’ has no member named ‘linewidth’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:499: error: invalid operands to binary * (have ‘struct <anonymous> *’ and ‘int’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:499: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_Init’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:600: error: ‘G320x200x256’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:600: warning: assignment makes integer from pointer without a cast
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘IN_Commands’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:894: error: ‘MOUSE_LEFTBUTTON’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:894: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:895: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:897: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:898: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:901: error: ‘MOUSE_RIGHTBUTTON’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:901: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:902: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:904: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:905: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:908: error: ‘MOUSE_MIDDLEBUTTON’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:908: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:909: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:911: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:912: error: invalid operands to binary & (have ‘int’ and ‘struct <anonymous> *’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c: In function ‘VID_ModeInfo’:
/home/ethan/Desktop/WinQuake/vid_svgalib.c:995: error: ‘modes’ undeclared (first use in this function)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:995: error: ‘struct <anonymous>’ has no member named ‘bytesperpixel’
/home/ethan/Desktop/WinQuake/vid_svgalib.c:995: error: invalid operands to binary * (have ‘struct <anonymous> *’ and ‘int’)
/home/ethan/Desktop/WinQuake/vid_svgalib.c:995: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘struct <anonymous> *’
make[1]: *** [debugi386-glibc/squake/vid_svgalib.o] Error 1
make[1]: Leaving directory `/home/ethan/Desktop/WinQuake'
make: *** [build_debug] Error 2
ethan@ethan-desktop:~/Desktop/WinQuake$ 

```

now what? Is it me, am I missing something that I should have noticed earlier, or is it the code?

Thanks so far for the help.

---

### Post by 2Karl on 2010-07-28
The file vid_svgalib.c is looking for some header files and not finding them. Namely: asm/io.h, vga.h, vgakeyboard.h and vgamouse.h.

This may be down to missing dependencies (check the docs to make sure you have all the necessary packages installed - you'll need the -dev variants of any required), or even down to something as simple as the version of the compiler you are using.

Have you tried some of the other Quake sourceports? Dark Places is a good one [http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/) you may find it more compliant.

---

