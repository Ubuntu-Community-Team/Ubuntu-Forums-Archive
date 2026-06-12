---
title: "Discussion - https://help.ubuntu.com/community/GizmodIn11.10and12.04"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by nothingspecial on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/GizmodIn11.10and12.04](https://help.ubuntu.com/community/GizmodIn11.10and12.04)

Support threads should be posted in normal forums.

Thank you.

---

### Post by Penguissimo on 2012-09-08
After following these instructions, I get this error during the compile:


```
/home/will/Downloads/gizmod-3.5/libGizmod/Processes.cpp: In static member function &#8216;static void Gizmod::Processes::updateProcessTree()&#8217;:
/home/will/Downloads/gizmod-3.5/libGizmod/Processes.cpp:157:27: error: expected unqualified-id before &#8216;;&#8217; token
make[2]: *** [libGizmod/CMakeFiles/Gizmod.dir/Processes.o] Error 1
make[1]: *** [libGizmod/CMakeFiles/Gizmod.dir/all] Error 2
make: *** [all] Error 2
```

I did some Googling of the error, but unfortunately the last programming I've ever done was in Applesoft BASIC, so I'm at a bit of a loss to solve this. I know that this line in this file is one of the lines the instructions have us change, and I went back to make sure I copy-pasted everything perfectly, but I still get this error. Any ideas? I'm running 12.04 (with the 3.5 kernel branch, if that makes a difference).

edit: I get the same error even when I revert the line back to the original line (so that it's identical to a freshly-downloaded copy).

---

### Post by Borfo on 2012-12-26
I got gizmod working in 12.10 - had the same "expected unqualified-id before ‘;’ token" error.  I fixed that by changing all the lines suggested on the wiki page, but wherever it said to change the line to 'iter->;path().string() + "\"', I deleted the semicolon, so it read 'iter->path().string() + "\"'

I had to make the changes suggested in the "Excessive CPU Usage" section too, since otherwise it consumed 100% of one CPU all the time.

Also, follow the instructions here:
[http://sourceforge.net/apps/mediawiki/gizmod/index.php?title=HOWTO_-_Setting_Input_Device_Permissions_-_Creating_a_udev_Rule](http://sourceforge.net/apps/mediawiki/gizmod/index.php?title=HOWTO_-_Setting_Input_Device_Permissions_-_Creating_a_udev_Rule)

...don't forget the colon in the MODE setting - eg: 'MODE:="660"'

---

### Post by krodelabestiole on 2013-06-22
[COLOR=#000000][FONT=Arial]hello

i think i followed exactly this documentation :
[https://help.ubuntu.com/community/GizmodIn11.10and12.04](https://help.ubuntu.com/community/GizmodIn11.10and12.04)

but when i run make i get this error :
[/FONT][/COLOR]
```
[ 88%] Building CXX object gizmod/CMakeFiles/gizmod.dir/GizmoDaemon.o
/home/krodelabestiole/Téléchargements/gizmod-3.5/gizmod/GizmoDaemon.cpp: In member function ‘void GizmoDaemon::initPython()’:
/home/krodelabestiole/Téléchargements/gizmod-3.5/gizmod/GizmoDaemon.cpp:1332:51: erreur: ‘initGizmoDaemon’ was not declared in this scope
make[2]: *** [gizmod/CMakeFiles/gizmod.dir/GizmoDaemon.o] Erreur 1
make[1]: *** [gizmod/CMakeFiles/gizmod.dir/all] Erreur 2
make: *** [all] Erreur 2
```
[COLOR=#000000][FONT=Arial]i found absolutely no information about this error anywhere
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]line 1332 looks like this :[/FONT][/COLOR]

```
void GizmoDaemon::initPython() {
    try {
        cdbg1 << "Embedding Python Interpreter..." << endl;
        PyImport_AppendInittab((char *) "GizmoDaemon", &initGizmoDaemon);
```
[COLOR=#000000][FONT=Arial]what do you think ? have i forget to install any dependency or should i edit the source code ?[/FONT][/COLOR]

---

### Post by krodelabestiole on 2013-06-22
ok i found the issue

cmake was using python3.2 instead of python2.7

---

