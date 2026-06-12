---
title: "Xnee Install"
date: 2005-11-24
forum: Desktop Environments
---

### Post by oportista on 2005-11-24
Hi,

First of all i want to say that i'm very newbie about this subject. I downloaded Xnee from [http://www.gnu.org/software/xnee/]("http://www.gnu.org/software/xnee/")
and then i extracted it.
Then i did the ./configure thing and it appeared some errors related to gtk+-2.0 but i download that package and now the compilation is fine!
But when i do:
```
make
sudo make install

```
it appears this:
```

cd . && /bin/sh ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entrando no diret&#243;rio `/home/filipe/Xnee-2.01'
Making all in libxnee
make[2]: Entrando no diret&#243;rio `/home/filipe/Xnee-2.01/libxnee'
Making all in src
make[3]: Entrando no diret&#243;rio `/home/filipe/Xnee-2.01/libxnee/src'
source='xnee.c' object='libxnee_a-xnee.o' libtool=no \
depfile='.deps/libxnee_a-xnee.Po' tmpdepfile='.deps/libxnee_a-xnee.TPo' \
depmode=gcc3 /bin/sh ../.././autotools//depcomp \
gcc -DHAVE_CONFIG_H -I. -I. -I../..    -I../include   -g -DUSE_VERBOSE   -DNO_BUF_VERBOSE  -DNO_XOSD   -g -O2 -c -o libxnee_a-xnee.o `test -f 'xnee.c' || echo './'`xnee.c
xnee.c:41:36: error: X11/extensions/record.h: Arquivo ou diret&#243;rio n&#227;o encontrado
In file included from ../include/libxnee/xnee.h:43,
                 from xnee.c:44:
../include/libxnee/xnee_internal.h:222: error: syntax error before &#8216;XRecordInterceptData&#8217;
../include/libxnee/xnee_internal.h:225: error: syntax error before &#8216;XRecordInterceptData&#8217;
In file included from xnee.c:44:
../include/libxnee/xnee.h:415: error: syntax error before &#8216;XRecordClientSpec&#8217;
../include/libxnee/xnee.h:415: warning: no semicolon at end of struct or union
../include/libxnee/xnee.h:416: warning: data definition has no type or storage class
../include/libxnee/xnee.h:417: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee.h:417: warning: data definition has no type or storage class
../include/libxnee/xnee.h:420: error: syntax error before &#8216;rContext&#8217;
../include/libxnee/xnee.h:420: warning: data definition has no type or storage class
../include/libxnee/xnee.h:425: error: syntax error before &#8216;}&#8217; token
../include/libxnee/xnee.h:425: warning: data definition has no type or storage class
../include/libxnee/xnee.h:523: error: syntax error before &#8216;xnee_recordext_setup&#8217;../include/libxnee/xnee.h:523: warning: no semicolon at end of struct or union
../include/libxnee/xnee.h:543: error: syntax error before &#8216;}&#8217; token
../include/libxnee/xnee.h:543: warning: data definition has no type or storage class
../include/libxnee/xnee.h:568: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee.h:580: error: syntax error before &#8216;*&#8217; token
In file included from ../include/libxnee/print.h:22,
                 from xnee.c:45:
../include/libxnee/xnee_record.h:70: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:84: error: syntax error before &#8216;XRecordInterceptData&#8217;
../include/libxnee/xnee_record.h:96: error: syntax error before &#8216;XRecordInterceptData&#8217;
../include/libxnee/xnee_record.h:106: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:118: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:127: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:138: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:151: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:162: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:174: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_record.h:185: error: syntax error before &#8216;*&#8217; token
In file included from ../include/libxnee/print.h:23,
                 from xnee.c:45:
../include/libxnee/xnee_replay.h:52: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:81: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:94: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:107: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:128: error: syntax error before &#8216;XRecordInterceptData&#8217;
../include/libxnee/xnee_replay.h:150: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:164: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:176: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:198: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_replay.h:210: error: syntax error before &#8216;XRecordInterceptData&#8217;
In file included from ../include/libxnee/print.h:24,
                 from xnee.c:45:
