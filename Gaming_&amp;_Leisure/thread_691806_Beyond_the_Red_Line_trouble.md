---
title: "Beyond the Red Line trouble"
date: 2008-02-09
forum: Gaming &amp; Leisure
---

### Post by Djalmahal on 2008-02-09
So,while installing this game i get the following message

andreas@andreas-laptop:~$ sudo sh BtRLDemoInstaller.run
[sudo] password for andreas:
Verifying archive integrity... All good.
Uncompressing Beyond the Red Line Demo.................................................................................................................
/home/andreas/.setup3894: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory




andreas@andreas-laptop:~$ sudo sh BtRLDemoInstaller.run
Verifying archive integrity... All good.
Uncompressing Beyond the Red Line Demo.................................................................................................................
dirname: missing operand
Try `dirname --help' for more information.
cp: cannot stat `/data/players/single/Nugget.pl2': No such file or directory
Couldn't run Beyond the Red Line Demo (btrl_demo.bin). Is FSO_DATA_PATH set?
andreas@andreas-laptop:~


The second time I ran the sh command I had the libgtk1.2 (the name was closest to the missing shared library)installed , still the an error message.

Does anybody know how to get on with it, the game looks really promising

Andreas

---

### Post by Cappy on 2008-02-09
Did you get prompted on where to install it?

If so check the directory and see if it is installed. If it is you can probably run it from that directory.

---

### Post by LinuxGamer on 2008-02-09
I had no problem installing it.  I installed it in my home directory instead of as root though.  Runs no problem.  I would make sure you have the [newest release]("http://www.game-warden.com/bsg/downloads.html") and then try again into your home directory. I am guessing you are running into a problem from installing as root and running as user.

---

