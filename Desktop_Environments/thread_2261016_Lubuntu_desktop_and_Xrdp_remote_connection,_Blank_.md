---
title: "Lubuntu desktop and Xrdp remote connection, Blank screen with X like cursor"
date: 2015-01-15
forum: Desktop Environments
---

### Post by chairmansaab2 on 2015-01-15
Hello,

I'm new to linux world, so pardon my ignorance. I want to connect to my VPS via remote desktop which is running Ubuntu 14.04 LTS and lubuntu-desktop. I've also installed Xrdp to remote connect with my machine but i'm unsuccessful so far, i get this blank screen! 

This is what i've done to install lubuntu-desktop

```
sudo apt-get install --no-install-recommends lubuntu-desktop

sudo apt-get install xrdp

sudo nano /etc/xrdp/startwm.sh

```

[COLOR="#EE82EE"]#!/bin/sh

if [ -r /etc/default/locale ]; then
. /etc/default/locale
export LANG LANGUAGE
fi

[B]#. /etc/X11/Xsession
. /usr/bin/startlxde[/B][/COLOR]

My VPS has 1GB of ram with 1GB of Vswap if that's matter.

Is there anything i'm missing here ? It should take me to desktop but i'm getting this blank screen, i don't know why!

Ram usage has shot up from usual 10-20MB to 175MB now after installation of Lubuntu-desktop and Xrdp.

[IMG]http://i.imgur.com/TatwNt5.jpg[/IMG]

Please let me know if you guys need any additional information about my setup.

---

### Post by chairmansaab2 on 2015-01-16
I've reinstalled Ubuntu with LXDE desktop this time and Xrdp is working now!

---

