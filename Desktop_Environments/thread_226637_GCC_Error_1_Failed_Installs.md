---
title: "GCC Error 1 Failed Installs"
date: 2006-07-31
forum: Desktop Environments
---

### Post by rbgCODE on 2006-07-31
I am having a lot of failed installs, Right now I am trying to install Cheetah, via 

error: command 'gcc' failed with exit status 1
:~/Cheetah-2.0rc7$ python setup.py install

and this is the output.  Any help would be great...

running install
running build
running build_py
running build_ext
building 'Cheetah._namemapper' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPI C -I/usr/include/python2.4 -c src/_namemapper.c -o build/temp.linux-i686-2.4/src /_namemapper.o
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:11,
                 from /usr/include/python2.4/Python.h:18,
                 from src/_namemapper.c:15:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:122:61: error: limits.h: No s uch file or directory
In file included from src/_namemapper.c:15:
/usr/include/python2.4/Python.h:32:19: error: stdio.h: No such file or directory
/usr/include/python2.4/Python.h:34:5: error: #error "Python.h requires that stdi o.h define NULL."
/usr/include/python2.4/Python.h:37:20: error: string.h: No such file or director y
/usr/include/python2.4/Python.h:38:19: error: errno.h: No such file or directory
/usr/include/python2.4/Python.h:39:20: error: stdlib.h: No such file or director y
/usr/include/python2.4/Python.h:41:20: error: unistd.h: No such file or director y
/usr/include/python2.4/Python.h:53:20: error: assert.h: No such file or director y
In file included from /usr/include/python2.4/Python.h:55,
                 from src/_namemapper.c:15:
/usr/include/python2.4/pyport.h:90:76: error: math.h: No such file or directory
/usr/include/python2.4/pyport.h:97:22: error: sys/time.h: No such file or direct ory
/usr/include/python2.4/pyport.h:98:18: error: time.h: No such file or directory
/usr/include/python2.4/pyport.h:116:24: error: sys/select.h: No such file or dir ectory
/usr/include/python2.4/pyport.h:155:22: error: sys/stat.h: No such file or direc tory
In file included from /usr/include/python2.4/Python.h:74,
                 from src/_namemapper.c:15:
/usr/include/python2.4/pymem.h:50: warning: parameter names (without types) in f unction declaration
/usr/include/python2.4/pymem.h:51: error: syntax error before ‘size_t’
/usr/include/python2.4/pymem.h:51: warning: function declaration isn’t a prototy pe
In file included from /usr/include/python2.4/Python.h:76,
                 from src/_namemapper.c:15:
/usr/include/python2.4/object.h:227: error: syntax error before ‘FILE’
/usr/include/python2.4/object.h:227: warning: function declaration isn’t a proto type
/usr/include/python2.4/object.h:371: error: syntax error before ‘FILE’
/usr/include/python2.4/object.h:371: warning: function declaration isn’t a proto type
In file included from /usr/include/python2.4/Python.h:77,
                 from src/_namemapper.c:15:
/usr/include/python2.4/objimpl.h:97: warning: parameter names (without types) in  function declaration
/usr/include/python2.4/objimpl.h:98: error: syntax error before ‘size_t’
/usr/include/python2.4/objimpl.h:98: warning: function declaration isn’t a proto type
/usr/include/python2.4/objimpl.h:292: warning: parameter names (without types) i n function declaration
In file included from /usr/include/python2.4/Python.h:81,
                 from src/_namemapper.c:15:
/usr/include/python2.4/unicodeobject.h:55:19: error: ctype.h: No such file or di rectory
/usr/include/python2.4/unicodeobject.h:118:21: error: wchar.h: No such file or d irectory
In file included from /usr/include/python2.4/Python.h:81,
                 from src/_namemapper.c:15:
