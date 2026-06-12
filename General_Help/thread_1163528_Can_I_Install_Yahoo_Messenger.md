---
title: "Can I Install Yahoo Messenger"
date: 2009-05-18
forum: General Help
---

### Post by Titoolsen on 2009-05-18
I have now installed Ubuntu 9.4 - 

1. Can I use yahoo?
2. how to I set up my logitech camera?
3. Can i use a form of key logger to supervise my children's use?

---

### Post by BZF on 2009-05-18
[SIZE=1][COLOR=Blue]I can answer 1, you can download it here, but just so u know its a bit old looking but it works[/COLOR][/SIZE]

[http://in.docs.yahoo.com/messenger/download/unix.html](http://in.docs.yahoo.com/messenger/download/unix.html)

---

### Post by loell on 2009-05-18
one program to rule those three items :D


its [gyachi]("ubuntuforums.org/showthread.php?t=773802") ;)

1. it's the defacto yahoo messenger for linux

2. logitech cameras **usually** works well with linux , and so the program can use it.


3. if this is your computer and your the parent , you can monitor the conversations on gyachi's logs. :)

---

### Post by Jive Turkey on 2009-05-18
I dont use IM much but you can set up pidgin to use the Yahoo protocol.  Then under Tools>Preferences>Logging make sure all boxes are checked.  After that, locate the logs (possibly in ~./pidgin) so you know where to look when it comes time to snoop, I mean supervise.  I believe Yahoo supports voice chat as well with their windows client, I don't know if that works in pidgin or not.

---

### Post by Titoolsen on 2009-05-23
> **loell said:**
> one program to rule those three items :D


its [gyachi]("http://ubuntuforums.org/showthread.php?t=773802") ;)

1. it's the defacto yahoo messenger for linux

2. logitech cameras **usually** works well with linux , and so the program can use it.


3. if this is your computer and your the parent , you can monitor the conversations on gyachi's logs. :)


I tried hard to follow the links and the guides but pages of geek language such as:

                                  **Howto: Gyachi - Yahoo! messenger, Webcam, room voice chat, photo sharing**             
                                                                just my regular support  thread for gyachi :smile:

**About gyachi**: *Yahoo! client for Linux operating system supports almost all of the features you would expect to find on the official Windows Yahoo! client: Voice chat, webcams, faders, 'nicknames', audibles, avatars, display images, and more *

current packages can be found here

[https://launchpad.net/~loell/+archive/ppa]("https://launchpad.net/%7Eloell/+archive/ppa")

Well says it all - why Windows has been such a success - it speaks in laymen's language!

HELP! This is as far as I got before I decided I needed a coffee:

Installing with make...Installing with install...

========================= Installation results ===========================
make: *** No rule to make target `install'. Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by Liolikas on 2009-05-23
sudo apt-get install gyachi

You already have Pidgin and it allows basic chat in yahoo.

---

### Post by loell on 2009-05-23
> **Titoolsen said:**
> I tried hard to follow the links and the guides but pages of geek language such as:


ok, making this easy for you :)


download this

[https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.1.71-1~jaunty1_i386.deb]("https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.1.71-1~jaunty1_i386.deb")


after downloading, the file should be on the desktop, double click to install.

you will find the program in **Applications menu --> Internet --> Gyache Imprroved**


[COLOR="Blue"]note: only use what is easier and what works for you..[/COLOR]

---

### Post by colau on 2009-05-23
Pidgin seems better than yahoo messenger for chatting.
```

sudo aptitude install gyachi

```

---

### Post by ragadanga63 on 2009-09-29
Please stop telling newbies to sudo apt-get install when you haven't verified that that software is in Ubuntu repository (Gyachi is not).  The newbie will only end up more confused than before.

---

### Post by dek2pogs on 2009-12-07
what can we do? in order to install gyachi in our ubuntu?

---

### Post by MarkCrider on 2010-02-07
> **dek2pogs said:**
> what can we do? in order to install gyachi in our ubuntu?To install GyachE Improved in ubuntu jaunty
Open sources.list

This worked for me:

[http://blog.dipinkrishna.info/2009/07/gyache-improved-yahoo-client-for-linux.html](http://blog.dipinkrishna.info/2009/07/gyache-improved-yahoo-client-for-linux.html)

    $ sudo gedit /etc/apt/sources.list

Add these lines to sources.list

    deb [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/loell/ppa/ubuntu](http://ppa.launchpad.net/loell/ppa/ubuntu) jaunty main

Now update apt-get.

    $ sudo apt-get update

Install Gyachi

    $ sudo apt-get install gyachi

---

### Post by soluckytouselinux on 2010-03-24
hi. i can't get yahoo working in either pidgin or empathy. i don't know why. i hope it comes to the repository.

---

