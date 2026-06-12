---
title: "How to install Dolphin Wii Emulator?"
date: 2011-01-05
forum: Gaming &amp; Leisure
---

### Post by mark2741 on 2011-01-05
Stumbled upon this today:

[http://www.dolphin-emulator.com/](http://www.dolphin-emulator.com/)

Looks awesome! But there are only Windows builds on the Download page, even though it's open source and they say it runs on Linux.

Has anyone gotten it to install?

I did find a website offering downloads pre-built for Ubuntu here:
[http://alphaboxmedia.net/dolphin-emu/](http://alphaboxmedia.net/dolphin-emu/)

Even though those builds are old now I tried anyway and when I download, decompress, open a terminal and try to run it I get this:

mark@mark-ubuntu:~/Desktop/Linux-x86_64$ ./dolphin-emu
./dolphin-emu: error while loading shared libraries: libao.so.2: cannot open shared object file: No such file or directory
mark@mark-ubuntu:~/Desktop/Linux-x86_64$ apt-get install libao.so.2
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mark@mark-ubuntu:~/Desktop/Linux-x86_64$ sudo apt-get install libao.so.2
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libao.so.2
E: Couldn't find any package by regex 'libao.so.2'
mark@mark-ubuntu:~/Desktop/Linux-x86_64$ 

Looking in the /usr/lib directory it appears that libao.so.4 is there but not version 2. So I think my best bet is to try to find the latest linux build versus trying to get the old version running.

---

### Post by Bonster on 2011-01-06
you can download it from the Getdeb or Playdeb repo

[http://www.getdeb.net/](http://www.getdeb.net/)
[http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by DirtyPC on 2011-01-06
Have you tried using it under Wine? I find programs (such as spotify) run just as good and are simpler to install through wine. Could give it a try

---

### Post by thatguruguy on 2011-01-06
> **mark2741 said:**
> Stumbled upon this today:

[http://www.dolphin-emulator.com/](http://www.dolphin-emulator.com/)

Looks awesome! But there are only Windows builds on the Download page, even though it's open source and they say it runs on Linux.

Has anyone gotten it to install?

I did find a website offering downloads pre-built for Ubuntu here:
[http://alphaboxmedia.net/dolphin-emu/](http://alphaboxmedia.net/dolphin-emu/)

Even though those builds are old now I tried anyway and when I download, decompress, open a terminal and try to run it I get this:

mark@mark-ubuntu:~/Desktop/Linux-x86_64$ ./dolphin-emu
./dolphin-emu: error while loading shared libraries: libao.so.2: cannot open shared object file: No such file or directory
mark@mark-ubuntu:~/Desktop/Linux-x86_64$ apt-get install libao.so.2
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mark@mark-ubuntu:~/Desktop/Linux-x86_64$ sudo apt-get install libao.so.2
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libao.so.2
E: Couldn't find any package by regex 'libao.so.2'
mark@mark-ubuntu:~/Desktop/Linux-x86_64$ 

Looking in the /usr/lib directory it appears that libao.so.4 is there but not version 2. So I think my best bet is to try to find the latest linux build versus trying to get the old version running.

There's a ppa for dolphin which updates fairly regularly. It's available [here]("https://launchpad.net/%7Eglennric/+archive/dolphin-emu").

Once you've installed the ppa, you can install dolphin-emu directly from synaptic, and it will receive updates when available.

---

