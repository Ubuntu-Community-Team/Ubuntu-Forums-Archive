---
title: "Real Player 10, again"
date: 2005-12-25
forum: Desktop Environments
---

### Post by rfruth on 2005-12-25
Trying to get RealPlayer 10 working but having trouble, help me !  I keep getting command not found when I run RealPlayer10GOLD.bin even though its executable (or is it, if I had the answer wouldn't be posting)
> rfruth@ubuntu:~$ chmod a+x RealPlayer10GOLD.bin
rfruth@ubuntu:~$ ls -l
drwxr-xr-x  4 rfruth rfruth    4096 2005-12-23 17:41 audio
-rw-r--r--  1 rfruth rfruth      72 2005-12-18 21:36 Dad info 12-05
-rw-r--r--  1 rfruth rfruth      38 2005-12-18 21:35 Dad info 12-05~
drwxr-xr-x  3 rfruth rfruth    4096 2005-12-25 20:12 Desktop
drwxr-xr-x  2 rfruth rfruth    4096 2005-12-22 17:31 download
drwxr-xr-x  2 rfruth rfruth    4096 2005-12-22 20:10 file
drwxr-xr-x  3 rfruth rfruth    4096 2005-12-25 18:43 image
drwxr-xr-x  2 rfruth rfruth    4096 2005-12-25 16:37 My Music
-rw-r--r--  1 rfruth rfruth  230399 2005-12-15 20:24 ohiocold.jpg
-rwxr-xr-x  1 rfruth rfruth 5789348 2005-12-25 20:17 RealPlayer10GOLD.bin
-rw-r--r--  1 rfruth rfruth     226 2005-12-23 20:18 Unsaved Document 1
-rw-r--r--  1 rfruth rfruth     281 2005-12-23 20:16 Unsaved Document 1~
-rw-r--r--  1 rfruth rfruth     413 2005-12-21 19:19 Unsaved Document 2
-rw-r--r--  1 rfruth rfruth      66 2005-12-21 19:10 Unsaved Document 2~
rfruth@ubuntu:~$ RealPlayer10GOLD.bin
bash: RealPlayer10GOLD.bin: command not found
rfruth@ubuntu:~$ RealPlayer10GOLD

help me :confused:

---

### Post by CapnKennit on 2005-12-25
Try

./RealPlayer10GOLD.bin

You use the ./ in front of the program when you are in the same directory as it is.  If the program is in a another directory than you and that directory is in the PATH than you can run it without the ./ :p

---

### Post by briancurtin on 2005-12-25
[QUOTE=rfruth]I keep getting command not found when I run RealPlayer10GOLD.bin[/QUOTE]
thats because RealPlayer10GOLD.bin isnt a command

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
rfruth, to execute a program yu need to make it executable. You can do this by right clicking on it in nautilus and selecting properties, then enabling the "execute" option. You can also do it from the command line by executing "chmod +x *filename*"

I doubt you'll have much luck with this, however, as realplayer 10 doesn't get along well with breezy. Your best bet would be to install mplayer and then download the "all" codecs package (not the "essential" as many here suggest).

---

### Post by rfruth on 2005-12-25
I *was* using chmod as needed (see above) then I got all the way to a new error message(s)(( RealPlayer10 install complaining it can't find some libraries even though I get a "file exists") ((see below)) 
```
 rfruth@ubuntu:~$  ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
ln: `/usr/lib/libstdc++.so.5': File exists
rfruth@ubuntu:~$ ln -s /usr/local/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1
ln: `/usr/lib/libgcc_s.so.1': File exists
rfruth@ubuntu:~$ ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
ln: `/usr/lib/libstdc++.so.5': File exists
rfruth@ubuntu:~$ ln -s /usr/local/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1
ln: `/usr/lib/libgcc_s.so.1': File exists
rfruth@ubuntu:~$
rfruth@ubuntu:~$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
anyway I went with the mplayer solution and while it's not perfect things are better :p

---

### Post by dcstar on 2005-12-26
[QUOTE=rfruth]
......
rfruth@ubuntu:~$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/CODE]
anyway I went with the mplayer solution and while it's not perfect things are better :p[/QUOTE]
It would probably be better to install this as root:

sudo ./RealPlayer10GOLD.bin

Myself, I'd add this to the repositories and just install realplayer via Synaptic:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

---

