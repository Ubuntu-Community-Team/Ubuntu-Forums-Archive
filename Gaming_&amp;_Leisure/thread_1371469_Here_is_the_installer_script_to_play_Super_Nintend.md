---
title: "Here is the installer script to play Super Nintendo over the NET for Ubuntu !!"
date: 2010-01-03
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2010-01-03
Run this script ;) for Ubuntu and Debian

```

#!/bin/sh
cd /tmp
mkdir zsnesnet
cd zsnesnet
wget -N "http://linksadventure.no-ip.biz/programs/zsnesnet.tar.bz2"

sudo apt-get install nasm  libsdl1.2-dev

tar xvf zsnesnet.tar.bz2
./configure
make 
make install
cd /tmp
cp -a zsnesnet /usr/bin
ln -s /usr/bin/zsnesnet/zsnes  /usr/bin/zsnesnet
```


then :
server side:
Server needs no keypad
$ zsnesnet
configure the input #1
$ zsnesnet
netplay > connect server

client side:
Client needs a keypad
$ zsnesnet
configure the input #2
quit
$ zsnesnet
wait that the server choose a game !!

Play, enjoy !!



It is a bit tricky, but I hope that the programmers of ZNES will read this post & realize how complicateed it is to play under Ubuntu Linux

---

