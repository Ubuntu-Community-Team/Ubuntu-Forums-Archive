---
title: "Need help installing this Falling Sand Game Simulator!"
date: 2010-07-01
forum: Gaming &amp; Leisure
---

### Post by sodra on 2010-07-01
Hi again
Theres this sand game simulator called wxSand
I need help installing the .BIN file or the tar.gz file, none of them worked
can someone tell me how to? or point me in the right direction?

heres the website to download it
[http://www.piettes.com/fallingsandgame/download.html](http://www.piettes.com/fallingsandgame/download.html)

---

### Post by shazbut on 2010-07-02
I got it to work. It's a bit of a challenge if you haven't done this sort of thing before.
First make the downloaded file (fsg-4.4) executable (right click, properties, permissions, allow executing)
Need to install some extra things (which I found out by running ./fsg-4.4 from the the terminal)
```
sudo apt-get install libpng3 libexpat1
```
Also need libstdc++5, which can is no longer available from 9.10 onwards, but which can be had by following the instructions here:
[http://www.hackourlives.com/ubuntu-10-04-lucid-lynx-libstdc-so-5/]("http://www.hackourlives.com/ubuntu-10-04-lucid-lynx-libstdc-so-5/")

Basically, my method is to run it from the command line to see which library it complains about being missing, then add that library and run it again.  Repeat until it stops complaining and actually works.

---

### Post by sodra on 2010-07-02
```
edwin@wesley:~$ ./fsg-4.4
bash: ./fsg-4.4: No such file or directory
edwin@wesley:~$ cd Desktop
edwin@wesley:~/Desktop$ cd fsg
edwin@wesley:~/Desktop/fsg$ ./fsg-4.4
./fsg-4.4: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
edwin@wesley:~/Desktop/fsg$ ^C
edwin@wesley:~/Desktop/fsg$ 

```
I keep getting this...

---

### Post by Perfect Storm on 2010-07-03
> **sodra said:**
> ```
edwin@wesley:~$ ./fsg-4.4
bash: ./fsg-4.4: No such file or directory
edwin@wesley:~$ cd Desktop
edwin@wesley:~/Desktop$ cd fsg
edwin@wesley:~/Desktop/fsg$ ./fsg-4.4
./fsg-4.4: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
edwin@wesley:~/Desktop/fsg$ ^C
edwin@wesley:~/Desktop/fsg$ 

```
I keep getting this...

Symblink /lib/libexpat.so.1 to /lib/libexpat.so.0

---

