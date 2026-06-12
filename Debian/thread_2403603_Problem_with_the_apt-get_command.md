---
title: "Problem with the apt-get command"
date: 2018-10-13
forum: Debian
---

### Post by ubunter90 on 2018-10-13
Hi to all, i'm new in this forum, and i hope to have posted in a correct section.

To achieve my thesis on my University i use Netkit, the network simulator, but i have this problem.

When i try to install or update programs using: apt-get install or apt-get update, i have this message "Failed to fetch http://ftp.it.debian.org".
I need to install wireshark in netkit and the telnet daemon or something similar.
I try to see my /etc/apt/sources.list file and this is its content:

---

### Post by wildmanne39 on 2018-10-13
*Thread moved to **Debian for a more appropriate fit**.*

---

### Post by arochester on 2018-10-13
Your sources.list output does not appear here.

What does your sources.list and sources.list.d  show?

---

### Post by ubunter90 on 2018-10-16
> **arochester said:**
> Your sources.list output does not appear here.

What does your sources.list and sources.list.d  show?

Sorry but i don't know why the output of the two files doesn't it is shown.

I rewrite in this post:

```

* sources.list file:
# Pick the mirror that is nearest to you among the following ones:
#
#deb [http://ftp.at.debian.org/debian/](http://ftp.at.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.wa.au.debian.org/debian/](http://ftp.wa.au.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.au.debian.org/debian/](http://ftp.au.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.bg.debian.org/debian/](http://ftp.bg.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.br.debian.org/debian/](http://ftp.br.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.ch.debian.org/debian/](http://ftp.ch.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.cl.debian.org/debian/](http://ftp.cl.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.cz.debian.org/debian/](http://ftp.cz.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp2.de.debian.org/debian/](http://ftp2.de.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.dk.debian.org/debian/](http://ftp.dk.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.ee.debian.org/debian/](http://ftp.ee.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.es.debian.org/debian/](http://ftp.es.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.fi.debian.org/debian/](http://ftp.fi.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.fr.debian.org/debian/](http://ftp.fr.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp2.fr.debian.org/debian/](http://ftp2.fr.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.hk.debian.org/debian/](http://ftp.hk.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.hr.debian.org/debian/](http://ftp.hr.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.hu.debian.org/debian/](http://ftp.hu.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.ie.debian.org/debian/](http://ftp.ie.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.is.debian.org/debian/](http://ftp.is.debian.org/debian/)      unstable main contrib non-free
 deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.jp.debian.org/debian/](http://ftp.jp.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp2.jp.debian.org/debian/](http://ftp2.jp.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.kr.debian.org/debian/](http://ftp.kr.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.mx.debian.org/debian/](http://ftp.mx.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.nl.debian.org/debian/](http://ftp.nl.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.no.debian.org/debian/](http://ftp.no.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.nz.debian.org/debian/](http://ftp.nz.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.pl.debian.org/debian/](http://ftp.pl.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.pt.debian.org/debian/](http://ftp.pt.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.ro.debian.org/debian/](http://ftp.ro.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.ru.debian.org/debian/](http://ftp.ru.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.se.debian.org/debian/](http://ftp.se.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.si.debian.org/debian/](http://ftp.si.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.sk.debian.org/debian/](http://ftp.sk.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.tr.debian.org/debian/](http://ftp.tr.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.tw.debian.org/debian/](http://ftp.tw.debian.org/debian/)      unstable main contrib non-free
#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/)      unstable main contrib non-free
```

* sources.list.d:
i've used this command: cd /etc/apt/sources.list.d
and ls -l, the message is: total 0.

---

### Post by QIII on 2018-10-16
Hello!

Please use the default font and color.

Enclose all terminal commands and results in code tags:

1.  Click the # button above the text entry box, place your cursor between the code tags that appear and paste or type your text.  Alternatively, paste or type your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by arochester on 2018-10-16
Never seen a sources.list like that. I assume when Italy is the only mirror not made ineffective that you are in Italy.

I would first try replacing that sources.list with only```
deb http://ftp.it.debian.org/debian/ unstable main contrib non-free
 
```

Sources.list.d is a directory. Try the command  ```
cat /etc/apt/sources.list.d/*

```

(Another place to ask is [http://forums.debian.net](http://forums.debian.net) )

---

### Post by ubunter90 on 2018-10-17
> **arochester said:**
> Never seen a sources.list like that. I assume when Italy is the only mirror not made ineffective that you are in Italy.

I would first try replacing that sources.list with only```
deb http://ftp.it.debian.org/debian/ unstable main contrib non-free
 
```

Sources.list.d is a directory. Try the command  ```
cat /etc/apt/sources.list.d/*

```

(Another place to ask is [http://forums.debian.net](http://forums.debian.net) )

Thanks, i've tried ```
 cat /etc/apt/sources.list.d/*
```, and the result is:
```

No such file or directory

```
[LEFT]
[FONT=Verdana]All the output posted here it[COLOR=#222222] is the output of the my Netkit network simulator VM, based on a Linux kernel.[/COLOR][/FONT][/LEFT]

---

