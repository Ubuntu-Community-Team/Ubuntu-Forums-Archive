---
title: "howto make a .deb from source?"
date: 2006-02-15
forum: Desktop Environments
---

### Post by syklitengutt on 2006-02-15
Ive been adviced to not install from source.
Now I want to install the newest [http://www.sacredchao.net/quodlibet/wiki/Download]("http://http://www.sacredchao.net/quodlibet/wiki/Download")
and its in source. Anyone interessed in explainong to me how to create a deb of this, or to create one for me?

---

### Post by curtis on 2006-02-15
Checkinstall should help you.
Install it via apt-get.
Then instead of using make install, use checkinstall.

---

### Post by frodon on 2006-02-15
Same advice, checkinstall will create a .deb in the directory where you run the command and it will also create all the needed debian files so that you will be able to see the software in synaptic and therefore uninstall easily if you wish.

---

### Post by syklitengutt on 2006-02-15
how can I install from source with apt get?
The files in the folder is this:
> chris@chris:~/Desktop/quodlibet-0.17.1$ ls
browsers            library.py         quodlibet.desktop.in
check.py            Makefile           quodlibet.png
config.py           massagers.py       quodlibet.py
const.py            mmkeys             quodlibet.svg
COPYING             mutagen            README
exfalso.1           NEWS               rhythmbox-volume-max.png
exfalso.desktop     parse              rhythmbox-volume-medium.png
exfalso.desktop.in  player.py          rhythmbox-volume-min.png
exfalso.png         plugins            rhythmbox-volume-zero.png
exfalso.py          po                 stock.py
exfalso.svg         qltk               trayicon
formats             quodlibet.1        util.py
HACKING             quodlibet.desktop  widgets.py


---

### Post by syklitengutt on 2006-02-15
tnx....
I learned something today....

---

### Post by frodon on 2006-02-15
If you want to learn more read that : [http://doc.gwos.org/index.php/ProgramInstallBeginners](http://doc.gwos.org/index.php/ProgramInstallBeginners)

---

### Post by syklitengutt on 2006-02-15
but a little issue with quodlibet.
I cant get it to play.
Get this error with alsasink:
Unable to play song
GStreamer was unable to load the selected song.
GStreamer status 'NONE_PENDING' != 'NULL

And wit ossink it just flies trough the songs without any music played.

---

### Post by andrewsawyer on 2006-02-15
Quick question relating to this thread...

I have tried to make a deb file from source, however when I try to install it I get the following error:
```
andrew@Elisha:~/Temp/Xserver-6.6.1$ sudo dpkg -i xserver_6.6.1-1_x86_64.deb
dpkg: error processing xserver_6.6.1-1_x86_64.deb (--install):
 package architecture (x86_64) does not match system (amd64)
Errors were encountered while processing:
 xserver_6.6.1-1_x86_64.deb
andrew@Elisha:~/Temp/Xserver-6.6.1$
```

Could anyone shed any light on this?  Any help would be much appreciated.

---

### Post by art on 2006-02-15
when running checkinstall, it is asking you some questions. Somewhere near the end it will say 
**This package will be built according to these values:**
and 9 options below it. Change option 7 to amd64, and install should go fine after that.

---