../include/libxnee/print_varargs.h:40: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:45:
../include/libxnee/print.h:36: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:46: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:56: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:66: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:76: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:82: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:91: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:112: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:127: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:141: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:155: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:170: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:184: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:197: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:213: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:231: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:249: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:263: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:277: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:294: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:304: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:308: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:312: error: syntax error before &#8216;*&#8217; token
../include/libxnee/print.h:315: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:46:
../include/libxnee/xnee_dl.h:33: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_dl.h:36: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_dl.h:39: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_dl.h:42: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:48:
../include/libxnee/xnee_setget.h:44: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:57: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:71: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:84: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:97: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:109: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:120: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:131: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:141: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:153: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:163: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:173: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:183: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:195: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:205: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:217: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:221: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:225: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:228: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:232: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:235: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:239: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:244: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:247: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:250: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:253: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:258: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:261: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:264: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:268: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:272: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:275: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:278: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:284: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:288: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:291: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:295: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:301: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:304: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:307: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:310: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:313: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:316: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:319: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:322: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:325: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:328: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:334: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:337: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:340: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:343: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:346: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:349: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:352: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:355: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:372: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:375: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:378: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:381: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:389: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:392: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:395: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:398: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:404: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:407: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:410: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:413: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:420: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:423: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:426: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:430: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:433: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:436: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:439: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:446: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:449: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:452: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:455: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:459: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:462: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:466: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:469: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:475: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:478: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:481: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:487: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:490: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:493: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:496: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:499: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:502: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:505: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:508: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:511: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:526: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:529: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:532: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:535: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:538: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:541: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:544: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:548: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:551: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:555: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_setget.h:558: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:49:
../include/libxnee/xnee_fake.h:36: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_fake.h:48: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_fake.h:64: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_fake.h:77: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_fake.h:92: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_fake.h:97: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_fake.h:104: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_fake.h:107: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:51:
../include/libxnee/xnee_grab.h:30: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_grab.h:33: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_grab.h:43: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_grab.h:46: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_grab.h:70: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_grab.h:73: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_grab.h:76: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:52:
../include/libxnee/xnee_km.h:29: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_km.h:41: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_km.h:45: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_km.h:50: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_km.h:55: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_km.h:58: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_km.h:62: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:53:
../include/libxnee/xnee_resolution.h:33: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:36: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:39: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:42: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:45: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:48: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:51: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:60: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:63: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:66: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:69: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:72: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:75: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:78: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:81: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:84: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resolution.h:87: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:54:
../include/libxnee/xnee_resource.h:88: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:98: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:105: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:108: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:110: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:112: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:114: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:116: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:118: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:120: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:122: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:124: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:126: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:130: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:133: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:136: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:139: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:142: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:145: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:148: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:151: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:154: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:157: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:160: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:163: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:166: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:169: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:172: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:175: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:178: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:181: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:184: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:187: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:190: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_resource.h:193: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:55:
../include/libxnee/xnee_callback.h:44: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_callback.h:72: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:56:
../include/libxnee/xnee_range.h:74: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_range.h:92: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_range.h:112: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_range.h:124: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_range.h:136: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_range.h:146: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_range.h:151: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:58:
../include/libxnee/xnee_session.h:31: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:43: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:55: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:66: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:76: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:84: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:88: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:106: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_session.h:115: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:60:
../include/libxnee/xnee_display.h:34: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_display.h:45: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_display.h:58: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_display.h:70: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_display.h:83: error: syntax error before &#8216;xnee_data&#8217;
../include/libxnee/xnee_display.h:95: error: syntax error before &#8216;xnee_data&#8217;
In file included from xnee.c:61:
../include/libxnee/xnee_utils.h:40: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_utils.h:45: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_utils.h:73: error: syntax error before &#8216;*&#8217; token
In file included from xnee.c:62:
../include/libxnee/xnee_alloc.h:37: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_alloc.h:38: warning: data definition has no type or storage class
../include/libxnee/xnee_alloc.h:48: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_alloc.h:58: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_alloc.h:59: warning: data definition has no type or storage class
../include/libxnee/xnee_alloc.h:69: error: syntax error before &#8216;*&#8217; token
../include/libxnee/xnee_alloc.h:81: error: syntax error before &#8216;*&#8217; token
xnee.c:89: error: syntax error before &#8216;*&#8217; token
xnee.c: In function &#8216;xnee_start&#8217;:
xnee.c:95: error: &#8216;xd&#8217; undeclared (first use in this function)
xnee.c:95: error: (Each undeclared identifier is reported only once
xnee.c:95: error: for each function it appears in.)
make[3]: ** [libxnee_a-xnee.o] Erro 1
make[3]: Saindo do diret&#243;rio `/home/filipe/Xnee-2.01/libxnee/src'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diret&#243;rio `/home/filipe/Xnee-2.01/libxnee'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diret&#243;rio `/home/filipe/Xnee-2.01'
make: ** [all] Erro 2

```

can u help me? this program is important for me.. i really need this because it's the reason why i'm still using windows.
thks for your help.

---

### Post by Xian on 2005-11-24
The package is available for use in Ubuntu: [xnee_1.08-3](http://archive.ubuntu.com/ubuntu/pool/universe/x/xnee/xnee_1.08-3_i386.deb).

Download that file & install locally or enable the universe repos and use Synaptic.
From the wiki: [Synaptic How-To](https://wiki.ubuntu.com//SynapticHowto).

---

### Post by oportista on 2005-11-24
That is like an auto-installer right? i only have to make
dkpg --install file.deb right?

I did that but now where is the program? i found one in home\bin\ but i double clicked and did nothing. Am I doing something wrong?

---

### Post by oportista on 2005-11-25
How do i run the program? It's a stupid question but i'm not really seeing what i must do...

---

### Post by oportista on 2005-11-25
Hi again,

I managed to run the program but now i don't have a clue on how to start recording my mouse movements and then play it back in a loop.

hope u can help me and sorry for this monologue.

---

