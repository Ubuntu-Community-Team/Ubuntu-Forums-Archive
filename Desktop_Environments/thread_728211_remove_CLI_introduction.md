---
title: "remove CLI introduction"
date: 2008-03-18
forum: Desktop Environments
---

### Post by Ck.asdf on 2008-03-18
Hello, whenever logging into a console, I get the following welcome message, which I find unnecessary (I'm used to Fedora, and know the console fairly well); is there a way I can get rid of, or change, this welcome?

> ck@192.168.1.4's password: 
Linux server 2.6.22-14-server #1 SMP Sun Oct 14 23:34:23 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue Mar 18 15:28:17 2008 from 192.168.1.2


Thanks for any suggestions!

---

### Post by init1 on 2008-03-18
> **Ck.asdf said:**
> Hello, whenever logging into a console, I get the following welcome message, which I find unnecessary (I'm used to Fedora, and know the console fairly well); is there a way I can get rid of, or change, this welcome?



Thanks for any suggestions!
That message is displayed by /etc/motd. You can change it to anything you want.

---

### Post by Ck.asdf on 2008-03-18
Thanks, that did it!
By the way, is there any way to do system commands within that file?
Such as, passing "clear" to the system, so it clears what's on-screen, and moves to the top of the console?

---

### Post by init1 on 2008-03-18
> **Ck.asdf said:**
> Thanks, that did it!
By the way, is there any way to do system commands within that file?
Such as, passing "clear" to the system, so it clears what's on-screen, and moves to the top of the console?
Your welcome :D
I usually just do that by adding a command to the end of ~/.bashrc

---

### Post by Polk on 2008-04-27
This how-to worked before the 8.04 hardy. Now, every time I delete everything from the motd file, it's working only untill next reboot. Once computer is rebooted the default text is in place again.
Any ideas?

Update: ok, "rm motd" helped, but what if I need some custom text in there.

---

### Post by Polk on 2008-05-02
Anyone knows if it's a bug or a feature now?

---

### Post by adamos on 2008-05-29
edit /etc/motd.tail

---

