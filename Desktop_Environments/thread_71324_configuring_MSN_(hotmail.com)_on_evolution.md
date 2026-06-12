---
title: "configuring MSN (hotmail.com) on evolution"
date: 2005-10-03
forum: Desktop Environments
---

### Post by psylvester on 2005-10-03
hi all.
I want to configure Evolution. In outlook I used to configure my hotmail account.
But I dont know how to configure it in ubuntu-evoluiton.
Hotmail doesnt have pop & imap service. It Only have http:// service. So i dont know
how to configure it on evolution.
Please help to configure (step by step explanations will be much appreciated)
Thanks
PrasanthSylvester.
mail@psylvester.net

---

### Post by aysiu on 2005-10-03
I'm not sure if this still works, but you can try [this](http://ubuntuforums.org/showthread.php?t=36002)

---

### Post by psylvester on 2005-10-03
I installed like its shown On that Page. The Only difference is, In that page he was using
0.0.27.tar.gz , Im using 0.0.31.tar.gz || Everything worked, till make.

I started from here...

sudo apt-get install bison flex libc6-dev libcurl3-dev libexpat1-dev libidn11-dev libssl0.9.7 zlib1g-dev debconf

root@ubuntu:/home/sylvu # cd ~
root@ubuntu:~ # wget [http://mesh.dl.sourceforge.net/sourceforge/freepops/freepops-0.0.31.tar.gz](http://mesh.dl.sourceforge.net/sourceforge/freepops/freepops-0.0.31.tar.gz)

root@ubuntu:~ # sudo tar -xzvf freepops-0.0.31.tar.gz -C /usr/src
root@ubuntu:~ # cd /usr/src/freepops-0.0.31

root@ubuntu:/usr/src/freepops-0.0.31 # ls
AUTHORS       config        COPYING   modules            scripts
BUILD         config.h      doc       README             src
buildfactory  config.lua    INSTALL   README.modules     TODO
ChangeLog     configure.sh  Makefile  README.modules.it


root@ubuntu:/usr/src/freepops-0.0.31 # sudo ./configure.sh linux
root@ubuntu:/usr/src/freepops-0.0.31 # sudo make
> 
Default is all
building lua
building luay
 building dep for luay.c
/bin/sh: gcc: command not found
make[3]: *** [.luay.d] Error 127
building freepopsd
 compiling engine.c -> make[2]: gcc: Command not found
make[2]: *** [engine.o] Error 127
make[1]: *** [src] Error 2
make: *** [help] Error 2

(this is what I get when I make): acn some One help please. If it only works on 0.0.27.tar.gz , Please some one mail me that

thanks,
p.sylvester
cochin.

---

### Post by tehwa on 2005-10-03
It's looking for a C compiler. Get one by running

```
sudo apt-get install build-essentials
```

It should be the same process for 0.0.31 as it is for 0.0.27 so this shouldn't be a problem.

---

### Post by psylvester on 2005-10-03
root@ubuntu:/usr/src/freepops-0.0.31 # sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials

This is what I get most Of the time when I try to install. Please Help.
Prashanth

---

### Post by aysiu on 2005-10-03
It's not *build-essential**s***; it's *build-essential*.

It's better to use Synaptic to install software, if you're not sure of the name. See my sig for more details.

---

### Post by tehwa on 2005-10-03
[QUOTE=aysiu]It's not *build-essential**s***; it's *build-essential*.
It's better to use Synaptic to install software, if you're not sure of the name. See my sig for more details.[/QUOTE]
indeed, i typed that into terminal just to check first. Perhaps I need my eyes checked.

---

### Post by edemark on 2005-10-03
Hi I would suggest you to use Thunderbird with this mail program you can use a webmail extension that lets you get your messages from hotmail from yahoo and from some other web based mails. the set up is stright forward takes some 20 seconds and restarting Thunderbird some 3 times but there is no compiling and it works if you want to try after installing Thunderbird google for web-mail-0.3-4[inter2].xpi and from the same page download an other xpi (hotmail yahoo) then install both of them in Tbird following the instructions of the page then you set

good luck

---

### Post by aysiu on 2005-10-03
There are various fixes--I've tried the webmail extension for Thunderbird. It works great for a while. Every couple of weeks or so, you get a warning about "negative vibes." The problem is that Microsoft doesn't want you checking email without either seeing their web-based advertisements or using Microsoft Outlook.

My advice--get a Gmail account or some other account--not Hotmail or Yahoo! You'll be happier in the end. These workarounds for restrictive email accounts are patchy at best.

---

