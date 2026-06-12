---
title: "network manager won't detect network"
date: 2009-02-12
forum: General Help
---

### Post by firsttimeuser on 2009-02-12
Sorry I can not figure this one out.

I just completely removed kde, and after that the network manager applet refuses to detect any network devices (it shows 'NO network devices available").

I can still manually connect to wireless or wired using command line, but the nework manager applet just won't pick up any wired or wireless connection. I remember it used to give me something like "wireless network available" and I can just click select a wireless AP and I am good to go.

What can I do to fix this problem, anyone can share me some insight here?

---

### Post by bodhi.zazen on 2009-02-12
Ahh network manager ...

Hard to tell , did you try rebooting ?

When network manager is not working I always try wicd next :

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The issues with network manager can be difficult to resolve.

---

### Post by firsttimeuser on 2009-02-12
reboot does not help at all.

Just wondering besides installing another 3rd software, can I do something to fix network manager itself? It used to work before I removed kde

---

### Post by bodhi.zazen on 2009-02-12
> **firsttimeuser said:**
> can I do something to fix network manager itself? It used to work before I removed kde

I don't know. Last time I tried wrestling with network manager I failed after a month while wicd works out of the box.

You could install wicd and if that fails try re-installing network manger. Each is a single package so it is very simple.

Your other option would be to kill network manager and re-start it from the command line, see if you get some clue as to the problem or error message.

At the moment you all we know is that it is not working. Hard to guess at why.

---

### Post by partsdale on 2009-02-12
"The issues with network manager can be difficult to resolve."


... and Moby Dick was just a big fish


:) 

I actually don't have any useful input but I couldn't resist the understatement of the year.

Good Luck

---

### Post by firsttimeuser on 2009-02-13
can anyone tell me what is the package name of the networkmanager?

apparently ubuntu does not think it is "networkmanager"

@noname:~$ sudo apt-get remove NetworkManager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package NetworkManager

@noname:~$ sudo apt-get remove networkmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package networkmanager

---

### Post by firsttimeuser on 2009-02-13
nerver mind, it is network-manager

still no network after reinstall... sight

Time to give wicd a try

---

### Post by partsdale on 2009-02-14
I believe if you were using KDE it would be KNetworkManager.

good luck

---

### Post by Trizzy on 2010-06-11
My network-manager package was somehow broken, I'm not sure how. After reading this article, I decided to install wicd. The package worked flawlessly for me right out of the box, as stated above.

I just like to post when I find an article that helped my problem, so others like myself can find results easier. Thanks for the above posts!

---