/usr/include/python2.4/unicodeobject.h:131: error: syntax error before ‘Py_UNICO DE’
/usr/include/python2.4/unicodeobject.h:131: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:131: warning: data definition has no type  or storage class
/usr/include/python2.4/unicodeobject.h:376: error: syntax error before ‘Py_UNICO DE’
/usr/include/python2.4/unicodeobject.h:376: warning: no semicolon at end of stru ct or union
/usr/include/python2.4/unicodeobject.h:381: error: syntax error before ‘}’ token
/usr/include/python2.4/unicodeobject.h:381: warning: type defaults to ‘int’ in d eclaration of ‘PyUnicodeObject’
/usr/include/python2.4/unicodeobject.h:381: warning: data definition has no type  or storage class
/usr/include/python2.4/unicodeobject.h:422: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:422: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:424: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:429: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:431: warning: type defaults to ‘int’ in d eclaration of ‘PyUnicodeUCS4_AsUnicode’
/usr/include/python2.4/unicodeobject.h:431: warning: data definition has no type  or storage class
/usr/include/python2.4/unicodeobject.h:440: error: syntax error before ‘PyUnicod eUCS4_GetMax’
/usr/include/python2.4/unicodeobject.h:440: warning: type defaults to ‘int’ in d eclaration of ‘PyUnicodeUCS4_GetMax’
/usr/include/python2.4/unicodeobject.h:440: warning: data definition has no type  or storage class
/usr/include/python2.4/unicodeobject.h:511: warning: type defaults to ‘int’ in d eclaration of ‘wchar_t’
/usr/include/python2.4/unicodeobject.h:511: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:513: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:528: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:531: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:621: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:621: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:625: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:654: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:654: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:661: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:683: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:683: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:686: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:760: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:760: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:764: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:779: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:779: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:781: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:796: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:796: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:798: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:827: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:827: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:830: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:849: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:849: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:852: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:891: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:891: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:896: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:912: warning: type defaults to ‘int’ in d eclaration of ‘Py_UNICODE’
/usr/include/python2.4/unicodeobject.h:912: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:916: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:965: error: syntax error before ‘*’ token
/usr/include/python2.4/unicodeobject.h:969: warning: function declaration isn’t a prototype
/usr/include/python2.4/unicodeobject.h:1128: error: syntax error before ‘*’ toke n
/usr/include/python2.4/unicodeobject.h:1131: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1143: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1144: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1147: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1148: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1151: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1152: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1155: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1156: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1159: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1160: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1162: error: syntax error before ‘_PyUnic odeUCS4_ToLowercase’
/usr/include/python2.4/unicodeobject.h:1163: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1164: warning: type defaults to ‘int’ in declaration of ‘_PyUnicodeUCS4_ToLowercase’
/usr/include/python2.4/unicodeobject.h:1164: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1164: warning: data definition has no typ e or storage class
/usr/include/python2.4/unicodeobject.h:1166: error: syntax error before ‘_PyUnic odeUCS4_ToUppercase’
/usr/include/python2.4/unicodeobject.h:1167: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1168: warning: type defaults to ‘int’ in declaration of ‘_PyUnicodeUCS4_ToUppercase’
/usr/include/python2.4/unicodeobject.h:1168: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1168: warning: data definition has no typ e or storage class
/usr/include/python2.4/unicodeobject.h:1170: error: syntax error before ‘_PyUnic odeUCS4_ToTitlecase’
/usr/include/python2.4/unicodeobject.h:1171: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1172: warning: type defaults to ‘int’ in declaration of ‘_PyUnicodeUCS4_ToTitlecase’
/usr/include/python2.4/unicodeobject.h:1172: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1172: warning: data definition has no typ e or storage class
/usr/include/python2.4/unicodeobject.h:1175: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1176: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1179: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1180: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1183: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1184: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1187: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1188: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1191: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1192: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1195: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1196: warning: function declaration isn’t  a prototype
/usr/include/python2.4/unicodeobject.h:1199: error: syntax error before ‘ch’
/usr/include/python2.4/unicodeobject.h:1200: warning: function declaration isn’t  a prototype
In file included from /usr/include/python2.4/Python.h:82,
                 from src/_namemapper.c:15:
/usr/include/python2.4/intobject.h:35: error: syntax error before ‘*’ token
/usr/include/python2.4/intobject.h:35: warning: function declaration isn’t a pro totype
In file included from /usr/include/python2.4/Python.h:84,
                 from src/_namemapper.c:15:
/usr/include/python2.4/longobject.h:46: error: syntax error before ‘*’ token
/usr/include/python2.4/longobject.h:46: warning: function declaration isn’t a pr ototype
/usr/include/python2.4/longobject.h:63: error: syntax error before ‘_PyLong_NumB its’
/usr/include/python2.4/longobject.h:63: warning: type defaults to ‘int’ in decla ration of ‘_PyLong_NumBits’
/usr/include/python2.4/longobject.h:63: warning: data definition has no type or storage class
/usr/include/python2.4/longobject.h:79: error: syntax error before ‘size_t’
/usr/include/python2.4/longobject.h:80: warning: function declaration isn’t a pr ototype
/usr/include/python2.4/longobject.h:102: error: syntax error before ‘size_t’
/usr/include/python2.4/longobject.h:103: warning: function declaration isn’t a p rototype
In file included from /usr/include/python2.4/Python.h:101,
                 from src/_namemapper.c:15:
