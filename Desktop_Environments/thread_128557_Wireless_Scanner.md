---
title: "Wireless Scanner"
date: 2006-02-11
forum: Desktop Environments
---

### Post by namit on 2006-02-11
I was looking for Netstumber for linux but can not find it.

Does anyone recommend a wireless scanner.

---

### Post by gingermark on 2006-02-11
A VERY quick google search seems to suggest that is a Windows program. Is that right? Do you know that a linux version exists?

I don't use a wireless scanner, but I could imagine that it might well be quite a hassle. Maybe post what sort of features you are looking for in a program, and someone might be able to suggest something.

Many of us here aren't that familiar with Windows apps anymore :)

You might also want to post in the [Hardware Help](http://ubuntuforums.org/forumdisplay.php?f=98) forum if you just need help getting it up and running.

Sorry if I misunderstood your question.

---

### Post by namit on 2006-02-13
i am just looking for a program that will list all avalable networks in the area and there strenghts and if they are avalable encripted or not.

Yes it is a windows version, i do not know of any linux version.

Was wondering could anyone recommend one to me

---

### Post by i_eat_red_meat on 2006-02-13
There are 3 that I have tried: 
[LIST]
[*]WifiRadar:  didn't really work
[*]GTKwifi:    [http://www.ubuntuforums.org/showthread.php?t=113715]("http://www.ubuntuforums.org/showthread.php?t=113715")  Not too bad
[*]Network Manager:   What I am currently using, along with GTKwifi. Network Manager will *attempt* to make sure you are always connected. If you disconnect from your wired network, NM will try to connect to a wireless network. It also lets me connect to my WEP AP.
[/LIST]

---

### Post by FlakJacket on 2006-02-13
KWifiManager should already be installed with Kubuntu and will allow you to scan for networks and can give you some info on the network and has a nifty chart with signal strength and optionally noise.  Very Handy.

Flak

---

### Post by i_eat_red_meat on 2006-02-13
Oops, I just noticed that this was in the Kubuntu thread. My options were for GNOME....My bad

---

### Post by FlakJacket on 2006-02-13
I was kinda wondering myself if I was in the right forum from your post haha.

Flak

---

### Post by canibal on 2006-02-17
You may want to try [SWScanner]("http://www.swscanner.org/en/index.htm")
:mrgreen:

---

### Post by namit on 2006-02-19
But i have searched in Synaptic but can not find these packages have been messing with it for last few hours such a pain in the ***

But it looks like perfect program

 swscanner depends on kdelibs4c2a (>= 4:3.4.3-1); however:
  Package kdelibs4c2a is not installed.
 swscanner depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 swscanner depends on libidn11 (>= 0.5.18); however:
  Version of libidn11 on system is 0.5.13-1.0.
 swscanner depends on libqt3-mt (>= 3:3.3.5); however:
  Version of libqt3-mt on system is 3:3.3.4-8ubuntu5.
 swscanner depends on libshp1; however:
  Package libshp1 is not installed.
 swscanner depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
 swscanner depends on libxrender1 (>> 1:0.9.0-1); however:
  Version of libxrender1 on system is 1:0.9.0-1.
 swscanner depends on libqt3-mt-sqlite (>= 3.3.5); however:
  Package libqt3-mt-sqlite is not installed.
dpkg: error processing swscanner (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

---

### Post by FlakJacket on 2006-02-19
I get the same errors when i try to install any wifi utility.  Can anyone tell us why?

Flak

---

### Post by A*p on 2007-04-23
I Cannot help with your dependency woes, but you may want to take a look at [Kismet]("http://www.kismetwireless.net/").

---

