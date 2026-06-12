---
title: "Freeciv crash in Ubuntu 10.10"
date: 2011-02-26
forum: Gaming &amp; Leisure
---

### Post by barlaventoexpert on 2011-02-26
I am having an ongoing problem which continually ruins playing Freeciv on my Ubuntu 10.10 installation.

I will play for several hours and then in the middle of a seesion, bingo, Freeciv crashes. The game will not restart from that point onwards.

Any help, comments or advice would be appreciated.

Details:

Ubuntu 10.10
Gnome 2.32.0
Kernel Linux 2.6.35-25-generic
Intel Celeron M CPU 530 @ 1.73GHZ
Memory: 2.0GB
FreeCiv- server version - Freeciv: 2.2.1-1ubuntu1

Error Message from system.log

Feb 26 08:20:39 xxxusernamexxx kernel: [ 5540.017512] freeciv-server[2221]: segfault at b4 ip 0000000000485b60 sp 00007fff2ae10ae8 error 4 in freeciv-server[400000+185000]

---

### Post by ubudog on 2011-03-21
Try running freeciv from a terminal, and after it crashes paste the terminal output into a code block on the Forums.

```
freeciv
```

The error messages there may be more helpful.

---

### Post by Ozor Mox on 2011-03-21
There were some AI bugs that would cause the Freeciv server to crash every couple of turns that were fixed in 2.2.3. I recommend you uninstall the Freeciv found in the repositories and compile the newest one (currently 2.2.5) from source. For me, the crashes then disappeared.

---

### Post by ubudog on 2011-03-21
Try getting the one from PlayDeb.

[http://www.playdeb.net/software/FreeCiv](http://www.playdeb.net/software/FreeCiv)

---

