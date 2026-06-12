---
title: "Can sbdy share his ~/.xmess/xmessrc ?"
date: 2008-06-01
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-06-01
Thank you !

---

### Post by frenchn00b on 2008-06-01
Here is my script to install sdlmess !!
Finally 
to be retrieved [here]("http://yellowprotoss.ye.funpic.org/games/sdlmame/sdlmame0122-installer-ubuntu.sh") 
you can run it from the console directly.

```
#!/bin/bash
mkdir -p /usr/share/games/
cd /usr/share/games/
wget -N http://ftp.plusline.de/FreeBSD/distfiles/sdlmess0122.zip
unzip sdlmess0122.zip
rm sdlmess0122.zip
mv sdlmess0122 sdlmess
cd /usr/share/games/sdlmess
make -f makefile.sd
beep
chmod ug+rx /usr/share/games/sdlmess -R
mkdir -p /usr/share/games/sdlmess/roms
echo "please put all the zip files into /usr/share/games/sdlmess/roms, like this"
rox & rox &
echo "I am waiting you do so with rox and please press enter"
read lfkdjdlfs
rm /usr/bin/sdlmess 
ln -s /usr/share/games/sdlmess/mess   /usr/bin/sdlmess 
chmod ug+rx /usr/share/games/sdlmess -R
chmod ug+rx /usr/bin/sdlmess
echo "to run a floppy game : mess cpc464 -flop1 renegade.dsk"
echo "to run a console game : mess n64 -cart mario64.n64"
echo "Enjoy !!"

```

---