/usr/include/python2.4/fileobject.h:12: error: syntax error before ‘FILE’
/usr/include/python2.4/fileobject.h:12: warning: no semicolon at end of struct o r union
/usr/include/python2.4/fileobject.h:15: error: syntax error before ‘*’ token
/usr/include/python2.4/fileobject.h:15: warning: function declaration isn’t a pr ototype
/usr/include/python2.4/fileobject.h:28: error: syntax error before ‘}’ token
/usr/include/python2.4/fileobject.h:28: warning: type defaults to ‘int’ in decla ration of ‘PyFileObject’
/usr/include/python2.4/fileobject.h:28: warning: data definition has no type or storage class
/usr/include/python2.4/fileobject.h:38: error: syntax error before ‘*’ token
/usr/include/python2.4/fileobject.h:39: error: syntax error before ‘*’ token
/usr/include/python2.4/fileobject.h:40: warning: type defaults to ‘int’ in decla ration of ‘PyFile_AsFile’
/usr/include/python2.4/fileobject.h:40: warning: data definition has no type or storage class
/usr/include/python2.4/fileobject.h:57: error: syntax error before ‘FILE’
/usr/include/python2.4/fileobject.h:57: warning: function declaration isn’t a pr ototype
/usr/include/python2.4/fileobject.h:58: error: syntax error before ‘Py_Universal NewlineFread’
/usr/include/python2.4/fileobject.h:58: error: syntax error before ‘size_t’
/usr/include/python2.4/fileobject.h:58: warning: type defaults to ‘int’ in decla ration of ‘Py_UniversalNewlineFread’
/usr/include/python2.4/fileobject.h:58: warning: function declaration isn’t a pr ototype
/usr/include/python2.4/fileobject.h:58: warning: data definition has no type or storage class
In file included from /usr/include/python2.4/Python.h:112,
                 from src/_namemapper.c:15:
/usr/include/python2.4/pyerrors.h:156: warning: type defaults to ‘int’ in declar ation of ‘Py_UNICODE’
/usr/include/python2.4/pyerrors.h:156: error: syntax error before ‘*’ token
/usr/include/python2.4/pyerrors.h:156: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pyerrors.h:160: warning: type defaults to ‘int’ in declar ation of ‘Py_UNICODE’
/usr/include/python2.4/pyerrors.h:160: error: syntax error before ‘*’ token
/usr/include/python2.4/pyerrors.h:160: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pyerrors.h:226: error: syntax error before ‘size_t’
/usr/include/python2.4/pyerrors.h:227: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pyerrors.h:228: error: syntax error before ‘size_t’
/usr/include/python2.4/pyerrors.h:229: warning: function declaration isn’t a pro totype
In file included from /usr/include/python2.4/Python.h:117,
                 from src/_namemapper.c:15:
/usr/include/python2.4/pythonrun.h:32: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:32: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:33: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:33: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:35: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:35: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:36: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:36: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:40: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:40: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:41: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:41: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:42: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:42: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:43: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:43: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:44: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:44: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:45: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:45: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:46: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:46: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:49: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:49: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:55: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:56: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:59: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:59: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:60: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:61: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:64: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:65: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:66: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:67: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:82: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:82: warning: function declaration isn’t a pro totype
/usr/include/python2.4/pythonrun.h:123: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:123: warning: function declaration isn’t a pr ototype
/usr/include/python2.4/pythonrun.h:125: error: syntax error before ‘*’ token
/usr/include/python2.4/pythonrun.h:125: warning: function declaration isn’t a pr ototype
In file included from /usr/include/python2.4/Python.h:119,
                 from src/_namemapper.c:15:
/usr/include/python2.4/sysmodule.h:12: error: syntax error before ‘*’ token
/usr/include/python2.4/sysmodule.h:12: error: syntax error before ‘FILE’
/usr/include/python2.4/sysmodule.h:12: warning: type defaults to ‘int’ in declar ation of ‘PySys_GetFile’
/usr/include/python2.4/sysmodule.h:12: warning: function declaration isn’t a pro totype
/usr/include/python2.4/sysmodule.h:12: warning: data definition has no type or s torage class
In file included from /usr/include/python2.4/Python.h:121,
                 from src/_namemapper.c:15:
/usr/include/python2.4/import.h:25: error: syntax error before ‘size_t’
/usr/include/python2.4/import.h:25: warning: function declaration isn’t a protot ype
In file included from src/_namemapper.c:15:
/usr/include/python2.4/Python.h:131: error: syntax error before ‘size_t’
/usr/include/python2.4/Python.h:131: warning: function declaration isn’t a proto type
In file included from /usr/include/python2.4/Python.h:149,
                 from src/_namemapper.c:15:
/usr/include/python2.4/pyfpe.h:129:20: error: signal.h: No such file or director y
/usr/include/python2.4/pyfpe.h:130:20: error: setjmp.h: No such file or director y
In file included from /usr/include/python2.4/Python.h:149,
                 from src/_namemapper.c:15:
