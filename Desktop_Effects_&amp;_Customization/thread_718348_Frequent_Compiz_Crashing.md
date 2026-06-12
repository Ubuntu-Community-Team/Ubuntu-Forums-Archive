---
title: "Frequent Compiz Crashing"
date: 2008-03-08
forum: Desktop Effects &amp; Customization
---

### Post by Locutus_of_Borg on 2008-03-08
This just started happening today or last night some time.  I haven't done any updates or changed any significant settings.

Here is the terminal readout when it happens:
```
Thread 1 (Thread -1213606224 (LWP 5795)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c826b3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c27b8b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7f5b962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfbec838 in ?? ()
#5  0xb7f5ba94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfbef95e in ?? ()
#7  0x000016a3 in ?? ()
#8  0x000016a3 in ?? ()
#9  0x000016a3 in ?? ()
#10 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c826b3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c27b8b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7f5b962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfbec838 in ?? ()
#5  0xb7f5ba94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfbef95e in ?? ()
#7  0x000016a3 in ?? ()
#8  0x000016a3 in ?? ()
#9  0x000016a3 in ?? ()
#10 0x00000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 5795
```


The only thing I have done is logged into KDE4 and adjusted the appearance and effects. But I don't see how that might have caused this.

Any advice is appreciated.

---

### Post by BooBooNTZU on 2008-03-08
I think some versions of Compiz are compiled for GNOME only and some are for KDE only. If you want to use it with KDE and GNOME i think you have to compile it yourself and specify what options you want. 

I could be wrong. It's just an idea.

---

### Post by Locutus_of_Borg on 2008-03-08
It had been running fine with GNOME KDE3 and 4 for a long time, though.


I am pretty sure it's something to do with AWN as it seems to crash when I hover my pointer over an icon in the dock.  The two had been coinciding with no problems for several weeks now, though.

I did change some settings in ccsm, but nothing serious, just changed the animations to random, and fiddled with the screensaver...

I guess I'll try changing those back, and seeing if maybe I accidentally did something else.

---

### Post by Locutus_of_Borg on 2008-03-08
It was the random effects setting in Animations that did it.


Any ideas why?

I tried turning off the effects for tooltips to see if that might help, but it still crashes.

---

