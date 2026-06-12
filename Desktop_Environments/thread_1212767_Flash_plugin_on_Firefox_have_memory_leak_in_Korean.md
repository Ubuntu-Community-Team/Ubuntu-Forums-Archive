---
title: "Flash plugin on Firefox have memory leak in Korean locale"
date: 2009-07-14
forum: Desktop Environments
---

### Post by narusas on 2009-07-14
1. open terminal and set locale to Korean, and launch firefox

~$ export LANG=ko_KR.UTF-8
~$ export LC_ALL=ko_KR.UTF-8
~$ firefox

2. visit [http://www.betman.co.kr](http://www.betman.co.kr) or [http://traffic.local.naver.com/Traffic_browser/SubWayLine/](http://traffic.local.naver.com/Traffic_browser/SubWayLine/)

3. wait to crash( with 1GB Ram, under 1 minutes)
```

firefox: Fatal IO error 12 (Cannot allocate memory) on X server :0.0.
Program received signal SIGSEGV, Segmentation fault.

```

Test Env.
HW
 * D945GSEJT (Atom N270 board)
 * Over 10 General x86 PC(Core, Core 2 duo, etc)

OS
 * ubuntu 8.04
 * ubuntu 8.10
 * ubuntu 9.04
 * xubuntu 8.10
 * xubuntu 9.04

Web browser
 * Firefox 3.0
 * Firefox 3.5
 * kazehakase with Gecko 0.5.4
 * epiphany2.26.1
 * konquerer

Flash Plugin
 * Adobe flash plugin 10
 * Adobe flash plugin 10 debugger version
 * Adobe flash plugin 9

 Actual Results:

 Expected Results:

 Workaround (if any):

with pmap(Process mapping), I found there is memory leak
```

pmap 5304 <- firefox pid

5304: /usr/lib/firefox-3.0.11/firefox --display=:0
08048000 28K r-x-- /usr/lib/firefox-3.0.11/firefox
0804f000 4K r---- /usr/lib/firefox-3.0.11/firefox
08050000 4K rw--- /usr/lib/firefox-3.0.11/firefox
09570000 79932K rw--- [ anon ]
4750b000 1568K r---- /usr/share/fonts/truetype/LexiGulim090423.ttf
47693000 1568K r---- /usr/share/fonts/truetype/LexiGulim090423.ttf
4781b000 1568K r---- /usr/share/fonts/truetype/LexiGulim090423.ttf
479a3000 1568K r---- /usr/share/fonts/truetype/LexiGulim090423.ttf
47b2b000 1568K r---- /usr/share/fonts/truetype/LexiGulim090423.ttf
47cb3000 1568K r---- /usr/share/fonts/truetype/LexiGulim090423.ttf
.... hundreds line of /usr/share/fonts/truetype/LexiGulim090423.ttf

```

and it increase very quick

If I set English or japanese locale, there is only one (One time load) /usr/share/fonts/truetype/LexiGulim090423.ttf

Font name is setup by /etc/fonts/conf.d/69-language-selector-ko-kr.conf
I try to change font to other korean fonts, or English fonts, etc but firefox is crased

So I launch firefox with debugger, and at crash point, there is many threads

Flash thread backtrace
```

#0 0xb804c9f0 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#1 0xb18f50a8 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#2 0xb18f5332 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#3 0xb18f53c1 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#4 0xb176c50d in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#5 0xb804b50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6 0xb7ea0a0e in clone () from /lib/tls/i686/cmov/libc.so.6

```

Firefox main thread backtrace
```

#0 0xb8088430 in __kernel_vsyscall ()
#1 0xb7e9d276 in munmap () from /lib/tls/i686/cmov/libc.so.6
#2 0xb1deaf74 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#3 0xb1deadc0 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#4 0xb18fa81d in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#5 0xb176b105 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#6 0xb1754550 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#7 0xb7dedd89 in exit () from /lib/tls/i686/cmov/libc.so.6
#8 0xb67051d5 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#9 0xb6b46062 in _XIOError () from /usr/lib/libX11.so.6
#10 0xb6b4d3f8 in _XGetXCBBuffer () from /usr/lib/libX11.so.6
#11 0xb6b4d5fd in ?? () from /usr/lib/libX11.so.6
#12 0xb6b4e37e in _XReply () from /usr/lib/libX11.so.6
#13 0xb6b2a4f9 in XGetImage () from /usr/lib/libX11.so.6
#14 0xb6b2a779 in XGetSubImage () from /usr/lib/libX11.so.6
#15 0xb6700ff2 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#16 0xb66cb9f9 in gdk_drawable_copy_to_image () from /usr/lib/libgdk-x11-2.0.so.0
#17 0xb66cb9f9 in gdk_drawable_copy_to_image () from /usr/lib/libgdk-x11-2.0.so.0
#18 0xb176a3c3 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#19 0xb175e0c5 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#20 0xb1754590 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#21 0xb1759124 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#22 0xb7871887 in ?? () from /usr/lib/xulrunner-1.9.0.11/libxul.so
#23 0xb7429aff in ?? () from /usr/lib/xulrunner-1.9.0.11/libxul.so
#24 0xb7a69680 in ?? () from /usr/lib/xulrunner-1.9.0.11/libxul.so
#25 0xb7a5adcb in ?? () from /usr/lib/xulrunner-1.9.0.11/libxul.so
#26 0xb7a5b04a in ?? () from /usr/lib/xulrunner-1.9.0.11/libxul.so
...

```

---

### Post by csabo2 on 2009-07-14
nice find!

---

