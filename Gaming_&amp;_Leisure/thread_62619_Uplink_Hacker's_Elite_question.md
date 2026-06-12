---
title: "Uplink: Hacker's Elite question"
date: 2005-09-05
forum: Gaming &amp; Leisure
---

### Post by Watcher on 2005-09-05
Anybody had any chance getting this game to work in Ubuntu? I followed the instructions about copying the stuff, but when opening uplink in my terminal I just got this error:

> bernard@bernardtux:~/uplink$ ./uplink
./uplink: relocation error: ./uplink: undefined symbol: __glutRoot 

This is not fun, cause I really really really like this game. Anyway if anyone had any luck making this work, please share your solution. Thanks in advance!!

---

### Post by slux on 2005-09-06
I've got Uplink but haven't played it in a while (should as it's a great game).  The error message looks like you're missing the glut libs or maybe have a wrong version. Try installing those if you don't have already.

---

### Post by Watcher on 2005-09-06
[QUOTE=slux]I've got Uplink but haven't played it in a while (should as it's a great game).  The error message looks like you're missing the glut libs or maybe have a wrong version. Try installing those if you don't have already.[/QUOTE]
 Well I checked and I've got the glut libs installed, but wrong version, I don't really know what is the right version than ...

---

### Post by gord on 2005-09-06
just install the newest libglut from synaptic. mine is version 3.7-25 and uplink works ok. allthough there are some problems with fullscreen resolutions for me

oh and make sure you have the latest patch :)

---

### Post by Watcher on 2005-09-06
[QUOTE=gord]just install the newest libglut from synaptic. mine is version 3.7-25 and uplink works ok. allthough there are some problems with fullscreen resolutions for me

oh and make sure you have the latest patch :)[/QUOTE]
I got the 3.8 and it doesn't work  ](*,)

---

### Post by born_confused on 2005-09-06
Well, I got this file from somewhere else. Basically unzip it to /usr/lib

then write the following code to a file and place the file in the directory with the uplink executable

```
#!/bin/sh
here=/PATH/TO/UPLINK/DIRECTORY
export LD_LIBRARY_PATH=$here:$LD_LIBRARY_PATH
export LD_PRELOAD=/usr/lib/libglut.so.3.7
exec $here/uplink $*

```

save the file as say exec_uplink

then chmod +x exec_uplink
./exec_uplink

---

### Post by Watcher on 2005-09-07
[QUOTE=born_confused]Well, I got this file from somewhere else. Basically unzip it to /usr/lib

then write the following code to a file and place the file in the directory with the uplink executable

```
#!/bin/sh
here=/PATH/TO/UPLINK/DIRECTORY
export LD_LIBRARY_PATH=$here:$LD_LIBRARY_PATH
export LD_PRELOAD=/usr/lib/libglut.so.3.7
exec $here/uplink $*

```

save the file as say exec_uplink

then chmod +x exec_uplink
./exec_uplink[/QUOTE]
 That got me to run the non-patched version, but when I install the patch i get this error now:

> bernard@bernardtux:~/.uplink$ ./exec_uplink
/home/bernard/.uplink/uplink: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


---

### Post by born_confused on 2005-09-07
apt for libstdc++

---

### Post by Watcher on 2005-09-07
Checked that before I posted, and have it, so I don't know why it doesn't want to work ...

---

### Post by born_confused on 2005-09-07
Hmm, well, I just searched libstdc++ in synaptic, and the only installed result is
libstdc++5-3.3-dev

---

### Post by Watcher on 2005-09-08
[QUOTE=born_confused]Hmm, well, I just searched libstdc++ in synaptic, and the only installed result is
libstdc++5-3.3-dev[/QUOTE]
yes, same thing as I found (and it clearly said it was installed)

---

### Post by Jonahhubunutu on 2006-11-24
Ubuntu LTS 6.06 user:
I have been trying to find out how to run the same game on my system for a week, couldn't even get the original working with what posts' points you have discussed. Love it too, but i get that same error msg the whole time, have the libs and the bash command says the same thing originally posted the whole time. <<<HEAD WRECKING>>>

---

### Post by Perfect Storm on 2006-11-24
But did you install libglut and then followed what was mention earlier in this thread?

---

### Post by Jonahhubunutu on 2006-11-26
Yeah i tried them all and still got, the patch wasn't a big help either,

./uplink: symbol lookup error: ./uplink: undefined symbol: __glutRoot

I even got the shell app from your links and still haven't gotten it working, on a thumbs up note i downloaded the uplink demo for linux and that works fine.  the package from the games for linux page for the full game (shell app) won't register my cdrom and install.

---