/usr/include/python2.4/pyfpe.h:132: error: syntax error before ‘PyFPE_jbuf’
/usr/include/python2.4/pyfpe.h:132: warning: type defaults to ‘int’ in declarati on of ‘PyFPE_jbuf’
/usr/include/python2.4/pyfpe.h:132: warning: data definition has no type or stor age class
src/_namemapper.c: In function ‘setNotFoundException’:
src/_namemapper.c:79: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c:79: error: (Each undeclared identifier is reported only once
src/_namemapper.c:79: error: for each function it appears in.)
src/_namemapper.c: In function ‘wrapInternalNotFoundException’:
src/_namemapper.c:95: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c: In function ‘PyNamemapper_valueForKey’:
src/_namemapper.c:165: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c: In function ‘PyNamemapper_valueForName’:
src/_namemapper.c:186: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c: In function ‘namemapper_valueForKey’:
src/_namemapper.c:241: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c: In function ‘namemapper_valueForName’:
src/_namemapper.c:257: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c:268: warning: return from incompatible pointer type
src/_namemapper.c:271: warning: implicit declaration of function ‘malloc’
src/_namemapper.c:271: warning: incompatible implicit declaration of built-in fu nction ‘malloc’
src/_namemapper.c:271: warning: implicit declaration of function ‘strlen’
src/_namemapper.c:271: warning: incompatible implicit declaration of built-in fu nction ‘strlen’
src/_namemapper.c:271: warning: implicit declaration of function ‘free’
src/_namemapper.c:271: warning: return from incompatible pointer type
src/_namemapper.c:276: warning: statement with no effect
src/_namemapper.c: In function ‘namemapper_valueFromSearchList’:
src/_namemapper.c:290: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c:304: warning: return from incompatible pointer type
src/_namemapper.c:307: warning: incompatible implicit declaration of built-in fu nction ‘malloc’
src/_namemapper.c:307: warning: incompatible implicit declaration of built-in fu nction ‘strlen’
src/_namemapper.c:307: warning: return from incompatible pointer type
src/_namemapper.c:310: warning: comparison of distinct pointer types lacks a cas t
src/_namemapper.c:316: warning: statement with no effect
src/_namemapper.c:319: warning: statement with no effect
src/_namemapper.c:324: warning: statement with no effect
src/_namemapper.c:330: warning: comparison of distinct pointer types lacks a cas t
src/_namemapper.c: In function ‘namemapper_valueFromFrameOrSearchList’:
src/_namemapper.c:342: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c:360: warning: return from incompatible pointer type
src/_namemapper.c:363: warning: incompatible implicit declaration of built-in fu nction ‘malloc’
src/_namemapper.c:363: warning: incompatible implicit declaration of built-in fu nction ‘strlen’
src/_namemapper.c:363: warning: return from incompatible pointer type
src/_namemapper.c:366: warning: statement with no effect
src/_namemapper.c:369: warning: comparison of distinct pointer types lacks a cas t
src/_namemapper.c:374: warning: statement with no effect
src/_namemapper.c:377: warning: statement with no effect
src/_namemapper.c:382: warning: statement with no effect
src/_namemapper.c:387: warning: statement with no effect
src/_namemapper.c:390: warning: statement with no effect
src/_namemapper.c:397: warning: comparison of distinct pointer types lacks a cas t
src/_namemapper.c: In function ‘namemapper_valueFromFrame’:
src/_namemapper.c:411: error: ‘NULL’ undeclared (first use in this function)
src/_namemapper.c:425: warning: return from incompatible pointer type
src/_namemapper.c:428: warning: incompatible implicit declaration of built-in fu nction ‘malloc’
src/_namemapper.c:428: warning: incompatible implicit declaration of built-in fu nction ‘strlen’
src/_namemapper.c:428: warning: return from incompatible pointer type
src/_namemapper.c:431: warning: statement with no effect
src/_namemapper.c:434: warning: statement with no effect
src/_namemapper.c:437: warning: statement with no effect
src/_namemapper.c: At top level:
src/_namemapper.c:456: error: ‘NULL’ undeclared here (not in a function)
src/_namemapper.c: In function ‘init_namemapper’:
src/_namemapper.c:469: warning: passing argument 3 of ‘Py_InitModule4’ from inco mpatible pointer type
src/_namemapper.c:469: warning: passing argument 4 of ‘Py_InitModule4’ from inco mpatible pointer type
src/_namemapper.c:473: warning: passing argument 3 of ‘PyErr_NewException’ from incompatible pointer type
src/_namemapper.c:474: warning: passing argument 2 of ‘PyErr_NewException’ from incompatible pointer type
src/_namemapper.c:474: warning: passing argument 3 of ‘PyErr_NewException’ from incompatible pointer type
error: command 'gcc' failed with exit status 1

---

