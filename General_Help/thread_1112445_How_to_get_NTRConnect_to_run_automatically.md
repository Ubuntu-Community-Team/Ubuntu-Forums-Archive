---
title: "How to get NTRConnect to run automatically"
date: 2009-03-31
forum: General Help
---

### Post by cleanden on 2009-03-31
Just for the next person who would otherwise spend a day bashing their head against a wall...

I found that NTRConnect wasn't working after a reboot until I ran:
```
/etc/init.d/NTRConnectScript start
```

My fix was the following line in /etc/rc.local:
sleep 10 && sudo /etc/init.d/NTRConnectScript start

---

### Post by xoroz on 2009-04-21
NTRConnect is a great solution.
I wrote a howto about it here:
[http://felipeferreira.net/?p=369]("http://felipeferreira.net/?p=369")

cheers,
Felipe Ferreira
[www.felipeferreiar.net](www.felipeferreiar.net)

---

### Post by YesSir on 2009-05-11
xoroz, you saved my life! ;) I tried several options (see: [http://ubuntuforums.org/showthread.php?t=272986](http://ubuntuforums.org/showthread.php?t=272986)), but somehow I never figured this out. Including NTRconnect. 

With the help of your blog, I could! I don´t know how, but it works :D

Thanks a million!

---

### Post by craig100 on 2010-02-13
Just tried ntrconnect on my set up (controlling an Ubuntu 9.10x64 workstation from an Ubuntu 9.10x64 laptop). No joy. I feel it is a misrepresentation on the ntrconnect web site to say it runs on Linux without making it clear that you can't control a machine FROM a Linux machine, you can only control a Linux machine FROM an M$ Windows (or possibly Apple Mac) machine.

The search for a remote control solution that isn't a PITA to set up for Linux/Linux control continues. NTRConnect, isn't it (in my view)!

---

