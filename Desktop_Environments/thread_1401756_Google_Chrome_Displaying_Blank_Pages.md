---
title: "Google Chrome Displaying Blank Pages"
date: 2010-02-08
forum: Desktop Environments
---

### Post by xslick on 2010-02-08
I have Google Chrome version 4.0.249.43 installed on Ubuntu Karmic. I am able to launch Google Chrome but i am unable to view any web pages. I do not get a "Web Page Cannot be displayed" warning, I simply get a blank page. If I try to look at my history, extensions or previous downloads I also get a blank page. I have tried un-installing and reinstalling. I read how this can sometimes can be caused by a profile corruption in Google chrome followed by directions on how to create a new profile in Windows. Anyone know how to create a new Goggle Chrome profile in Ubuntu? Anyone else experienced this problem?

---

### Post by giarca on 2010-02-08
Do not experienced that problem but you can reset your profile deleting .config/google-chrome/ directory.

---

### Post by programad on 2010-03-26
Same problem here.

I have already deleted the folder and the problem still persists.

---

### Post by e-San on 2010-06-07
Same here, but, since i changed kernel configuration.
I can provide configs.

edit. i made some reserch and found this: 
```
san@eeepc:~$ google-chrome
[3098:3098:1353126978:ERROR:chrome/app/chrome_dll_main.cc(234)] Gdk: shmget failed: error 38 (Function not implemented)
```
tried to serch something like shmget+kernel, and found this:
[http://www.linux.com/learn/docs/man/4075-shmget2](http://www.linux.com/learn/docs/man/4075-shmget2)

```
**#include <[sys/ipc.h]("file:///usr/include/sys/ipc.h")>**  
 **#include <[sys/shm.h]("file:///usr/include/sys/shm.h")>
```**

and from headers tried to find in kernel shm or ipc and found 'IPC V' option - it looks reasonable so i enabled it.
compiling at the moment but fount this one too [ [http://www.linuxforums.org/forum/linux-kernel/133860-vesa-0-shmget-lowmem-error-function-not-implemented.html](http://www.linuxforums.org/forum/linux-kernel/133860-vesa-0-shmget-lowmem-error-function-not-implemented.html) ].

---

