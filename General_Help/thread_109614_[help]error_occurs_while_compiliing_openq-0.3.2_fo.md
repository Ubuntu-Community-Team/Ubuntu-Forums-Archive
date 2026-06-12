---
title: "[help]error occurs while compiliing openq-0.3.2 for Gaim"
date: 2005-12-29
forum: General Help
---

### Post by survival on 2005-12-29
firstly ,i get the source bag of openq-0.3.2.tar.gz.then i take steps like this:
=============
tar zxvf openq-0.3.2.tar.gz
cd openq-0.3.2
./configure
=============
at this time ,there are some info shown on my screen. at last there is an error,which is so clear given by the system .but i cann't understand for sorry.so please do me a favor,someone help me out please.


=========
checking build system type... i686-pc-linux-gnu
.........../////////there are many other checking.... but all of them are right.so i just show you the question given by the system 


checking for pkg-config... /usr/bin/pkg-config
checking for gaim... Package gaim was not found in the pkg-config search path. Perhaps you should add the directory containing `gaim.pc' to the PKG_CONFIG_PATH environment variable No package 'gaim' found
configure: error: Library requirements (gaim) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

///////and there is another info below ,maybe useful for you.

survival@ubuntu:~$ env PKG_CONFIG_PATH
env: PKG_CONFIG_PATH: No such file or directory

---

### Post by SongQi on 2006-10-20
I'm having the same issue, but it's been almost a year now, and I don't see any answer, so I guess I shouldn't expect one any time soon. poop.

---

