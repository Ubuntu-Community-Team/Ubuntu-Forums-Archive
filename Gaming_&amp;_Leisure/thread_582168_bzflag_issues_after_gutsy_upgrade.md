---
title: "bzflag issues after gutsy upgrade"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by Tennesee Jed on 2007-10-19
After upgrading from 7.04 to 7.10 today, whenever I attempt to play bzflag, the application loads normally and I can connect to servers, but, after connecting, I get pauses of 1-2 seconds every 10-15 seconds. The entire app seems to pause, not just gameplay.

Has anyone else experienced a similar issue after upgrading? This upgrade was pretty extensive, and there are a number of possible culprits...

---

### Post by sci-fi guy on 2007-10-30
Consider yourself lucky. Internet gameplay is so horrible for me that I have given up on it entirely. I am celebrate if I get a new frame every *5 seconds*. It worked fine in *Windows*. And when trying to play a local game, BZFlag simply quits out of the blue after a short while (<1 minute). I am hoping that this is simply a problem w/64-bit that will be resolved shortly.

I have tried everything: reinstalling, compiling from source (dependency not met for some package not in the repos during compile stage), forcing the 32-bit .deb's architecture (did not even start), and even installing the Windows .exe in WINE (also did not start).

---

### Post by Crafty Kisses on 2007-10-30
> **sci-fi guy said:**
> Consider yourself lucky. Internet gameplay is so horrible for me that I have given up on it entirely. I am celebrate if I get a new frame every *5 seconds*. It worked fine in *Windows*. And when trying to play a local game, BZFlag simply quits out of the blue after a short while (<1 minute). I am hoping that this is simply a problem w/64-bit that will be resolved shortly.

I have tried everything: reinstalling, compiling from source (dependency not met for some package not in the repos during compile stage), forcing the 32-bit .deb's architecture (did not even start), and even installing the Windows .exe in WINE (also did not start).

That sucks, I've heard of issues about his.

---

### Post by JustJ on 2007-11-28
I have a similar problem. I try to start bzflag and it crashes the gui!

I was able to start it however...read on.

One possible hint to a problem.. and if anyone else can reproduce this please comment: starting bzflag immediately after logging in ( and while the system is still sluggish at startup ) sometimes allows it to start up!  I had set the bzflag config file so that bzflag was windowed.. not sure if this is important or not.

 I've tried this again myself today and couldn't get it to do it again. I had done it a few times yesterday successfully. Hmm.. I had clicked to start a terminal immediately after the bzflag on successful attempts - maybe that's the difference today. Id' try it now but don't want to risk a reset at the moment ;)

Something loaded after the gui is started up.. hmmm???

Update: Tried it again on boot, I started bzflag just after the "chime" that plays on startup but before the notification of the laptop "power changed to performance". I had also immediately started the terminal.

Here's the later part of the process listing:
 5800 ?        Ss     0:00 /bin/sh /usr/bin/startkde
 5847 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/startkde
 5882 ?        S      0:00 start_kdeinit --new-startup +kcminit_startup
 5883 ?        Ss     0:00 kdeinit Running...
 5886 ?        S      0:00 dcopserver [kdeinit] --nosid
 5889 ?        S      0:00 klauncher [kdeinit] --new-startup
 5891 ?        S      0:00 kded [kdeinit] --new-startup
 5896 ?        S      0:00 kwrapper ksmserver
 5898 ?        S      0:00 ksmserver [kdeinit]
 5899 ?        S      0:00 kwin [kdeinit]
 5901 ?        S      0:02 kdesktop [kdeinit]
 5903 ?        S      0:02 kicker [kdeinit]
 5904 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-justj/klauncher
 5905 ?        S      0:00 kio_media [kdeinit] media /tmp/ksocket-justj/klaunch
 5906 ?        SN     0:00 kio_thumbnail [kdeinit] thumbnail /tmp/ksocket-justj
 5908 ?        S      0:00 kio_uiserver [kdeinit]
 5909 ?        S      0:00 kio_system [kdeinit] system /tmp/ksocket-justj/klaun
 5910 ?        S      0:00 kio_trash [kdeinit] trash /tmp/ksocket-justj/klaunch
 5924 ?        S      0:01 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c
 5926 ?        S      0:00 kaccess [kdeinit]
 5930 ?        S      0:01 /usr/bin/python /usr/share/python-support/kde-guidanc
 5934 ?        S      0:00 knotify [kdeinit]
 5936 ?        S      0:00 konqueror [kdeinit] --preload
 5939 ?        S      0:00 /usr/bin/python /usr/bin/kblueplugd
 5941 ?        S      0:00 klipper [kdeinit]
 5943 ?        S      0:00 knetworkmanager [kdeinit]
 5944 ?        S      0:00 konqueror [kdeinit] --preload
 5946 ?        S      0:02 adept_notifier
 5956 ?        S      0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-globa
 5962 ?        SLl    0:02 bzflag
 5963 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth1.le
 6247 ?        S      0:01 kate [kdeinit] --use /home/justj/Desktop/usbmouse-1.
 6249 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-justj/klauncher
 6252 ?        R      0:00 konsole [kdeinit]
 6253 pts/1    Ss     0:00 /bin/bash
 6269 pts/1    R+     0:00 ps ax


any ideas?  I'll continue investigating little by little.. but _not_ playing bzflag is probably a good thing these days...

---

### Post by sci-fi guy on 2007-11-28
Getting into BZFlag isn't a problem for me. I can even launch a local game and enter that. But it crashes if I other people are connected to the same server.

---

