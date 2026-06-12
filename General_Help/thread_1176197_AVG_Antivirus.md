---
title: "AVG Antivirus"
date: 2009-06-02
forum: General Help
---

### Post by smartdude4ever on 2009-06-02
Hi everyone! Its nice to join the ubuntu community!
So I was getting things set up
For the antivirus, I installed AVG through the deb package. But I cannot find it in the applications menu?
Is there some shortcut to it or is it already running?
Thanks!

---

### Post by colau on 2009-06-02
> **smartdude4ever said:**
> Hi everyone! Its nice to join the ubuntu community!
So I was getting things set up
For the antivirus, I installed AVG through the deb package. But I cannot find it in the applications menu?
Is there some shortcut to it or is it already running?
Thanks!
Does this help?
[http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty)

---

### Post by Soul-Sing on 2009-06-02
Hi,
: [http://ubuntuforums.org/showthread.php?t=1175641](http://ubuntuforums.org/showthread.php?t=1175641)

conclusion: the 8.5 version comes without a -gui.

---

### Post by smartdude4ever on 2009-06-02
Whoa!
I got the response in less than a minute!
Thanks!!!!!!

---

### Post by smartdude4ever on 2009-06-02
So is it already running (the protection)?

---

### Post by Soul-Sing on 2009-06-02
> **smartdude4ever said:**
> So is it already running (the protection)?

take a look at: system monitor processes
and a look at the manpage, howto scan/update/etc.
there must be a manpage in ./avg home

(It seems to be an on access scanner...)

---

### Post by lovinglinux on 2009-06-02
> **smartdude4ever said:**
> So is it already running (the protection)?

As far as I know, all of those Desktop anti-virus with Linux versions doesn't have real-time protection. They are actually designed to scan on demand and they are not capable of scanning Linux virus. Besides, there isn't any Linux virus in the wild, so unless you want to protect other Windows machines on your network, AVG would completely useless.

I also believe that AVG doesn't have any graphical interface, so you have to launch it through terminal. Additionally, as far as I know, it is not capable of healing, putting in quarantine or deleting the infected files, so it is pretty much useless.

If you really need an anti-virus, I would recommend [BitDefender](https://help.ubuntu.com/community/BitDefender). But first you should read about [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421), because unlike Windows you don't need to run a bunch of security crap to be protected.


*UKeywords: 649167 2009 june avg bitdefender anti-virus*

---

