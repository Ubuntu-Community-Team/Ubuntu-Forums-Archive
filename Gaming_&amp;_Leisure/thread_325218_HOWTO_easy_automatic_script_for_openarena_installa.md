---
title: "HOWTO: easy automatic script for openarena installation"
date: 2006-12-25
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-12-25
screenshots: [http://mods.moddb.com/5727/openarena/image-gallery/](http://mods.moddb.com/5727/openarena/image-gallery/)
[http://openarena.ws/](http://openarena.ws/)

code 
```
gedit installrun.sh           #  copy the following code 
sh installrun.sh &
```

```

#!/bin/sh
sudo apt-get -f -y install libopenal0  file-roller  xdialog  xterm 
sudo apt-get -f -y install libopenal-dev
mkdir /tmp/openarena
cd /tmp/openarena
wget http://openarena.ws/rel/060/oa060.tar.gz
tar  xvpfz oa060.tar.gz 
echo " Let s try the game !"
## for the case of i386
./ioquake3.i386 
xmessage " Hi, copy where you want the file and run for instance from the xterm console ./ioquake3.i386 " &
xmessage " Dont forget to copy it from the /tmp/openarena  temporal folder  " &
xmessage " Enjoy Gaming !" &

```


--
Don't forget the Ubuntu Team :)

---

