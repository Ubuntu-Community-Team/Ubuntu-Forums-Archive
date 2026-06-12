---
title: "[XPS M1530] hard disk problem under Hardy"
date: 2008-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by var on 2008-11-27
hi all,

I'm using a XPS M1530 under Ubuntu 8.04.
the problem is that, when I'm under battery, the computer seems to be very slow. in particular, when I start an action (open a webpage, a console, a program and so on) it seems that the hard disk must me re-activated (I hear a sort of "reactivation" sound), and this operation take some time (reducing system's reactivity and performances).
what files and configurations can I check to remove this problem?

thanks a lot. :)

---

### Post by biocorp on 2008-11-27
> **var said:**
> hi all,

I'm using a XPS M1530 under Ubuntu 8.04.
the problem is that, when I'm under battery, the computer seems to be very slow. in particular, when I start an action (open a webpage, a console, a program and so on) it seems that the hard disk must me re-activated (I hear a sort of "reactivation" sound), and this operation take some time (reducing system's reactivity and performances).
what files and configurations can I check to remove this problem?

thanks a lot. :)

probably its following issue:
[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

---

### Post by var on 2008-11-27
> **biocorp said:**
> probably its following issue:
[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

hi, thanks for your answer.
however, I get not results when I use sudo hdparm -B 254 /dev/sda or sudo hdparm -B 255 /dev/sda: the problem still remains.

any other suggest?

thanks. :)

---

### Post by biocorp on 2008-11-27
> **var said:**
> hi, thanks for your answer.
however, I get not results when I use sudo hdparm -B 254 /dev/sda or sudo hdparm -B 255 /dev/sda: the problem still remains.

any other suggest?

thanks. :)

What is the result?
Problem still remains or command hdparm unsuccesful?

---

### Post by var on 2008-11-27
> **biocorp said:**
> What is the result?
Problem still remains or command hdparm unsuccesful?

the problem still remains.

---

### Post by var on 2008-11-28
please, any other help? :(

thanks.

---

### Post by var on 2008-12-01
up, thanks.

---

