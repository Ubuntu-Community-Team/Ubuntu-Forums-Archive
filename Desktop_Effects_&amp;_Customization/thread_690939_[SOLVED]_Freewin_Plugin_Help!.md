---
title: "[SOLVED] Freewin Plugin Help!"
date: 2008-02-08
forum: Desktop Effects &amp; Customization
---

### Post by Spoken on 2008-02-08
Ok, im trying to get this "freewin" plugin to work for me. Im using compiz fusion, ubuntu 7.10. I keep getting a error when i type in the "make" command. What did i do wrong!!!?!?!

Here is the Guide i Used

Freely Transform Windows was (Freewins) (Its renamed in ccsm)
Instead of a wget use [THIS POST #8 & #10]("http://ubuntuforums.org/showthread.php?t=604231") download the .tar.gz to your desktop
(save to disk when box pop up) right click the freewins.tar.gz click Extract Here .
Open your home folder (your user name) open compiz file & put freewin file off the desktop in
compiz file (drag & drop or copy & paste). Post #10 open the freewins folder in the compiz folder . Then open the freewins.c folder a gedit box opens scroll down past the blue text
the 1st line with pink text, change the line #include <compiz-core.h> to
#include <compiz.h> just remove -core click save in the toolbar close
the gedit box , close your file browser then code in the terminal.

Code:

cd ~/compiz/freewins

Code:

make

Code:

sudo make install

Here are the Errors that i got!

compiling : freewins.c -> build/freewins.lofreewins.c:41:25: error: compiz-core.h: No such file or directory
In file included from freewins.c:49:
build/freewins_options.h:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:42: error: expected ')' before '*' token
build/freewins_options.h:44: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:64: error: expected ')' before '*' token
build/freewins_options.h:66: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:68: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:69: error: expected ')' before '*' token
build/freewins_options.h:70: error: expected ')' before '*' token
build/freewins_options.h:71: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:72: error: expected ')' before '*' token
build/freewins_options.h:74: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:75: error: expected ')' before '*' token
build/freewins_options.h:76: error: expected ')' before '*' token
build/freewins_options.h:77: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:78: error: expected ')' before '*' token
build/freewins_options.h:80: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:81: error: expected ')' before '*' token
build/freewins_options.h:82: error: expected ')' before '*' token
build/freewins_options.h:83: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:84: error: expected ')' before '*' token
build/freewins_options.h:86: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:87: error: expected ')' before '*' token
build/freewins_options.h:88: error: expected ')' before '*' token
build/freewins_options.h:89: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:90: error: expected ')' before '*' token
build/freewins_options.h:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:93: error: expected ')' before '*' token
build/freewins_options.h:94: error: expected ')' before '*' token
build/freewins_options.h:95: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:96: error: expected ')' before '*' token
build/freewins_options.h:98: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:99: error: expected ')' before '*' token
build/freewins_options.h:100: error: expected ')' before '*' token
build/freewins_options.h:101: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:102: error: expected ')' before '*' token
build/freewins_options.h:104: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:105: error: expected ')' before '*' token
build/freewins_options.h:106: error: expected ')' before '*' token
build/freewins_options.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:108: error: expected ')' before '*' token
build/freewins_options.h:110: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:111: error: expected ')' before '*' token
build/freewins_options.h:112: error: expected ')' before '*' token
build/freewins_options.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:114: error: expected ')' before '*' token
build/freewins_options.h:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:117: error: expected ')' before '*' token
build/freewins_options.h:118: error: expected ')' before '*' token
build/freewins_options.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:120: error: expected ')' before '*' token
build/freewins_options.h:122: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:123: error: expected ')' before '*' token
build/freewins_options.h:124: error: expected ')' before '*' token
build/freewins_options.h:125: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:126: error: expected ')' before '*' token
build/freewins_options.h:128: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:129: error: expected ')' before '*' token
build/freewins_options.h:130: error: expected ')' before '*' token
build/freewins_options.h:131: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:132: error: expected ')' before '*' token
build/freewins_options.h:134: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:135: error: expected ')' before '*' token
build/freewins_options.h:136: error: expected ')' before '*' token
build/freewins_options.h:137: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:138: error: expected ')' before '*' token
build/freewins_options.h:140: error: expected ')' before '*' token
build/freewins_options.h:141: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:142: error: expected ')' before '*' token
build/freewins_options.h:144: error: expected ')' before '*' token
build/freewins_options.h:145: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:146: error: expected ')' before '*' token
build/freewins_options.h:148: error: expected ')' before '*' token
build/freewins_options.h:149: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:150: error: expected ')' before '*' token
build/freewins_options.h:152: error: expected ')' before '*' token
build/freewins_options.h:153: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:154: error: expected ')' before '*' token
build/freewins_options.h:156: error: expected ')' before '*' token
build/freewins_options.h:157: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:158: error: expected ')' before '*' token
build/freewins_options.h:160: error: expected ')' before '*' token
build/freewins_options.h:161: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:162: error: expected ')' before '*' token
build/freewins_options.h:164: error: expected ')' before '*' token
build/freewins_options.h:165: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:166: error: expected ')' before '*' token
build/freewins_options.h:168: error: expected ')' before '*' token
build/freewins_options.h:169: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:170: error: expected ')' before '*' token
build/freewins_options.h:172: error: expected ')' before '*' token
build/freewins_options.h:173: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:174: error: expected ')' before '*' token
build/freewins_options.h:176: error: expected ')' before '*' token
build/freewins_options.h:177: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:178: error: expected ')' before '*' token
build/freewins_options.h:180: error: expected ')' before '*' token
build/freewins_options.h:181: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:182: error: expected ')' before '*' token
build/freewins_options.h:184: error: expected ')' before '*' token
build/freewins_options.h:185: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:186: error: expected ')' before '*' token
build/freewins_options.h:188: error: expected ')' before '*' token
build/freewins_options.h:189: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/freewins_options.h:190: error: expected ')' before '*' token
freewins.c:108: error: expected specifier-qualifier-list before 'HandleEventProc'
freewins.c:120: error: expected specifier-qualifier-list before 'PaintOutputProc'
freewins.c:203: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsMetadata'
freewins.c:206: error: expected ')' before '*' token
freewins.c:242: error: expected ')' before '*' token
freewins.c:536: error: expected ')' before '*' token
freewins.c:657: error: expected ')' before '*' token
freewins.c:733: error: expected ')' before '*' token
freewins.c:753: error: expected ')' before '*' token
freewins.c:771: error: expected ')' before '*' token
freewins.c:838: error: expected ')' before '*' token
freewins.c:911: error: expected ')' before '*' token
freewins.c:945: error: expected ')' before '*' token
freewins.c:979: error: expected ')' before '*' token
freewins.c:1013: error: expected ')' before '*' token
freewins.c:1047: error: expected ')' before '*' token
freewins.c:1081: error: expected ')' before '*' token
freewins.c:1115: error: expected ')' before '*' token
freewins.c:1154: error: expected ')' before '*' token
freewins.c:1195: error: expected ')' before '*' token
freewins.c:1247: error: expected ')' before '*' token
freewins.c:1258: error: expected ')' before '*' token
freewins.c:1309: error: expected ')' before '*' token
freewins.c:1330: error: expected ')' before '*' token
freewins.c:1358: error: expected ')' before '*' token
freewins.c:1375: error: expected ')' before '*' token
freewins.c:1420: error: expected ')' before '*' token
freewins.c:1432: error: expected ')' before '*' token
freewins.c:1444: error: expected ')' before '*' token
freewins.c:1451: error: expected ')' before '*' token
freewins.c:1458: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsVTable'
freewins.c:1476: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/freewins.lo] Error 1

---

