---
title: "problems installing resin webserver"
date: 2006-04-18
forum: Desktop Environments
---

### Post by trooperz on 2006-04-18
hellow here, 

I've got some problems with the installation of "resin webserver". 

The following steps will start Resin for development:
     1. Install JDK 1.4 or later and link /usr/java to the Java home or set environment
          variable JAVA_HOME.
     2. tar -vzxf resin-3.0.0.tar.gz
     3. (Optional) Link /usr/local/resin to the resin-3.0.0 directory.
     4. ./configure;[COLOR="Blue"]make;[/COLOR] make install
     5. Execute resin-3.0.0/bin/httpd.sh
     6. Browse [http://localhost:8080](http://localhost:8080)

when i type "make" i got the following errors...

(cd modules/c/src; make)
make[1]: Entering directory `/usr/local/src/resin-pro-3.0.18/modules/c/src'
for dir in common resin_os; do (cd $dir; make); done
make[2]: Entering directory `/usr/local/src/resin-pro-3.0.18/modules/c/src/commo n'
gcc -c  -g -O2 -DPOLL stream.c
gcc -c  -g -O2 -DPOLL config.c
gcc -c  -g -O2 -DPOLL memory.c
/usr/bin/ld -r -o common.o stream.o config.o memory.o
/usr/local/src/resin-pro-3.0.18/libtool --silent --mode=compile gcc -o stream.lo  -c  -g -O2 -DPOLL stream.c
/usr/local/src/resin-pro-3.0.18/libtool --silent --mode=compile gcc -o config.lo -c  -g -O2 -DPOLL config.c
/usr/local/src/resin-pro-3.0.18/libtool --silent --mode=compile gcc -o memory.lo -c  -g -O2 -DPOLL memory.c
make[2]: Leaving directory `/usr/local/src/resin-pro-3.0.18/modules/c/src/common'
make[2]: Entering directory `/usr/local/src/resin-pro-3.0.18/modules/c/src/resin_os'
gcc -g -O2 -DPOLL  -D_FILE_OFFSET_BITS=64 -DRESIN_HOME=\"/usr/local/src/resin-pro-3.0.18\"  -I../common -DCPU=\"i386\" -DOS=   -c -o jni_os.o jni_os.c
jni_os.c:64:17: fout: jni.h: Onbekend bestand of map
jni_os.c:66: fout: syntax error before ‘jvmdi_can_reload_native’
jni_os.c:66: fout: syntax error before ‘*’ token
jni_os.c:66: let op: datadefinitie heeft geen type of opslagklasse
jni_os.c:67: fout: syntax error before ‘jvmti_can_reload_native’
jni_os.c:67: fout: syntax error before ‘*’ token
jni_os.c:67: let op: datadefinitie heeft geen type of opslagklasse
jni_os.c:70: fout: syntax error before ‘jvmti_reload_native’
jni_os.c:70: fout: syntax error before ‘*’ token
jni_os.c:75: let op: datadefinitie heeft geen type of opslagklasse
jni_os.c:78: fout: syntax error before ‘jvmdi_reload_native’
jni_os.c:78: fout: syntax error before ‘*’ token
jni_os.c:83: let op: datadefinitie heeft geen type of opslagklasse
jni_os.c:86: fout: syntax error before ‘*’ token
jni_os.c: In functie ‘resin_set_byte_array_region’:
jni_os.c:90: fout: ‘jbyte’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:90: fout: (Elke niet-gedeclareerde naam wordt slechts één
jni_os.c:90: fout: keer vermeld voor elke functie waarin hij staat.)
jni_os.c:90: fout: ‘cBuf’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:94: fout: ‘env’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:94: fout: ‘buf’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:97: fout: ‘offset’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:97: fout: ‘buffer’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:97: fout: ‘sublen’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c: Op bovenste niveau:
jni_os.c:108: fout: syntax error before ‘*’ token
jni_os.c: In functie ‘resin_get_byte_array_region’:
jni_os.c:112: fout: ‘jbyte’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:112: fout: ‘cBuf’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:112: fout: ‘env’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:112: fout: ‘buf’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:115: fout: ‘buffer’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:115: fout: ‘offset’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:115: fout: ‘sublen’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c: Op bovenste niveau:
jni_os.c:126: fout: syntax error before ‘*’ token
jni_os.c: In functie ‘resin_printf_exception’:
jni_os.c:130: fout: ‘jclass’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:130: fout: syntax error before ‘clazz’
jni_os.c:132: fout: ‘fmt’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:138: fout: ‘env’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:139: fout: ‘clazz’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:139: fout: ‘cl’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:132: fout: ‘va_start’ gebruikt in functie met vaste argumenten
jni_os.c: Op bovenste niveau:
jni_os.c:150: fout: syntax error before ‘jboolean’
jni_os.c:151: fout: syntax error before ‘*’ token
jni_os.c: In functie ‘Java_com_caucho_loader_ClassEntry_canReloadNative’:
jni_os.c:154: fout: ‘env’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:154: fout: ‘obj’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c: Op bovenste niveau:
jni_os.c:158: fout: syntax error before ‘jint’
jni_os.c:159: fout: syntax error before ‘*’ token
jni_os.c: In functie ‘Java_com_caucho_loader_ClassEntry_reloadNative’:
jni_os.c:166: fout: ‘env’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:166: fout: ‘obj’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:166: fout: ‘cl’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:166: fout: ‘buf’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:166: fout: ‘offset’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:166: fout: ‘length’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c: Op bovenste niveau:
jni_os.c:175: fout: syntax error before ‘*’ token
jni_os.c: In functie ‘get_utf8’:
jni_os.c:179: fout: ‘env’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:179: fout: ‘jaddr’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:182: fout: ‘buf’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:182: fout: ‘buflen’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c: Op bovenste niveau:
jni_os.c:191: fout: syntax error before ‘jint’
jni_os.c:192: fout: syntax error before ‘*’ token
jni_os.c: In functie ‘Java_com_caucho_server_boot_ResinBoot_execDaemon’:
jni_os.c:204: fout: ‘j_argv’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:205: fout: ‘env’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:206: fout: ‘j_envp’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:208: fout: ‘j_pwd’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:219: fout: ‘jstring’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:219: fout: syntax error before ‘j_string’
jni_os.c:221: fout: ‘j_string’ is hier niet gedeclareerd (eerste gebruik in deze functie)
jni_os.c:237: fout: syntax error before ‘j_string’
make[2]: *** [jni_os.o] Fout 1
make[2]: Leaving directory `/usr/local/src/resin-pro-3.0.18/modules/c/src/resin_os'
make[1]: *** [plugins] Fout 2
make[1]: Leaving directory `/usr/local/src/resin-pro-3.0.18/modules/c/src'
make: *** [all] Fout 2


can someone help me with thisone?

thx

---

### Post by linbie on 2006-10-29
I'm just wondering if you have found the solution? My ubuntu system is unable to find the gcc.

---

