---
title: "Install realTime kernal  12.04"
date: 2012-05-30
forum: Desktop Environments
---

### Post by forsubhi on 2012-05-30
I want to install RealTime kernal to my kubuntu 12.04 so I will be able to use java rts package and realtime facilities , what is the easy method to do that ?

---

### Post by forsubhi on 2012-05-30
I found this on google 

```
**Real Time kernell**

 If the  performance of the -lowlatency kernell provided in Ubuntu repositories  is not enough for you, you may try this repository. It is mostly needed  for audio production too, but scientific or industrial use may need them  too. 
sudo add-apt-repository ppa:abogani/realtimeTake care using those kernells : they might not support restricted drivers (Example: nNidia or AMD/ATI, some wifi chipsets). 
```

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

but I don't know how to add them

---

### Post by forsubhi on 2012-05-31
how can I change my thread location in forum cos I but it in wrong location?

---

### Post by forsubhi on 2012-06-01
I don't know how to use this command 

sudo add-apt-repository ppa:abogani/realtime

I mean after executing it , what should I do ?

---

### Post by forsubhi on 2012-06-02
I get this error when I execute 

sudo apt-get install linux-realtime

```
subhi@subhi-pc:~$ sudo apt-get install linux-realtime
[sudo] password for subhi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdelibs5-dev : Depends: libkimproxy4 (= 4:4.8.3-0ubuntu0.1) but 4:4.8.2-0ubuntu1 is to be installed
 libkimproxy4 : Depends: libkdecore5 (= 4:4.8.2-0ubuntu1) but 4:4.8.3-0ubuntu0.1 is to be installed
                Depends: libkdeui5 (= 4:4.8.2-0ubuntu1) but 4:4.8.3-0ubuntu0.1 is to be installed
                Depends: libkio5 (= 4:4.8.2-0ubuntu1) but 4:4.8.3-0ubuntu0.1 is to be installed
 linux-realtime : Depends: linux-image-realtime (= 3.2.0.23.25~ppa1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```what is the problem?

---

### Post by forsubhi on 2012-06-02
My thread is solved by using this page instructions 

[http://www.ubuntubuzz.com/2012/03/real-time-linux-installation-on-ubuntu.html](http://www.ubuntubuzz.com/2012/03/real-time-linux-installation-on-ubuntu.html)

and by using Synaptic package Manager

---

### Post by Guotao Lin on 2013-01-31
Hi,forsubhi
I executed the following commands on ubuntu 11.04:

$ sudo gedit /etc/apt/sources.list

deb [http://ppa.launchpad.net/abogani/realtime/ubuntu](http://ppa.launchpad.net/abogani/realtime/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/abogani/realtime/ubuntu](http://ppa.launchpad.net/abogani/realtime/ubuntu) precise main

$ sudo apt-get update
$ sudo apt-get install linux-realtime

but it says:
Unable to locate the package linux-realtime

what's wrong with it? how shoud I do?

---

