---
title: "Compiling Generator Error"
date: 2005-02-02
forum: Gaming &amp; Leisure
---

### Post by Ste on 2005-02-02
The megadrive emulator, had it running before but not it won't compile. Configures fine but when makeing or installing I get the following erros.
Can anybody shed some light on it ?

```
cpu68k-5.c:3346: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_926a':
cpu68k-5.c:3358: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_927a':
cpu68k-5.c:3370: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_928a':
cpu68k-5.c:3382: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_929a':
cpu68k-5.c:3394: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_930a':
cpu68k-5.c:3406: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_931a':
cpu68k-5.c:3418: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_932a':
cpu68k-5.c:3430: warning: unused variable `srcaddr_tmp'
cpu68k-5.c: In function `cpu_op_1010a':
cpu68k-5.c:4256: warning: unused variable `srcaddr_tmp'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-6.o -MD -MP -MF ".deps/cpu68k-6.Tpo" -c -o cpu68k-6.o cpu68k-6.c; \
then mv -f ".deps/cpu68k-6.Tpo" ".deps/cpu68k-6.Po"; else rm -f ".deps/cpu68k-6.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-7.o -MD -MP -MF ".deps/cpu68k-7.Tpo" -c -o cpu68k-7.o cpu68k-7.c; \
then mv -f ".deps/cpu68k-7.Tpo" ".deps/cpu68k-7.Po"; else rm -f ".deps/cpu68k-7.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-8.o -MD -MP -MF ".deps/cpu68k-8.Tpo" -c -o cpu68k-8.o cpu68k-8.c; \
then mv -f ".deps/cpu68k-8.Tpo" ".deps/cpu68k-8.Po"; else rm -f ".deps/cpu68k-8.Tpo"; exit 1; fi
cpu68k-8.c: In function `cpu_op_1067a':
cpu68k-8.c:83: warning: unused variable `srcaddr_tmp'
cpu68k-8.c: In function `cpu_op_1067b':
cpu68k-8.c:98: warning: unused variable `srcaddr_tmp'
cpu68k-8.c: In function `cpu_op_1099a':
cpu68k-8.c:1103: warning: unused variable `dstaddr_tmp'
cpu68k-8.c: In function `cpu_op_1099b':
cpu68k-8.c:1118: warning: unused variable `dstaddr_tmp'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-9.o -MD -MP -MF ".deps/cpu68k-9.Tpo" -c -o cpu68k-9.o cpu68k-9.c; \
then mv -f ".deps/cpu68k-9.Tpo" ".deps/cpu68k-9.Po"; else rm -f ".deps/cpu68k-9.Tpo"; exit 1; fi
cpu68k-9.c: In function `cpu_op_1146a':
cpu68k-9.c:111: warning: unused variable `srcaddr_tmp'
cpu68k-9.c: In function `cpu_op_1146b':
cpu68k-9.c:125: warning: unused variable `srcaddr_tmp'
cpu68k-9.c: In function `cpu_op_1180a':
cpu68k-9.c:1159: warning: unused variable `dstaddr_tmp'
cpu68k-9.c: In function `cpu_op_1180b':
cpu68k-9.c:1173: warning: unused variable `dstaddr_tmp'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-a.o -MD -MP -MF ".deps/cpu68k-a.Tpo" -c -o cpu68k-a.o cpu68k-a.c; \
then mv -f ".deps/cpu68k-a.Tpo" ".deps/cpu68k-a.Po"; else rm -f ".deps/cpu68k-a.Tpo"; exit 1; fi
cpu68k-a.c: In function `cpu_op_1613a':
cpu68k-a.c:15: warning: unused parameter `ipc'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-b.o -MD -MP -MF ".deps/cpu68k-b.Tpo" -c -o cpu68k-b.o cpu68k-b.c; \
then mv -f ".deps/cpu68k-b.Tpo" ".deps/cpu68k-b.Po"; else rm -f ".deps/cpu68k-b.Tpo"; exit 1; fi
cpu68k-b.c: In function `cpu_op_1230a':
cpu68k-b.c:21: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1231a':
cpu68k-b.c:47: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1232a':
cpu68k-b.c:74: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1233a':
cpu68k-b.c:99: warning: unused variable `srcaddr_tmp'
cpu68k-b.c:103: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1233b':
cpu68k-b.c:111: warning: unused variable `srcaddr_tmp'
cpu68k-b.c: In function `cpu_op_1234a':
cpu68k-b.c:132: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1235a':
cpu68k-b.c:160: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1236a':
cpu68k-b.c:188: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1237a':
cpu68k-b.c:215: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1238a':
cpu68k-b.c:241: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1239a':
cpu68k-b.c:267: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1240a':
cpu68k-b.c:293: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1241a':
cpu68k-b.c:318: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1242a':
cpu68k-b.c:343: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1243a':
cpu68k-b.c:369: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1244a':
cpu68k-b.c:396: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1245a':
cpu68k-b.c:424: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1246a':
cpu68k-b.c:452: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1247a':
cpu68k-b.c:480: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1248a':
cpu68k-b.c:508: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1249a':
cpu68k-b.c:535: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1250a':
cpu68k-b.c:561: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1251a':
cpu68k-b.c:587: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1252a':
cpu68k-b.c:613: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1253a':
cpu68k-b.c:638: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1254a':
cpu68k-b.c:663: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1255a':
cpu68k-b.c:689: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1256a':
cpu68k-b.c:716: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1257a':
cpu68k-b.c:744: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1258a':
cpu68k-b.c:772: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1259a':
cpu68k-b.c:800: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1260a':
cpu68k-b.c:828: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1261a':
cpu68k-b.c:855: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1262a':
cpu68k-b.c:881: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1263a':
cpu68k-b.c:907: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1264a':
cpu68k-b.c:933: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1265a':
cpu68k-b.c:958: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1266a':
cpu68k-b.c:983: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1267a':
cpu68k-b.c:1009: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1268a':
cpu68k-b.c:1036: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1269a':
cpu68k-b.c:1064: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1270a':
cpu68k-b.c:1092: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1271a':
cpu68k-b.c:1120: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1272a':
cpu68k-b.c:1148: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1273a':
cpu68k-b.c:1175: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1274a':
cpu68k-b.c:1201: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1275a':
cpu68k-b.c:1227: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1276a':
cpu68k-b.c:1253: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1277a':
cpu68k-b.c:1278: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1280a':
cpu68k-b.c:1367: warning: unused variable `dstaddr_tmp'
cpu68k-b.c: In function `cpu_op_1280b':
cpu68k-b.c:1382: warning: unused variable `dstaddr_tmp'
cpu68k-b.c: In function `cpu_op_1302a':
cpu68k-b.c:2083: warning: unused variable `srcaddr_tmp'
cpu68k-b.c:2087: warning: unused variable `dstaddr_tmp'
cpu68k-b.c:2089: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1302b':
cpu68k-b.c:2097: warning: unused variable `srcaddr_tmp'
cpu68k-b.c:2101: warning: unused variable `dstaddr_tmp'
cpu68k-b.c: In function `cpu_op_1303a':
cpu68k-b.c:2121: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1304a':
cpu68k-b.c:2151: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1305a':
cpu68k-b.c:2179: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1306a':
cpu68k-b.c:2205: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1307a':
cpu68k-b.c:2232: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1308a':
cpu68k-b.c:2260: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1309a':
cpu68k-b.c:2288: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1310a':
cpu68k-b.c:2316: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1311a':
cpu68k-b.c:2344: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1312a':
cpu68k-b.c:2371: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1313a':
cpu68k-b.c:2397: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1314a':
cpu68k-b.c:2423: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1315a':
cpu68k-b.c:2449: warning: unused variable `outdata'
cpu68k-b.c: In function `cpu_op_1316a':
cpu68k-b.c:2474: warning: unused variable `outdata'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-c.o -MD -MP -MF ".deps/cpu68k-c.Tpo" -c -o cpu68k-c.o cpu68k-c.c; \
then mv -f ".deps/cpu68k-c.Tpo" ".deps/cpu68k-c.Po"; else rm -f ".deps/cpu68k-c.Tpo"; exit 1; fi
cpu68k-c.c: In function `cpu_op_1319a':
cpu68k-c.c:83: warning: unused variable `srcaddr_tmp'
cpu68k-c.c: In function `cpu_op_1319b':
cpu68k-c.c:98: warning: unused variable `srcaddr_tmp'
cpu68k-c.c: In function `cpu_op_1351a':
cpu68k-c.c:1103: warning: unused variable `dstaddr_tmp'
cpu68k-c.c: In function `cpu_op_1351b':
cpu68k-c.c:1118: warning: unused variable `dstaddr_tmp'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-d.o -MD -MP -MF ".deps/cpu68k-d.Tpo" -c -o cpu68k-d.o cpu68k-d.c; \
then mv -f ".deps/cpu68k-d.Tpo" ".deps/cpu68k-d.Po"; else rm -f ".deps/cpu68k-d.Tpo"; exit 1; fi
cpu68k-d.c: In function `cpu_op_1401a':
cpu68k-d.c:111: warning: unused variable `srcaddr_tmp'
cpu68k-d.c: In function `cpu_op_1401b':
cpu68k-d.c:125: warning: unused variable `srcaddr_tmp'
cpu68k-d.c: In function `cpu_op_1435a':
cpu68k-d.c:1159: warning: unused variable `dstaddr_tmp'
cpu68k-d.c: In function `cpu_op_1435b':
cpu68k-d.c:1173: warning: unused variable `dstaddr_tmp'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-e.o -MD -MP -MF ".deps/cpu68k-e.Tpo" -c -o cpu68k-e.o cpu68k-e.c; \
then mv -f ".deps/cpu68k-e.Tpo" ".deps/cpu68k-e.Po"; else rm -f ".deps/cpu68k-e.Tpo"; exit 1; fi
cpu68k-e.c: In function `cpu_op_1485a':
cpu68k-e.c:20: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1486a':
cpu68k-e.c:59: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1487a':
cpu68k-e.c:98: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1497a':
cpu68k-e.c:551: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1498a':
cpu68k-e.c:590: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1499a':
cpu68k-e.c:629: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1509a':
cpu68k-e.c:1083: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1510a':
cpu68k-e.c:1124: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1511a':
cpu68k-e.c:1165: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1557a':
cpu68k-e.c:3273: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1558a':
cpu68k-e.c:3314: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1559a':
cpu68k-e.c:3355: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1560a':
cpu68k-e.c:3396: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1561a':
cpu68k-e.c:3437: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1562a':
cpu68k-e.c:3477: warning: unused variable `bits'
cpu68k-e.c: In function `cpu_op_1563a':
cpu68k-e.c:3516: warning: unused variable `bits'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k-f.o -MD -MP -MF ".deps/cpu68k-f.Tpo" -c -o cpu68k-f.o cpu68k-f.c; \
then mv -f ".deps/cpu68k-f.Tpo" ".deps/cpu68k-f.Po"; else rm -f ".deps/cpu68k-f.Tpo"; exit 1; fi
cpu68k-f.c: In function `cpu_op_1614a':
cpu68k-f.c:15: warning: unused parameter `ipc'
rm -f lib68k.a
ar cru lib68k.a cpu68k-0.o cpu68k-1.o cpu68k-2.o cpu68k-3.o cpu68k-4.o cpu68k-5.o cpu68k-6.o cpu68k-7.o cpu68k-8.o cpu68k-9.o cpu68k-a.o cpu68k-b.o cpu68k-c.o cpu68k-d.o cpu68k-e.o cpu68k-f.o
ranlib lib68k.a
make[3]: Entering directory `/home/stephen/apps/generator-0.35-cbiere/cpu68k'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/cpu68k'
make[2]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/cpu68k'
make[1]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/cpu68k'
Making install in ym2612
make[1]: Entering directory `/home/stephen/apps/generator-0.35-cbiere/ym2612'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT fm.o -MD -MP -MF ".deps/fm.Tpo" -c -o fm.o fm.c; \
then mv -f ".deps/fm.Tpo" ".deps/fm.Po"; else rm -f ".deps/fm.Tpo"; exit 1; fi
fm.c: In function `calc_eg':
fm.c:810: warning: comparison between signed and unsigned
fm.c: In function `OPN_CALC_FCOUNT':
fm.c:929: warning: comparison between signed and unsigned
fm.c: In function `YM2612UpdateOne':
fm.c:3428: warning: comparison between signed and unsigned
fm.c: In function `set_tl':
fm.c:697: warning: unused parameter `CH'
rm -f libym2612.a
ar cru libym2612.a fm.o
ranlib libym2612.a
make[2]: Entering directory `/home/stephen/apps/generator-0.35-cbiere/ym2612'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/ym2612'
make[1]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/ym2612'
Making install in sn76496
make[1]: Entering directory `/home/stephen/apps/generator-0.35-cbiere/sn76496'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT sn76496.o -MD -MP -MF ".deps/sn76496.Tpo" -c -o sn76496.o sn76496.c; \
then mv -f ".deps/sn76496.Tpo" ".deps/sn76496.Po"; else rm -f ".deps/sn76496.Tpo"; exit 1; fi
sn76496.c: In function `SN76496Write':
sn76496.c:99: warning: signed and unsigned type in conditional expression
sn76496.c: In function `SN76496Init':
sn76496.c:256: warning: unused variable `name'
rm -f libsn76496.a
ar cru libsn76496.a sn76496.o
ranlib libsn76496.a
make[2]: Entering directory `/home/stephen/apps/generator-0.35-cbiere/sn76496'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/sn76496'
make[1]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/sn76496'
Making install in main
make[1]: Entering directory `/home/stephen/apps/generator-0.35-cbiere/main'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpu68k.o -MD -MP -MF ".deps/cpu68k.Tpo" -c -o cpu68k.o cpu68k.c; \
then mv -f ".deps/cpu68k.Tpo" ".deps/cpu68k.Po"; else rm -f ".deps/cpu68k.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT mem68k.o -MD -MP -MF ".deps/mem68k.Tpo" -c -o mem68k.o mem68k.c; \
then mv -f ".deps/mem68k.Tpo" ".deps/mem68k.Po"; else rm -f ".deps/mem68k.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT reg68k.o -MD -MP -MF ".deps/reg68k.Tpo" -c -o reg68k.o reg68k.c; \
then mv -f ".deps/reg68k.Tpo" ".deps/reg68k.Po"; else rm -f ".deps/reg68k.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT event.o -MD -MP -MF ".deps/event.Tpo" -c -o event.o event.c; \
then mv -f ".deps/event.Tpo" ".deps/event.Po"; else rm -f ".deps/event.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT generator.o -MD -MP -MF ".deps/generator.Tpo" -c -o generator.o generator.c; \
then mv -f ".deps/generator.Tpo" ".deps/generator.Po"; else rm -f ".deps/generator.Tpo"; exit 1; fi
generator.c: In function `loadimage_zip':
generator.c:808: warning: implicit declaration of function `loadimage_bzip2'
generator.c:808: warning: assignment makes pointer from integer without a cast
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT cpuz80.o -MD -MP -MF ".deps/cpuz80.Tpo" -c -o cpuz80.o cpuz80.c; \
then mv -f ".deps/cpuz80.Tpo" ".deps/cpuz80.Po"; else rm -f ".deps/cpuz80.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT vdp.o -MD -MP -MF ".deps/vdp.Tpo" -c -o vdp.o vdp.c; \
then mv -f ".deps/vdp.Tpo" ".deps/vdp.Po"; else rm -f ".deps/vdp.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT gensound.o -MD -MP -MF ".deps/gensound.Tpo" -c -o gensound.o gensound.c; \
then mv -f ".deps/gensound.Tpo" ".deps/gensound.Po"; else rm -f ".deps/gensound.Tpo"; exit 1; fi
gensound.c: In function `sound_endfield':
gensound.c:265: warning: implicit declaration of function `nanosleep'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT memz80.o -MD -MP -MF ".deps/memz80.Tpo" -c -o memz80.o memz80.c; \
then mv -f ".deps/memz80.Tpo" ".deps/memz80.Po"; else rm -f ".deps/memz80.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT ui-sdl.o -MD -MP -MF ".deps/ui-sdl.Tpo" -c -o ui-sdl.o ui-sdl.c; \
then mv -f ".deps/ui-sdl.Tpo" ".deps/ui-sdl.Po"; else rm -f ".deps/ui-sdl.Tpo"; exit 1; fi
ui-sdl.c: In function `ui_endfield':
ui-sdl.c:780: warning: implicit declaration of function `gettimeofday'
ui-sdl.c:817: warning: implicit declaration of function `nanosleep'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT uiplot.o -MD -MP -MF ".deps/uiplot.Tpo" -c -o uiplot.o uiplot.c; \
then mv -f ".deps/uiplot.Tpo" ".deps/uiplot.Po"; else rm -f ".deps/uiplot.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT gensoundp-unix.o -MD -MP -MF ".deps/gensoundp-unix.Tpo" -c -o gensoundp-unix.o gensoundp-unix.c; \
then mv -f ".deps/gensoundp-unix.Tpo" ".deps/gensoundp-unix.Po"; else rm -f ".deps/gensoundp-unix.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT patch.o -MD -MP -MF ".deps/patch.Tpo" -c -o patch.o patch.c; \
then mv -f ".deps/patch.Tpo" ".deps/patch.Po"; else rm -f ".deps/patch.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT dib.o -MD -MP -MF ".deps/dib.Tpo" -c -o dib.o dib.c; \
then mv -f ".deps/dib.Tpo" ".deps/dib.Po"; else rm -f ".deps/dib.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT avi.o -MD -MP -MF ".deps/avi.Tpo" -c -o avi.o avi.c; \
then mv -f ".deps/avi.Tpo" ".deps/avi.Po"; else rm -f ".deps/avi.Tpo"; exit 1; fi
avi.c: In function `avi_open':
avi.c:93: warning: unused parameter `jpeg'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I. -I../cpu68k -I../ym2612 -I../raze -I../cmz80 -I../sn76496 -I../gtkopts -DFNAME_TCLSCRIPT=\"/usr/local/share/generator/gen.tcl\" -I/usr/include/SDL -D_REENTRANT    -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include -MT diss68k.o -MD -MP -MF ".deps/diss68k.Tpo" -c -o diss68k.o diss68k.c; \
then mv -f ".deps/diss68k.Tpo" ".deps/diss68k.Po"; else rm -f ".deps/diss68k.Tpo"; exit 1; fi
gcc  -g -O2 -W -Wall -Wformat=2 -O3 -ffast-math -fomit-frame-pointer -minline-all-stringops -fno-math-errno -march=i686  -I/usr/X11R6/include   -o generator-sdl  cpu68k.o mem68k.o reg68k.o event.o generator.o state.o cpuz80.o vdp.o gensound.o memz80.o snprintf.o ui-sdl.o uiplot.o gensoundp-unix.o initcart.o patch.o dib.o avi.o diss68k.o ../cpu68k/lib68k.a ../ym2612/libym2612.a -lz ../raze/libraze.a   -lSM -lICE  -L/usr/X11R6/lib ../sn76496/libsn76496.a -lSDL -lpthread ../gtkopts/libgtkopts.a ../cpu68k/tab68k.o
generator.o(.text+0x1233): In function `loadimage_zip':
/home/stephen/apps/generator-0.35-cbiere/main/generator.c:808: undefined reference to `loadimage_bzip2'
collect2: ld returned 1 exit status
make[1]: *** [generator-sdl] Error 1
make[1]: Leaving directory `/home/stephen/apps/generator-0.35-cbiere/main'
make: *** [install-recursive] Error 1
stephen@ubuntu:~/apps/generator-0.35-cbiere $
```

That's the patched version but I get the same error when trying the original client.
[http://www.squish.net/generator/](http://www.squish.net/generator/)

---

### Post by dhonn on 2005-02-02
did you ./configure to check for installed dependency libraries?

It stops at this point:
```

generator.o(.text+0x1233): In function `loadimage_zip':
/home/stephen/apps/generator-0.35-cbiere/main/generator.c:808: undefined reference to `loadimage_bzip2'
```

---

