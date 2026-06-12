---
title: "&quot;chkconfig&quot; like command in Ubuntu"
date: 2009-02-07
forum: General Help
---

### Post by paragkalra on 2009-02-07
I have "sendmail" server running on my Ubuntu 8.10. The problem is that it takes few minutes for sendmail to start when the system is booting up.

How could I avoid it's start during the booting process?

In Redhat/Fedora there is a command called "chkconfig", using which we can do:
 "chkconfing sendmail off"

I wanted to know same kind of application/command/utility on Ubuntu.

---

### Post by DGortze380 on 2009-02-07
> **paragkalra said:**
> I have "sendmail" server running on my Ubuntu 8.10. The problem is that it takes few minutes for sendmail to start when the system is booting up.

How could I avoid it's start during the booting process?

In Redhat/Fedora there is a command called "chkconfig", using which we can do:
 "chkconfing sendmail off"

I wanted to know same kind of application/command/utility on Ubuntu.

The first place to look will be in /etc/init.d
This directory holds your start-up scripts in Ubuntu.

---

### Post by andrewc6l on 2009-02-07
More particularly, /etc/rc5.d is what gets run when the system boots into runlevel 5 (graphical mode). In that directory are a bunch of symbolic links to the scripts in /etc/init.d, all beginning with S.

If you rename the link that starts sendmail and change the S to a K, then the app will not be started (actually, it will be killed if running when you enter that runlevel, but on boot that shouldn't matter.) See /etc/rc1.d for examples using K instead of S, and more info is in /etc/rc5.d/README

---

### Post by paragkalra on 2009-02-07
Thanks for your replies...but sorry to say...I already know this tweak...I am looking for some simple little command...I am sure it exists...

Weekend has started and I am feeling lazy to do a Googly...:mrgreen:

---

### Post by excbuntu on 2009-04-10
> **andrewc6l said:**
> More particularly, /etc/rc5.d is what gets run when the system boots into runlevel 5 (graphical mode). In that directory are a bunch of symbolic links to the scripts in /etc/init.d, all beginning with S.

If you rename the link that starts sendmail and change the S to a K, then the app will not be started (actually, it will be killed if running when you enter that runlevel, but on boot that shouldn't matter.) See /etc/rc1.d for examples using K instead of S, and more info is in /etc/rc5.d/README

woa, can you please direct me to a site that explains how programs startup in layman's terms? i feel like *complete* newb having no clue what you're talking about. this is important to me because i recently installed apcupsd (ups program) and want to know if it starts at boot.

---

### Post by Gary. on 2009-09-12
Ubuntu's alternative for chkconfig is **sysv-rc-conf**.
It can be installed with **sudo apt-get install sysv-rc-conf**

---

### Post by cariboo on 2009-09-12
You can also use update-rc.d to add and remove scripts from startup:

```
sudo update-rc.d -f sendmail remove
```

Just type update-rc.d at the prompt, and it will show you the options.

---

### Post by jobst on 2009-09-12
> **paragkalra said:**
> I have "sendmail" server running on my Ubuntu 8.10. The problem is that it takes few minutes for sendmail to start when the system is booting up.

How could I avoid it's start during the booting process?

In Redhat/Fedora there is a command called "chkconfig", using which we can do:
 "chkconfing sendmail off"

I wanted to know same kind of application/command/utility on Ubuntu.

Sendmail doesnt take long to start, if it does there is a problem [i run big sendmail servers and when they boot they hardly blink ;-)], so I gather you have a problem.

I highly recommend to go searching sendmail mailing list, this has been discussed before in those forums. 

jobst

---

