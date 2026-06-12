---
title: "Pyqt? Where do I find it?"
date: 2009-06-01
forum: General Help
---

### Post by Bigtime_Scrub on 2009-06-01
I wanted to get thin liquid film so I could convert files into mp4 for my ipod and I ran sudo /install.py and I got an error message saying I needed to get pyqt. Where do I find it?

```
gary@gary-laptop:~$ cd src
gary@gary-laptop:~/src$ ls
tlf-1.00.tar.bz2
gary@gary-laptop:~/src$ tar -jxvf tlf-1.00.tar.bz2
thinliquidfilm/
thinliquidfilm/main.py
thinliquidfilm/install.py
thinliquidfilm/getFileInfo.py
thinliquidfilm/uploadFileInfo.py
thinliquidfilm/README.txt
thinliquidfilm/thinliquidfilm.desktop
thinliquidfilm/timeConvert.py
thinliquidfilm/thinliquidfilm.py
thinliquidfilm/StuffIt Expander.png
thinliquidfilm/ipod_mount.png
thinliquidfilm/add.png
thinliquidfilm/remove.png
thinliquidfilm/quit.png
thinliquidfilm/preview.png
thinliquidfilm/manual.png
thinliquidfilm/selectall.png
thinliquidfilm/invert.png
gary@gary-laptop:~/src$ ls
thinliquidfilm  tlf-1.00.tar.bz2
gary@gary-laptop:~/src$ cd thinliquidfilm
gary@gary-laptop:~/src/thinliquidfilm$ ./configure
bash: ./configure: No such file or directory
gary@gary-laptop:~/src/thinliquidfilm$ make
make: *** No targets specified and no makefile found.  Stop.
gary@gary-laptop:~/src/thinliquidfilm$ sudo make install
make: *** No rule to make target `install'.  Stop.
gary@gary-laptop:~/src/thinliquidfilm$ sudo ./install.py
*************************************
      installing thinliquidfilm
*************************************


-------------------------
Checking dependencies ...
-------------------------

Couldn't find pyqt.  thin liquid film will not work without pyqt.  Aborting installation.
gary@gary-laptop:~/src/thinliquidfilm$ 

```

---

### Post by Bigtime_Scrub on 2009-06-01
Jeez this is a dependency nightmare. I suggest people stay away from this program. I figured out I did in fact pyqt-4. Which is the up to date version, problem is, thinliquidfilm wants python-pyqt-3. I installed that and it started to complain about the bash system. 

So I ran (please people do not run this command, I should have listened to the caveats given):

```

    * sudo rm -f /bin/sh
    * sudo ln -s /bin/bash /bin/sh

```


It gave me a bash error and my terminal was all messed up.

I fixed it doing this:

```
 

cd /bin
sudo su
rm sh
ln -s bash sh


```

when I tried to install thinliquidfilm again I got a gazzillion dependency errors all having to go with the fact I do not have kde. I will install kde right now and if that doesn't work I give up because this program is too much work to get running in Ubuntu.

---

