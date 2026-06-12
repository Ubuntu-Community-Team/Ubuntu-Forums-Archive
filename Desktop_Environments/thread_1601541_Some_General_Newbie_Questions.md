---
title: "Some General Newbie Questions"
date: 2010-10-20
forum: Desktop Environments
---

### Post by onaridge on 2010-10-20
Just started with Linux a few days ago, came from Windows. 

Can you leave a Linux computer for weeks unlike a Windows PC? 

How do you back up settings and customization in case of a restart?

For the address bars in browsers, how can you simply type an address without having to delete what's already there. In Windows browsers you just click on the address bar, the whole line is highlighted and you type. 

I love the cube and it works great but even though I have several effects associated with it selected, none of them work other then the cube itself.

I need to find a good tutorial on on installing programs and knowing where to put them if they are things like screenlets and not programs coming from repositories. For example I downloaded the Facebook screenlet and followed the directions but was still unsure of how to get it going and fumbled through it and did get it going. I was an advanced user in Windows and would like to be one in Ubuntu some day. I found the Pocket Guide very useful but it didn't answer a lot of questions for me. Searching the fora here helped somewhat but left the above questions unanswered.

---

### Post by lmontrieux on 2010-10-20
> **onaridge said:**
> Can you leave a Linux computer for weeks unlike a Windows PC?

Yes, you can.

> **onaridge said:**
> How do you back up settings and customization in case of a restart?

Settings and customization of what, exactly?

> **onaridge said:**
>  For the address bars in browsers, how can you simply type an address without having to delete what's already there. In Windows browsers you just click on the address bar, the whole line is highlighted and you type.

There's several ways to achieve that, I guess. CTRL+L will select the address bar and highlight whatever is in it. If you just clic on it, you can CTRL+A to highlight the current address. Alternatively, double-click on the address bar should highlight the address.

> **onaridge said:**
> I need to find a good tutorial on on installing programs and knowing where to put them if they are things like screenlets and not programs coming from repositories. For example I downloaded the Facebook screenlet and followed the directions but was still unsure of how to get it going and fumbled through it and did get it going. I was an advanced user in Windows and would like to be one in Ubuntu some day. I found the Pocket Guide very useful but it didn't answer a lot of questions for me. Searching the fora here helped somewhat but left the above questions unanswered.

Software you want to install and that doesn't come from repositories can be classified in, say, three categories:

* you get a .deb package. Just double-clic it or run dpkg -i your_file from a terminal
* you get an archive with a compiled program. Just open the archive and follow the readme. Usually, software installed from other sources is put in /usr/local, but it's just a "good practice". You can put it wheverver you want, basically
* you get source code. You need to compile it. Refer to the software documentation (there usually is an INSTALL and/or a README file), as it can vary a lot. The most common way is ./configure && make && sudo make install.

---

### Post by Pengwyn44 on 2010-10-21
I highly recommend buying a good book for beginners. "Beginning Ubuntu Linux" by Keir Thomas and Jaime Sicam. Published by Apress. ([www.apress.com](www.apress.com))
It continues up to Intermediate level. Don't grudge the £30 + , think of the hundreds you will save by not using Windows!

It has helped me enormously, as also has this forum.

Pengwyn44

---

### Post by sidzen on 2010-10-21
Welcome!
See [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by TBABill on 2010-10-21
Leaving it on all the time is absolutely ok. You won't get forced updates or other issues and come back to find your machine borked from something not working right during the process. It updates when you tell it to so it should remain in the same state as when you left it (besides power settings or screensavers that may kick in).
 
Address bars...one of my least favorite things. I tend to triple click to highlight the whole thing since I use a laptop and touchpad. It all highlights then I start typing. I don't like multi steps just to be able to enter an address or search string.
 
Although it is ok to download and install from the Internet to gain functionality or apps not in the repos, the problems this can lead to can be large during updates or upgrades to a newer version. The upgrade process counts on your machine being fully up to date, but it does not account for external software being installed. So the upgrade may fail on those machines, rendering it useless until a fresh install is done. 
 
Configs should remain during any reboot unless you are implying you are running from the LiveCD. I can't tell by the question is you mean an installed system or a LiveCD system. Installed system configurations will remain through restarts, just like they do in Windows. The only time they should not is if the configuration was only a 1-time thing (like killing an app) or something borked.

---

### Post by jerrrys on 2010-10-21
you may find this useful

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=tutorials&as_qdr=all&sa=Google+Search&lang=en#1046](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=tutorials&as_qdr=all&sa=Google+Search&lang=en#1046)

---

